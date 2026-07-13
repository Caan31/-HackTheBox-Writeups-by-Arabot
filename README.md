<div align="center">

# 🟢 Hack The Box — Writeups by Arabot

**Resoluciones paso a paso · En español · Para principiantes**

[![Máquinas resueltas](https://img.shields.io/badge/Máquinas%20resueltas-21-00ff88?style=flat-square&logo=hackthebox&logoColor=white)](#)
[![Fácil](https://img.shields.io/badge/Fácil-20-00cc66?style=flat-square)](#-fácil)
[![Medio](https://img.shields.io/badge/Medio-1-ffb703?style=flat-square)](#-medio)
[![Autor](https://img.shields.io/badge/Autor-Arabot-ff6b35?style=flat-square&logo=github&logoColor=white)](https://github.com/Caan31)

> *"La mejor forma de aprender hacking es hackeando — y documentándolo."*

</div>

---

## ¿Qué encontrarás aquí?

Writeups de máquinas **retiradas** de [Hack The Box](https://www.hackthebox.com/) resueltas desde cero. Cada resolución sigue la misma estructura:

**Reconocimiento → Enumeración → Explotación → Escalada de privilegios → Lección aprendida**

Todas las máquinas incluyen **capturas de pantalla reales** de cada paso. El objetivo es que entiendas **por qué** funciona cada técnica, no solo el qué.

> ⚠️ Solo se publican writeups de máquinas **retiradas** de HTB, respetando las normas de la plataforma.

---

## 🗂️ Estructura del repositorio

```
HackTheBox-Writeups-by-Arabot/
├── README.md
└── facil/
    ├── BASH/      → Bashed_Writeup.md  + Imagenes/
    ├── CAP/       → Cap_Writeup.md     + Imagenes/
    ├── GRANDPA/   → Grandpa_Writeup.md + Imagenes/
    ├── IRKED/     → Irked_Writeup.md   + Imagenes/
    ├── JERRY/     → Jerry_Writeup.md   + Imagenes/
    ├── KEEPER/    → Keeper_Writeup.md  + Imagenes/
    ├── KNIFE/     → Knife_Writeup.md   + Imagenes/
    ├── LAME/      → Lame_Writeup.md    + Imagenes/
    ├── LEGACY/    → Legacy_Writeup.md  + Imagenes/
    ├── LOVE/      → Love_Writeup.md    + Imagenes/
    ├── MIRAI/     → Mirai_Writeup.md   + Imagenes/
    ├── NETMON/    → Netmon_Writeup.md  + Imagenes/
    ├── NIBBLES/   → Nibbles_Writeup.md + Imagenes/
    ├── PREVISE/   → Previse_Writeup.md + Imagenes/
    ├── RETURN/       → Return_Writeup.md       + Imagenes/
    ├── SCRIPTKIDDIE/ → ScriptKiddie_Writeup.md + Imagenes/
    ├── SHOCKER/      → Shocker_Writeup.md      + Imagenes/
    ├── SPECTRA/      → Spectra_Writeup.md      + Imagenes/
    ├── TOOLBOX/      → Toolbox_Writeup.md      + Imagenes/
    └── VALIDATION/   → Validation_Writeup.md   + Imagenes/
└── medio/
    └── APOCALYST/ → Apocalyst_Writeup.md + Imagenes/
```

---

## 🟢 Fácil

> Máquinas ideales para empezar en HTB. Técnicas fundamentales de pentesting.

| # | Máquina | SO | Técnicas principales | Writeup |
|:-:|---------|:--:|---------------------|:-------:|
| 1 | **Bashed** | 🐧 | Nmap · Gobuster · Webshell `phpbash.php` · Sudo `scriptmanager` · CRON job hijacking → root | [📄 Ver](./facil/BASH/Bashed_Writeup.md) |
| 2 | **Cap** | 🐧 | Nmap · **IDOR** en `/data/<id>` · Análisis de PCAP en Wireshark · Credenciales FTP en claro · `cap_setuid` sobre Python → root | [📄 Ver](./facil/CAP/Cap_Writeup.md) |
| 3 | **Grandpa** | 🪟 | Nmap · IIS 6.0 · WebDAV · **CVE-2017-7269** (`ScStoragePathFromUrl`) · `SeImpersonatePrivilege` · `churrasco.exe` → SYSTEM | [📄 Ver](./facil/GRANDPA/Grandpa_Writeup.md) |
| 4 | **Irked** | 🐧 | Nmap · UnrealIRCd 3.2.8.1 backdoor · Esteganografía con `steghide` · SUID binario `viewuser` → root | [📄 Ver](./facil/IRKED/Irked_Writeup.md) |
| 5 | **Jerry** | 🪟 | Nmap · Apache Tomcat · Credenciales por defecto · Despliegue WAR · Reverse shell JSP → SYSTEM | [📄 Ver](./facil/JERRY/Jerry_Writeup.md) |
| 6 | **Keeper** | 🐧 | Nmap · Request Tracker (credenciales por defecto) · **CVE-2023-32784** (KeePass memory dump) · Clave PuTTY `.ppk` → root | [📄 Ver](./facil/KEEPER/Keeper_Writeup.md) |
| 7 | **Knife** | 🐧 | Nmap · `whatweb` · **PHP 8.1.0-dev backdoor** (`User-Agentt: zerodium…`) · Sudo `knife exec` (GTFOBins) → root | [📄 Ver](./facil/KNIFE/Knife_Writeup.md) |
| 8 | **Lame** | 🐧 | Nmap · Samba 3.0.20 · **CVE-2007-2447** (Username Map Script) · Explotación manual desde `smbclient` → root directo | [📄 Ver](./facil/LAME/Lame_Writeup.md) |
| 9 | **Legacy** | 🪟 | Nmap · SMB · Windows XP · **MS08-067** (CVE-2008-4250, NetAPI Buffer Overflow) · Metasploit → SYSTEM directo | [📄 Ver](./facil/LEGACY/Legacy_Writeup.md) |
| 10 | **Love** | 🪟 | Nmap · Certificado SSL (virtual host) · wfuzz · **SSRF** · Voting System 1.0 RCE · **`AlwaysInstallElevated`** · msfvenom MSI → SYSTEM | [📄 Ver](./facil/LOVE/Love_Writeup.md) |
| 11 | **Mirai** | 🐧 | Nmap · Raspberry Pi · Pi-hole · **Credenciales por defecto** (`pi:raspberry`) · `sudo NOPASSWD: ALL` · Recuperación forense con `strings` → root | [📄 Ver](./facil/MIRAI/Mirai_Writeup.md) |
| 12 | **Netmon** | 🪟 | Nmap · FTP anónimo · Backup de PRTG (`PRTG Configuration.old.bak`) · Credenciales en claro · **CVE-2018-9276** (command injection) · `psexec` → SYSTEM | [📄 Ver](./facil/NETMON/Netmon_Writeup.md) |
| 13 | **Nibbles** | 🐧 | Nmap · Gobuster · Nibbleblog 4.0.3 · Credenciales por defecto (`admin:nibbles`) · **Arbitrary File Upload** (plugin *My image*) · Reverse shell · `sudo NOPASSWD` sobre ruta inexistente → root | [📄 Ver](./facil/NIBBLES/Nibbles_Writeup.md) |
| 14 | **Previse** | 🐧 | Nmap · Gobuster · Burp Suite · **Forced Browsing** (bypass 302) · Creación de cuenta vía `accounts.php` · `siteBackup.zip` · **Command Injection** en `logs.php` · Hashcat (`$1$` MD5 crypt) · `sudo` + **PATH Hijacking** → root | [📄 Ver](./facil/PREVISE/Previse_Writeup.md) |
| 15 | **Return** | 🪟 | Nmap · Active Directory (`return.local`) · Panel web de impresora · **Rogue LDAP Server** (captura de credenciales en claro) · `crackmapexec` + `evil-winrm` · Grupo **Server Operators** · `sc.exe config binPath` (service hijacking) → SYSTEM | [📄 Ver](./facil/RETURN/Return_Writeup.md) |
| 16 | **ScriptKiddie** | 🐧 | Nmap · Flask/Werkzeug (5000) · **CVE-2020-7384** (msfvenom APK template injection) · Reverse shell · Pivot vía inyección en log (`scanlosers.sh`) · `sudo NOPASSWD` + `msfconsole` → root | [📄 Ver](./facil/SCRIPTKIDDIE/ScriptKiddie_Writeup.md) |
| 17 | **Shocker** | 🐧 | Nmap · Wfuzz (dir + ext) · Apache `mod_cgi` · **Shellshock (CVE-2014-6271)** vía `User-Agent` en `/cgi-bin/user.sh` · Reverse shell · `sudo NOPASSWD` sobre `perl` (GTFOBins) → root | [📄 Ver](./facil/SHOCKER/Shocker_Writeup.md) |
| 18 | **Spectra** | 🐧 | Nmap · Virtual host `spectra.htb` · Directory listing · `wp-config.php.save` filtrado · Reutilización de credenciales en WordPress admin · Editor de plugins (RCE) · Reverse shell · ChromeOS/Upstart · Job `initctl` escribible (`chmod u+s`) → root | [📄 Ver](./facil/SPECTRA/Spectra_Writeup.md) |
| 19 | **Toolbox** | 🪟 | Nmap · Virtual host `admin.megalogistic.com` · **PostgreSQL SQL Injection** (stacked queries) · RCE vía `COPY FROM PROGRAM` · Reverse shell · Pivot a Boot2Docker (`docker:tcuser`) · Carpeta compartida `/c` de Docker Toolbox · Robo de clave SSH de Administrator → Administrator | [📄 Ver](./facil/TOOLBOX/Toolbox_Writeup.md) |
| 20 | **Validation** | 🐧 | Nmap · **SQL Injection** en formulario de registro (`country`) · Error-based (ruta absoluta filtrada) · RCE vía `UNION SELECT ... INTO OUTFILE` (webshell) · Reverse shell · Credenciales de `config.php` reutilizadas en `su root` → root | [📄 Ver](./facil/VALIDATION/Validation_Writeup.md) |

---

## 🟡 Medio

> Máquinas que exigen encadenar varias técnicas y ser más metódico en la enumeración.

| # | Máquina | SO | Técnicas principales | Writeup |
|:-:|---------|:--:|---------------------|:-------:|
| 1 | **Apocalyst** | 🐧 | Nmap · Gobuster · CeWL (diccionario propio) · Wfuzz (página oculta) · Esteganografía `steghide` (diccionario de contraseñas oculto) · WPScan (enumeración + fuerza bruta) · WordPress Theme Editor RCE · `/etc/passwd` escribible → root | [📄 Ver](./medio/APOCALYST/Apocalyst_Writeup.md) |

---

## 🎯 Por técnica

Si te interesa una vulnerabilidad concreta, aquí tienes el atajo:

| Categoría | Máquina(s) |
|-----------|------------|
| **CVEs clásicas** | [Grandpa](./facil/GRANDPA/Grandpa_Writeup.md) (CVE-2017-7269) · [Irked](./facil/IRKED/Irked_Writeup.md) / [Lame](./facil/LAME/Lame_Writeup.md) (CVE-2007-2447) · [Legacy](./facil/LEGACY/Legacy_Writeup.md) (MS08-067) · [Keeper](./facil/KEEPER/Keeper_Writeup.md) (CVE-2023-32784) · [Netmon](./facil/NETMON/Netmon_Writeup.md) (CVE-2018-9276) · [ScriptKiddie](./facil/SCRIPTKIDDIE/ScriptKiddie_Writeup.md) (CVE-2020-7384) · [Shocker](./facil/SHOCKER/Shocker_Writeup.md) (CVE-2014-6271 / Shellshock) |
| **Credenciales por defecto / débiles** | [Jerry](./facil/JERRY/Jerry_Writeup.md) (Tomcat) · [Keeper](./facil/KEEPER/Keeper_Writeup.md) (Request Tracker) · [Mirai](./facil/MIRAI/Mirai_Writeup.md) (Raspberry Pi) · [Netmon](./facil/NETMON/Netmon_Writeup.md) (patrón `Base+Año`) · [Nibbles](./facil/NIBBLES/Nibbles_Writeup.md) (`admin:nibbles`) · [Toolbox](./facil/TOOLBOX/Toolbox_Writeup.md) (Boot2Docker `docker:tcuser`) |
| **Backdoors en software** | [Irked](./facil/IRKED/Irked_Writeup.md) (UnrealIRCd) · [Knife](./facil/KNIFE/Knife_Writeup.md) (PHP 8.1.0-dev) |
| **Web exploitation** | [Bashed](./facil/BASH/Bashed_Writeup.md) (phpbash) · [Jerry](./facil/JERRY/Jerry_Writeup.md) (Tomcat WAR) · [Grandpa](./facil/GRANDPA/Grandpa_Writeup.md) (WebDAV) · [Cap](./facil/CAP/Cap_Writeup.md) (IDOR) · [Love](./facil/LOVE/Love_Writeup.md) (SSRF + RCE) · [Netmon](./facil/NETMON/Netmon_Writeup.md) (PRTG command injection) · [Nibbles](./facil/NIBBLES/Nibbles_Writeup.md) (Nibbleblog file upload) · [Previse](./facil/PREVISE/Previse_Writeup.md) (forced browsing + command injection) · [Return](./facil/RETURN/Return_Writeup.md) (rogue LDAP + service hijack) · [ScriptKiddie](./facil/SCRIPTKIDDIE/ScriptKiddie_Writeup.md) (Flask wrapper + msfvenom) · [Shocker](./facil/SHOCKER/Shocker_Writeup.md) (Shellshock CGI) · [Toolbox](./facil/TOOLBOX/Toolbox_Writeup.md) (PostgreSQL SQLi) · [Validation](./facil/VALIDATION/Validation_Writeup.md) (MySQL SQLi → webshell) · [Apocalyst](./medio/APOCALYST/Apocalyst_Writeup.md) (WordPress Theme Editor RCE) |
| **SQL Injection** | [Toolbox](./facil/TOOLBOX/Toolbox_Writeup.md) (PostgreSQL stacked queries + `COPY FROM PROGRAM` → RCE) · [Validation](./facil/VALIDATION/Validation_Writeup.md) (MySQL `UNION SELECT ... INTO OUTFILE` → RCE) |
| **SSRF (Server-Side Request Forgery)** | [Love](./facil/LOVE/Love_Writeup.md) (File Scanner → servicio interno) |
| **Sudo abuse / GTFOBins** | [Bashed](./facil/BASH/Bashed_Writeup.md) (scriptmanager) · [Knife](./facil/KNIFE/Knife_Writeup.md) (`knife exec`) · [Mirai](./facil/MIRAI/Mirai_Writeup.md) (`NOPASSWD: ALL`) · [Nibbles](./facil/NIBBLES/Nibbles_Writeup.md) (`NOPASSWD` + path creation) · [Previse](./facil/PREVISE/Previse_Writeup.md) (`sudo` + PATH hijacking) · [ScriptKiddie](./facil/SCRIPTKIDDIE/ScriptKiddie_Writeup.md) (`sudo msfconsole` → `!bash`) · [Shocker](./facil/SHOCKER/Shocker_Writeup.md) (`sudo perl -e 'exec ...'`) |
| **SUID / Linux Capabilities** | [Irked](./facil/IRKED/Irked_Writeup.md) (`viewuser`) · [Cap](./facil/CAP/Cap_Writeup.md) (`cap_setuid` en Python) |
| **Privilege escalation Windows** | [Grandpa](./facil/GRANDPA/Grandpa_Writeup.md) (churrasco / SeImpersonate) · [Love](./facil/LOVE/Love_Writeup.md) (`AlwaysInstallElevated`) · [Netmon](./facil/NETMON/Netmon_Writeup.md) (servicio PRTG como SYSTEM) · [Return](./facil/RETURN/Return_Writeup.md) (Server Operators + `sc.exe binPath`) |
| **Gestores de contraseñas / secretos** | [Keeper](./facil/KEEPER/Keeper_Writeup.md) (KeePass + clave PuTTY) |
| **Análisis de red / PCAP** | [Cap](./facil/CAP/Cap_Writeup.md) (Wireshark + IDOR) |
| **Esteganografía** | [Irked](./facil/IRKED/Irked_Writeup.md) (`steghide`) · [Apocalyst](./medio/APOCALYST/Apocalyst_Writeup.md) (`steghide`, diccionario de contraseñas oculto) |
| **Análisis forense / recuperación de datos** | [Mirai](./facil/MIRAI/Mirai_Writeup.md) (`strings` sobre `/dev/sdb`) |
| **CRON job hijacking** | [Bashed](./facil/BASH/Bashed_Writeup.md) |
| **SMB enumeration & exploitation** | [Lame](./facil/LAME/Lame_Writeup.md) · [Legacy](./facil/LEGACY/Legacy_Writeup.md) |
| **Permisos de ficheros del sistema mal configurados** | [Apocalyst](./medio/APOCALYST/Apocalyst_Writeup.md) (`/etc/passwd` con permisos 666 → root) |

---

## 🔜 Próximamente

| Máquina | SO | Dificultad | Estado |
|---------|:--:|:----------:|:------:|
| Blue | 🪟 | Fácil | 📋 Pendiente |
| Devel | 🪟 | Fácil | 📋 Pendiente |

---

## 🗺️ ¿Por dónde empiezo?

Si vienes de DockerLabs y quieres dar el salto a HTB:

```
1. Crea tu cuenta en hackthebox.com (es gratis)
2. Conéctate a la VPN de HTB (Starting Point te guía)
3. Empieza con Legacy o Lame — son las más accesibles (un único exploit)
4. Sigue con Bashed, Jerry o Cap — añaden enumeración manual
5. Lee el writeup DESPUÉS de intentarlo tú solo
6. Ve subiendo de dificultad a tu ritmo
```

La diferencia principal con DockerLabs es que en HTB las máquinas son más realistas y necesitas conectarte por VPN. Pero si ya resuelves máquinas fáciles de DockerLabs, estás preparado.

---

## 📚 Más writeups

| Plataforma | Repositorio | Máquinas |
|-----------|-------------|:--------:|
| 🐋 DockerLabs | [Ver repositorio](https://github.com/Caan31/-DockerLabs-Writeups-by-Arabot) | 64 |
| 🟢 Hack The Box | Estás aquí | 21 |

---

<div align="center">

**¿Te ha ayudado algún writeup?** Dale una ⭐ — ayuda a que más gente lo encuentre.

[![GitHub](https://img.shields.io/badge/Más%20contenido-github.com/Caan31-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Caan31)
[![Blog](https://img.shields.io/badge/Blog-arabot.org-21759B?style=flat-square&logo=wordpress&logoColor=white)](https://arabot.org)

*Arabot · Aprendiendo en público · Ciberseguridad en español* 🇪🇸

</div>
