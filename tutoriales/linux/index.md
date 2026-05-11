# Todo lo que tienes que saber sobre Linux y su accesibilidad
## 1. Linux, lo que tienes que saber
## 1.1. ¿Qué es Linux?
Linux es, un kenrel que se encarga de gestionar directamente el hardware, sobre el cual se instalan diferentes programas, tales como un intérprete de comandos (generalmente bash) o entornos de escritorio (que nos permitirá navegar un sistema Linux con teclado y ratón) todo sobre el kernel.  
## 1.2. ¿Qué es un kernel?
Un kernel es la capa más baja de un sistema operativo, que se encarga de gestionar el hardware y diferentes procesos generados por software.  
Para que nos entendamos. Ees lo que le permite al sistema funcionar. Sin kernel, no hay sistema operativo.
## 1.2. El intérprete de comandos, tty
La tty es la primera capa de sistema que tiene contacto con el usuario. Si eres un usuario con poderes administrativos, puedes hacer todo en tu sistema. Desde eliminar archivos importantes, que impidan al sistema arrancar, todo desde comandos. Es decir, la tty es un prompt de comandos en el que sólo interactúas con texto. Aquí te ofrezco algunos comandos para que veas qué ocurre desde que inicia tu sistema y entras a la tty:  
Nota: El prompt que usaremos es bash, ya que es el más común en las distros de Linux más conocidas.  
```
cd: se utiliza para moverse entre carpetas
ls: Lista los diversos archivos / carpetas que tengas en esa ubicación
pwd: este comando se encarga de proporcionarte la ruta en la que te encuentras.
rm: Este comando es muy arriesgado. Elimina un archivo / carpeta (con el flag -r) sin confirmación.
sudo su: ¡Cuidado! úsalo con frecuencia. Si estás en los sudoers, este comando te ayudará a entrar como administrador (root)
```
Y así, podemos seguir sin parar, dependiendo de los paquetes que instales.
## 1.2.1. Soy una persona ciega y quiero usar la tty. ¿Cómo lo hago?
Primero que todo, esto dependerá mucho de tu dispositivo:
* Si tienes una raspberry pi con raspberry pi os lite y wifi, puedes configurar ssh y conectarte a una tty para instalar las herramientas necesarias para usarla.
* En un sistema tipo debian, lo más común es instalar un entorno de escritorio, ya sea mate, gnome, Xfce, kde…
Con esto en cuenta, vamos a aprender a instalar un lector de pantalla en la tty, antes de cambiar a ella. Esto en una raspberry pi lo haces desde tu PC, y en un debian con entorno gráfico, lo realizas desde el emulador de terminal de ese mismo escritorio. Por ejemplo, si usas mate (a mi juicio el mejor entorno para accesibilidad si buscas escritorios ligeros y parecidos a windows) abre la terminal con alt+control+t, y escribe, ya sea que estés en la terminal remota de la pi o en el sistema debian con el emulador de terminal, los siguientes comandos, asumiendo que ya estés conectado a la red wifi.
```
sudo apt update
sudo apt install espeakup -y
sudo systemctl enable espeakup
sudo systemctl start espeakup
```
Ahora, si estás en debian, escribe
```
sudo systemd set default multi-user-target
```
Y ahora, reinicia el sistema operativo, esto en ambos, sea pi o debian.
```
sudo reboot
```
Listo, ya tienes tty. Ahora verás que puedes usar tu sistema, con una voz en inglés, llamada espeak-ng.
## 2. Entorno de escritorio (desktop enevironment)
Esto es lo más parecido a Windows. Permite que tu sistema tenga una interfaz gráfica de usuario. Todo sistema menos arch Linux y algunos diseñados para usuarios avanzados tiene entorno de escritorio, ya sea mate, gnome, lxde, Xfce, kde, etc.  
Recomiendo, si tienes una raspberry pi y quieres instalarle un entonro como los que vienen en debian y tener accesibilidad, consultes el tutorial provisto en esta página.
## 2.1. Servidor gráfico
El servidor gráfico es el que se encarga de mostrar la interfaz gráfica de usuario, gui. Existen 2 servidores gráficos principales.
* xorg: Este es el servidor que mejor se lleva con accesibilidad y orca (lector de pantalla).
* Wayland: Este servidor es más moderno que xorg, pero la accesibilidad es menos madura y es más pesado.
##2.1.2. ¿Qué diferencia a xor y a wayland?
Lamentablemente, no puedo responder a esto, porque sólo probé xorg.  
Si encuentro información sobre esto, la pondré aquí.
## 3. Accesibilidad en Linux para personas con discapacidad visual
Linux  es un sistema que cada vez se hace más accesible, pero no llega al nivel de windows.  
Windows es un sistema ya maduro a lo que accesibilidad respecta, ya que tenemos lectores de pantalla como Jaws y NVDA, que ya se están haciendo un hueco hace ya mucho tieimpo.  
En linux podemos hacer tareas tales como navegar por Internet, escribir documentos, programar, compilar software... de forma cómoda con el lector de pantalla orca. Sin embargo, hay muchas aplicaciones que no son accesiibles en linux y en windows sí que lo son. Destacamos por ejemplo raspberry pi imagerr, que no expone nada al lector de pantalla, y en windows es casi accesible en su totalidad.
## 4. En conclusión
Linux es un sistema muy bueno, pero necesita avanzar mucho en tecnologías de asistencia. Espero que con el paso de los años y con la actualización de las tecnologías de accesibilidad, linux se haga un hueco entre los sistemas que usen las personas con discapacidad visual.  
Sé de gente ciega que utiliza sistemas linux a diario, reemplazando a windows en su vida. Yo, al adquirir mi raspberry pi, me estoy introduciendo más en este mundo de Linux y el software libre.  
Recomiendo a todos que le hecheis un vistazo a este sistema, ya sea en live usb o en placas raspberry si quieres ir más allá, si te interesan estos temas.  
Espero que hayas aprendido mucho en esta pequeña guía introductoria al mundo Linux.  
¡Un saludo a todos!