# Alcance del Programa: Kiwi.com

- **Enlace al programa:** https://hackerone.com/kiwicom/policy_scopes
- **Fecha de consulta:** 2026-10-28

## Dentro del alcance (In Scope)
- www.kiwi.com
- tequila.kiwi.com
- tequila-api.kiwi.com
- api.tequila.kiwi.com
- com.skypicker.Skypicker (App IOS)
- com.skypicker.main (App Android)
- auth.skypicker.com
- *.skypicker.com
- *.kiwi.com
- www.kiwi.com/stories
- jobs.kiwi.com
- vacation.kiwi.com


## Fuera del alcance (Out of Scope)
Kiwi.com para definir lo que está fuera del alcance usan las políticas estándar de HackerOne que son las siguientes:

### 1. Vulnerabilidades teóricas con interacción improbable del usuario:

- Ataques que solo funcionan en navegadores o sistemas operativos obsoletos o sin soporte (End-of-Life).

- Secuestro de enlaces rotos (Broken link hijacking).

- Tabnabbing.

- Falsificación de contenido (Content spoofing) e inyección de texto.

- Ataques que requieren acceso físico al dispositivo (salvo que el alcance lo permita explícitamente).

- Auto-explotación, como Self-XSS o Self-DoS (a menos que se pueda encadenar para atacar la cuenta de otro usuario).

### 2. Vulnerabilidades teóricas sin impacto demostrable en el mundo real:

- Clickjacking en páginas donde no se realizan acciones sensibles.

- Cross-Site Request Forgery (CSRF) en formularios sin impacto sensible (ej. forzar el cierre de sesión o Logout CSRF).

- Configuraciones CORS permisivas donde no se pueda demostrar la extracción de datos sensibles.

- Divulgación de versiones de software, identificación de banners, mensajes de error descriptivos (trazas de pila, errores de servidor).

- Inyección de CSV (Comma Separated Values).

- Redirecciones abiertas (Open redirects), a menos que sirvan para demostrar un impacto mayor (como el robo de tokens).

### 3. Falta de mejores prácticas o configuraciones de endurecimiento opcionales:

- Problemas de configuración SSL/TLS.

- Falta de SSL Pinning (fijación de certificados) en aplicaciones móviles.

- Falta de detección de jailbreak o root en aplicaciones móviles.

- Falta de flags de seguridad en las Cookies (ej. HttpOnly o Secure).

- Hallazgos basados únicamente en la configuración estricta del Content-Security-Policy (CSP).

- Falta de registros para la seguridad del correo electrónico (SPF, DKIM, DMARC).

- La gran mayoría de problemas relacionados con la falta de limitación de peticiones (Rate limiting).

## 4. Actividades peligrosas o ruidosas (Estrictamente prohibidas):

- Cualquier prueba relacionada con peticiones masivas o denegación de servicio (DoS / DDoS).

- Pruebas que puedan afectar a la disponibilidad de los sistemas de producción.

- Ingeniería social (ej. phishing a empleados, abrir tickets falsos al equipo de soporte).

- Ataques ruidosos (ej. enviar spam masivo a través de formularios o notificaciones).

- Cualquier intento de ataque físico a las instalaciones de la empresa.


## Reglas relevantes
Para la ejecución de esta auditoría, y de acuerdo tanto con las políticas del programa de Kiwi.com en HackerOne como con los requisitos del Proyecto 1, se aplicarán estrictamente las siguientes reglas:

### Reglas de interacción y herramientas (Reglas del Proyecto):

**Solo técnicas pasivas:** Queda estrictamente prohibido el uso de técnicas activas. No se realizará escaneo de puertos (Nmap), no se usarán escáneres automáticos de vulnerabilidades (Nessus, Nuclei, etc.) ni se realizarán ataques de fuerza bruta (ej. directorios con Dirb/ffuf o fuerza bruta de contraseñas). Toda la información debe obtenerse de fuentes abiertas y bases de datos públicas (OSINT).

**Cero interacción humana:** No se permite interactuar con empleados, usuarios o personal de soporte técnico bajo ningún concepto. Quedan prohibidos los mensajes directos, las solicitudes de contacto (ej. vía LinkedIn) y la creación de perfiles falsos para recabar información.

**Prohibición de cuentas:** No se crearán cuentas de usuario ni perfiles de prueba en los servicios web o aplicaciones de Kiwi.com durante esta fase.

**Gestión de hallazgos críticos:** Si durante el reconocimiento pasivo se descubre información crítica (ej. credenciales expuestas en texto claro en repositorios públicos, paneles de administración abiertos sin autenticación, o datos personales/PII expuestos), no se accederá, ni se explotará, ni se realizarán copias de seguridad de dichos datos. El protocolo a seguir será:

**Anotar el hallazgo de forma censurada** en el cuaderno de trabajo (sin incluir el dato sensible).
