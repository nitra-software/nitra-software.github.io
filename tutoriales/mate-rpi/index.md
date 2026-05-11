# Tutorial de instalación de mate en raspberry pi os lite

¡Hola a todos!  
En este pequeño tutorial, veremos, para aquellos que tengáis una raspberry pi, cómo instalar mate, lightdm y orca en la misma.

## Requisitos

Lo que necesitaremos es lo siguiente:

* Una placa raspberry pi, en mi caso, una raspberry pi4b.
* Un teclado externo, para usarlo en la raspberry pi.
* Raspberry pi imager instalado en algún sistema operativo, para este tutorial usaremos Windows.
* Una microSD, una memoria USB/disco duro externo (sólo en versiones recientes del bootloader)
* Una conexión a Internet.

## Instalación del sistema operativo

Vamos a proceder a instalar el sistema operativo raspberry pi os lite:

* En la primera pantalla, escogeremos nuestro modelo de raspberry pi. En mi caso escogeré raspberry pi4. Lo seleccionamos con espacio, y pasará a la pantalla siguiente.
* Aquí, seleccionaremos nuestro sistema operativo. Nos desplazamos con flecha abajo hasta la opción Raspberry Pi OS (other). Other Raspberry Pi OS based images"
* Hecho esto, seleccionamos el sistema operativo en sí. En mi caso, seleccionaré la primera opción, que es la versión de 64 bit
* Ahora, seleccionamos el dispositivo de almacenamiento. Lo seleccionas como en las pantallas anteriores.
* Tras eso, comenzamos con las personalizaciones. Nombre de equipo, red wifi, ssh... todo esto es muy intuitivo.  
  Sólo una recomendación final. Te recomiendo que actives ssh, para que la puedas usar con tu lector de pantalla preferido desde un sistema que ya conozcas.

### Arranque del sistema

Bien. Una vez que se complete el proceso de instalación, enchufamos la raspberry pi a una toma de corriente, esperamos un poco, y nos conectamos con el nombre de equipo que le pusimos por ssh. Esta es la sintaxis.  
ssh usuario@host.local  
Ahora, el cliente ssh te pedirá confirmar si realmente quieres conectarte, escribimos yes, y pulsamos enter.  
Ahora te pedirá la contraseña. La escribimos, y listo. ¡Ya estamos en Linux!

### Instalación del escritorio

A continuación, toca instalar un escritorio sobre este sistema. Ahora te indicaré cómo hacerlo paso a paso.  
El proceso es sencillo, pero te puede frustrar si, como yo, eres nuevo en este mundillo.

* Actualizamos los paquetes: sudo apt update \&\& sudo apt full-upgrade -y
* Instalamos el escritorio mate, lightdm y orca: sudo apt install mate-desktop-environment lightdm orca -y  
  Configuramos lightdm para que haga autologin con nuestro usuario. Para ello, abriremos con nano la configuración de lightdm con el siguiente comando: sudo nano /etc/lightdm/lightdm.conf
* Una vez abierto el archivo con nano, vamos al inicio, pulsamos alt+a,  bajamos al final del archivo, y pulsamos control+k para borrarlo todo.
* Ahora, introduciremos el siguiente contenido. Reemplaza Tu\_Usuario con el usuario real de tu sistema:  
  \[Seat:\*]  
  autologin-user=tu\_usuario  
  autologin-user-timeout=0  
  user-session=mate  
  greeter-session=lightdm-gtk-greeter
  Guardamos con control+s, y salimos con control+x.

### Prueba del escritorio

Si has llegado hasta aquí, estás a un punto de tener todo listo. Quedan ya unos pocos pasos.  
Si quieres configurarlo en español, lo puedes hacer de forma sencilla desde sudo raspi-config  
Ahora, reinicia la máquina con sudo reboot, y por si acaso, vuelve a conectarte por ssh.  
Conecta el teclado, pulsa alt+super (windows en la mayoría de teclados)+s, espera unos segundos y, si se activa orca, ¡Genial!  Realizaste el tutorial de forma correcta.
# Bonus extra. Hacerle creer a la raspberry pi que hay una pantalla conectada.
Aveces, sólo queremos usar el escritorio con nuestro ladrillo tecnológico simplemente sin pantalla, sin conectarlo a un monitor, con nuestros auriculares bluetooth o cable. Esto tiene fácil solución: vamos a modificar un archivo, que se encuentra en la partición fat32, o, si lla estás usando la raspberry pi, en /boot/firmware/  
El archivo en cuestión se llama config.txt. Vamos a editarlo, añadiendo un par de líneas. Pónlas al final del archivo.  
```
hdmi_force_hotplug=1
hdmi_group=2
hdmi_mode=4
```
Esto nos indica que la pi activará siempre la salida hdmi, en un monitor de pc, en un modo mínimo para que la gpu quede fresca y no tenga que renderizar mucho contenido y mate arranque.  
Esto te permitirá usar la raspberry pi sin pantalla, escuchando a orca directamente desde tus  auriculares o cualquier otro dispositivo de audio.
# Despedida y conclusión
¡Muchas gracias por leer este tutorial! Así tenemos otra forma para utilizar nuestra raspberry pi.  
¡Saludos cordiales a todos, y hasta la próxima!