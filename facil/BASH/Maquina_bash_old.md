# BASH — Hack The Box

**Plataforma:** Hack The Box  
**Dificultad:** Easy  
**SO:** Linux  
**Fecha:** 2026-05-13  
**Técnicas:** Enumeración Web, Directory Bruteforcing, Command Execution, Reverse Shell, Sudo Abuse, Privilege Escalation


![[20260513230452.png]]

Explicación de parámetros
Parámetro	Función
-sCV	Ejecuta detección de versiones y scripts NSE
-T5	Timing agresivo para acelerar el escaneo


exploramos la pagina
![[20260513230638.png]]


Hacemos un gobuster especificando la IP, un diccionario y los tipos de ficheros que queremos que nos liste

![[20260513230643.png]]


en el siguiente directorio 

![[20260513230726.png]]


si exploramos un poco, podemos encontrarnos con una phpbash.php que ejecuta comandos 

ahora generamos una reverse shell

![[20260513230811.png]]

la ejecutamos 

![[20260513230819.png]]

nos podemos en escucha 

![[20260513230827.png]]

ahora exploramos en los directorios hasta encontrar la flag de usuario

![[20260513230847.png]]


escalada 

vemos si este usuario tiene permisos sudoers y vemos que podemos logearnos facilmente al usuario 

![[20260513230859.png]]


buscamos ficheros con el usuario en el directorio raiz 

![[20260513230945.png]]

vemos un .py asi que vamos a ver que contiene
revisamos los permisos y lo que hace el script

![[20260513231023.png]]

creamos el siguiente script para hacer una reverse shell 


![[20260513231116.png]]

nos ponemos en escucha en un puerto diferente


![[20260513231134.png]]

vamos abrir un servidor python para compartirnos con la maquina victima ficheros
![[20260513231216.png]]

con wget obtenemos el scritp


![[20260513231220.png]]

al ejecutarlo vemos que nos da el usuario root que es lo que hacia el script 

![[20260513231317.png]]

conseguimos la flag de root.

![[20260513231328.png]]
