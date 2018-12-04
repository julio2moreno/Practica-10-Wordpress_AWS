# Practica-10-Wordpress_AWS
###### Amazon Elastic Compute Cloud (Amazon EC2) es un servicio web que proporciona capacidad informática en la nube segura y de tamaño modificable. Está diseñado para simplificar el uso de la informática en la nube a escala web para los desarrolladores.
###### Bitnami es una empresa que ofrece instaladores que nos permiten realizar la instalación y configuración de aplicaciones web de una forma muy sencilla.
## Iniciar una instancia EC2
Lo primero que hay que hacer es abrir la consola de administración de AWS. Cuando la pantalla se cargue, escriba su nombre de usuario y contraseña para comenzar. A continuación seleccionamos Amazon EC2.
Le damos en  ``Launch Instance`` para crear y configurar una máquina virtual.

## Configuracion de la instancia
Ahora en la opcion del panel de la izquierda tenemos que seleccionar ``Community AMIs`` y en la barra del buscador ponemos ``ubuntu`` que es la instancia que vamos a crear.
vamos a coger la version 18.04 que es ``ubuntu/images/hvm-ssd/ubuntu-bionic-18.04-amd64-server-20180912`` damos en ``select``.

Damos ``continue`` hasta la opcion 6 donde configuraremos las reglas de seguridad y en ``add rule`` seleccionamos ``http`` y ``https`` para que nos deje acceder desde cualquier sitio y Launch.

 La siguiente pantalla muestra pares de claves. Los pares de claves se utilizan para conectarse a las instancias de EC2 mediante un programa de shell seguro (SSH).
 Seleccionamos la segunda opcion ``create a new key pair`` y ponemos un nombre a ese archivo y nos descargamos un archivo en extension .pem y damos seleccionamos ``Launch instances``
 
 ## Conectarse a la instancia mediante Windows
 Una vez iniciada la instancia, deberá conectarse a ella mediante SSH.
 Lo primero que tenemos que tener instalado PuTTy para poder acceder via SSh: 
 
 Para descargar puTTY for Windows: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
 
Tenemos que cambiar el par de claves a .ppk que es la extension de claves privadas que utiliza PuTTy.
Por eso abrimos puTTYgen en la ventana seleccionamos ``load`` seleccionamos el archivo que anteriormente se nos ha descargado con la extension .pem, seleccionamos ``view all files`` y renombramos el archivo, a continuacion ``save private key``.

En el panel de la instancias nos vamos a ``connect`` y copiamos el public DNS. En el programa puTTY ponemos lo que hemos copiado. Ejemplo:``ubuntu@ec2-52-90-146-135.compute-1.amazonaws.com``, en la barra lateral nos vamos a la opcion de ``ssh > Auth`` y ponemos la nueva clave que hemos creado.

 ## Conectarse a la instancia mediante Mac/Linux 
 Abrimos un terminal, damos permisos al archivo donde se encuentra el par de claves y con chmod cambiamos los permisos.
 
 ``chmod 400 archivoejemplo.pem ``
 
 Nos vamos al menu de instancias y en ``connect`` copiamos el public DNS y lo pegamos en el terminal.
 
 ``ssh -i "archivoejemplo.pem" ubuntu@ec2-52-90-146-135.compute-1.amazonaws.com``

 ## Instalación y configuración de Wordpress
 Ahora vamos a instalar y configurar un sitio Wordpress con los instaladores de Bitnami ya que automatizan la configuración de una pila de aplicaciones Bitnami en Windows, Mac OS y Linux. Cada instalador incluye todo el software necesario para ejecutarse.

Nos bajamos el paquete Wordpress de bitnami:

 ``wget https://bitnami.com/redirect/to/371173/bitnami-wordpress-4.9.8-3-linux-x64-installer.run``
 
 En caso de que este enlaze no funcione nos vamos a  https://bitnami.com/stacks elegimos la aplicacion que queremos instalar 
  
 Cambiamos permisos para ejecutarlo, se pone en verde el archivo: 
 
 ``sudo chmod 755 bitnami-wordpress-4.9.8-3-linux-x64-installer.run``
 
 Instalamos:
 
 ``sudo ./bitnami-wordpress-4.9.8-3-linux-x64-installer.run``
 
 Comenzara un asistente para configurar el Wordpress seguimos los pasos.
 
 Copiamos IPv4 Public IP lo pegamos en el buscador y accedemos
 
 ## Finalizar la instancia
En la consola de EC2. Haga clic en el botón Actions de la maquina que se quiere eliminar, vaya a ``Instance State`` y apareceran diferentes opciones ente ellas

- ``start`` inicio  de la maquina.

- ``stop`` apagar  de la maquina.

- ``reboot`` reinicio de la maquina.

- ``terminate`` eliminacion de la  maquina, este proceso dura varios minutos hasta que se finalize por completa la estancia.
