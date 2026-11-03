# Proyecto 1 · Know Your Target

**Autor:** Hugo Pérez Arévalo.  
**Asignatura / Módulo:** Auditoría de Seguridad / Hacking Ético  
**Fecha de consulta:** 30/10/2026  

---

##  Objetivo Seleccionado

* **Organización:** Kiwi.com
* **Programa:** Bug Bounty Oficial en HackerOne
* **URL del Programa:** [https://hackerone.com/kiwicom/policy_scopes](https://hackerone.com/kiwicom/policy_scopes)
* **Alcance Principal:** Dominio comodín `*.kiwi.com`

---

##  Descripción del Proyecto

Este proyecto consiste en realizar un reconocimiento pasivo (OSINT) exhaustivo sobre la infraestructura pública de Kiwi.com siguiendo las reglas de su programa de Bug Bounty en HackerOne.

El trabajo se divide en dos fases principales:
1. **Fase Manual:** Identificación pasiva de la superficie de ataque, registro pormenorizado de comandos y hallazgos en un cuaderno de trabajo, y redacción final del mapa de superficie.
2. **Fase Automatizada (IA):** Extensión de un agente de reconocimiento con *scope-guard* para auditar el alcance de forma autónoma y comparar críticamente su desempeño frente al trabajo humano.

---

##  Estructura y Enlaces a los Documentos

Todos los entregables del proyecto se encuentran organizados en este repositorio:

| Documento | Descripción |
| :--- | :--- |
|  [`alcance.md`](./alcance.md) | Resumen de la política oficial, reglas de compromiso, restricciones y política de *Core Ineligible Findings*. |
|  [`scope.txt`](./scope.txt) | Fichero en texto plano con los objetivos en alcance y exclusiones estrictas (`!`) preparado para herramientas y el agente de IA. |
|  [`cuaderno.md`](./cuaderno.md) | Cuaderno de laboratorio con el registro temporal (*Cuándo · Objetivo · Qué hice · Qué salió · Siguiente paso*) de cada técnica pasiva ejecutada. |
|  [`mapa.md`](./mapa.md) | Informe final de superficie de ataque entregado al equipo antes de la fase activa (subdominios, infraestructura, tecnologías, correos y puntos de interés). |

---

##  Herramientas y Técnicas Pasivas Utilizadas

* **Registros DNS & Dominio:** `whois`, `dig` (registros TXT, MX, SPF).
* **Enumeración de Subdominios:** `subfinder`, `crt.sh`, `theHarvester`.
* **Huella Tecnológica & Infraestructura:** Netcraft, Wappalyzer, consulta de registros `robots.txt` y `sitemap.xml`.
* **Servicios Expuestos & OSINT:** Shodan / InternetDB, Google Dorks.

---

##  Declaración de Ética y Cumplimiento

* **Técnicas 100% Pasivas:** No se ha realizado escaneo de puertos activo, fuerza bruta ni lanzamiento de escáneres de vulnerabilidades.
* **Sin Interacción Humana:** No se ha contactado con ningún empleado, cliente ni canal de soporte de la organización.
* **Respeto al Scope:** Todas las consultas se han mantenido estrictamente dentro de los límites autorizados por la política de Kiwi.com en HackerOne.