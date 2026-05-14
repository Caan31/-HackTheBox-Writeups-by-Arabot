<div align="center">

# 🟢 Hack The Box — Writeups by Arabot

**Resoluciones paso a paso · En español · Para principiantes**

[![Máquinas resueltas](https://img.shields.io/badge/Máquinas%20resueltas-2-00ff88?style=flat-square&logo=hackthebox&logoColor=white)](#)
[![Fácil](https://img.shields.io/badge/Fácil-2-00cc66?style=flat-square)](#-fácil)
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
    ├── BASH/
    │   ├── Imagenes/
    │   └── Bashed_Writeup.md
    └── JERRY/
        ├── Imagenes/
        └── Jerry_Writeup.md
```

---

## 🟢 Fácil

> Máquinas ideales para empezar en HTB. Técnicas fundamentales de pentesting.

| Máquina | SO | Técnicas principales | Writeup |
|---------|:--:|---------------------|:-------:|
| Bashed | 🐧 | Nmap · Gobuster · Webshell phpbash · sudo scriptmanager · CRON root | [📄 Ver](./facil/BASH/Bashed_Writeup.md) |
| Jerry | 🪟 | Nmap · Apache Tomcat · Credenciales por defecto · WAR reverse shell · SYSTEM | [📄 Ver](./facil/JERRY/Jerry_Writeup.md) |

---

## 🔜 Próximamente

Más máquinas en camino. Las siguientes en la lista:

| Máquina | SO | Dificultad | Estado |
|---------|:--:|:----------:|:------:|
| Lame | 🐧 | Fácil | 🔄 En progreso |
| Blue | 🪟 | Fácil | 📋 Pendiente |
| Netmon | 🪟 | Fácil | 📋 Pendiente |
| Shocker | 🐧 | Fácil | 📋 Pendiente |
| Nibbles | 🐧 | Fácil | 📋 Pendiente |

---

## 🗺️ ¿Por dónde empiezo?

Si vienes de DockerLabs y quieres dar el salto a HTB:

```
1. Crea tu cuenta en hackthebox.com (es gratis)
2. Conéctate a la VPN de HTB (Starting Point te guía)
3. Empieza con Bashed o Jerry — son las más accesibles
4. Lee el writeup DESPUÉS de intentarlo tú solo
5. Ve subiendo de dificultad a tu ritmo
```

La diferencia principal con DockerLabs es que en HTB las máquinas son más realistas y necesitas conectarte por VPN. Pero si ya resuelves máquinas fáciles de DockerLabs, estás preparado.

---

## 📚 Más writeups

| Plataforma | Repositorio | Máquinas |
|-----------|-------------|:--------:|
| 🐋 DockerLabs | [Ver repositorio](https://github.com/Caan31/-DockerLabs-Writeups-by-Arabot) | 64 |
| 🟢 Hack The Box | Estás aquí | 2 |

---

<div align="center">

**¿Te ha ayudado algún writeup?** Dale una ⭐ — ayuda a que más gente lo encuentre.

[![GitHub](https://img.shields.io/badge/Más%20contenido-github.com/Caan31-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Caan31)
[![Blog](https://img.shields.io/badge/Blog-arabot.org-21759B?style=flat-square&logo=wordpress&logoColor=white)](https://arabot.org)

*Arabot · Aprendiendo en público · Ciberseguridad en español* 🇪🇸

</div>
