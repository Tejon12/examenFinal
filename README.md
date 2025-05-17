# examenFinal
## ultimo trabajo de Telematica

#### Paso a paso para montar un contenedor docker apoyado con AWS.

1. Se crea una instancia dentro de EC2 en Ubuntu y configurando los grupos de seguridad para asi activar los puertos 22 (ssh) y puerto 80 (http).
2. Con la instancia creada, vamos a acceser a ella mediante una terminal local. el codigo es el siguiente: ssh -i "tu clave.pem" ubuntu@IP publica de la instancia.
3. Ya dentro de la instancia procedemos con la instalacion del Docker.

#### Intalacion del Docker en caso de que no lo tengas instalado

1. Recomendado --> a la hora de instalar algo hacer primero un "sudo apt update", se usa para actualizar la lista de paquetes disponibles.
2. Codigo para instalar docker --> sudo apt install -y docker.io
3. Despuede de intalar lo encendemos con --> sudo systemctl enable docker && sudo systemctl start docker
4. Para confirmar que si este bien todo usamos --> sudo systemctl status docker

#### Creacion de una carpeta del proyecto

1. Creacion--> mkdir nombre-de-tu-carpeta
2. Entramos en la carpeta --> cd nombre-de-tu-carpeta

#### Creacion del HTML y JavaScript del juego

1. Creamos un archivo --> nano index.html. Para asi en mi caso se almacene el famoso juego "Snake"

#### Creamos el Dockerfile

1. Este docker usara NGINX, este sirve para crear una imagen de contenedor que despliega una página web HTML estática, usando el servidor web NGINX para mostrarla en un navegador.
Codigo --> FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html

#### Contruir la imagen Docker 

1. Codigo --> sudo docker build -t snake-html .

#### Ejecutar el contenedor y exponerlo en el puerto 80

1. sudo docker run -d -p 80:80 --restart unless-stopped --name snake-game snake-game
-El --restart unless-stopped, quiere decir que: El contenedor se reiniciará automáticamente si la máquina se reinicia o si el contenedor falla.

#### Resultado final 

1. En el navegador colocando --> http://<tu-ip-publica> Asi podras ver los que almacena tu contenedor, en mi caso podre jugar al Snake.





 
 

