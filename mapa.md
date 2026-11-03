# Mapa de Superficie de Ataque · Kiwi.com

## 1. Resumen
Kiwi.com es una plataforma global de tecnología de viajes (*travel tech*) enfocada en la búsqueda y reserva de vuelos y transporte combinado. Su superficie de ataque pasiva muestra una arquitectura distribuida que depende fuertemente de redes de distribución de contenido (CDN) como Fastly y proxies de caché Varnish para proteger sus servidores de origen. El análisis pasivo revela un stack moderno basado en **Next.js (16.4.2)** y **React**, complementado por múltiples plataformas SaaS de gestión interna (Atlassian, Notion, Miro) y servicios de inteligencia artificial (OpenAI, Anthropic, Cursor). El alcance principal cubre el dominio comodín `*.kiwi.com`, habiéndose identificado subdominios de desarrollo, APIs B2B (plataforma Tequila) y endpoints no indexados en el archivo `robots.txt`.

## 2. Dominios y subdominios

| Subdominio | IP / Proveedor | En alcance | Propósito aparente |
| :--- | :--- | :--- | :--- |
| `www.kiwi.com` | `151.101.195.42` (Fastly) | Sí | Portal web principal de reservas |
| `api.tequila.kiwi.com` | Cloudflare / GCP | Sí | API B2B de la plataforma Tequila para socios |
| `staging-tequila-fe.kiwi.com` | `151.101.67.42` (Fastly) | Sí | Entorno de pruebas (*staging*) de la interfaz Tequila |
| `graphql.kiwi.com` | Google Cloud Run | Sí | Endpoint GraphQL principal para consultas web/móvil |
| `jira.kiwi.com` | `151.101.131.42` (Fastly) | Sí | Portal de gestión de incidencias (Atlassian) |
| `dev.parking.kiwi.com` | AWS | Sí | Entorno de desarrollo para el servicio de parking |
| `kyc.kiwi.com` | Google Cloud | Sí | Servicio de verificación de identidad de usuarios |
| `skypicker-984.firebaseio.com` | Google Firebase | **No** | Instancia de Firebase excluida explícitamente en el programa |
| `kiwi-debug.firebaseio.com` | Google Firebase | **No** | Instancia de depuración excluida explícitamente |

## 3. Infraestructura y servicios

* **Hosting y Nube:** Tráfico frontal enrutado a través de **Fastly Inc.** (ASN `AS54113`), con infraestructuras de origen alojadas en **Google Cloud Platform (GCP)** y **Amazon Web Services (AWS)**.
* **Tecnologías Web Frontal:** Framework **React** con **Next.js v16.4.2**, servido mediante **Varnish v1.1** como capa de caché HTTP y compatibilidad habilitada para **HTTP/3**.
* **Protección y Pagos:** Procesamiento de transacciones gestionado con **PayPal** y prevención de fraude integrada con **Forter**. Monitorización RUM ejecutada mediante **Datadog**.
* **Integraciones y Servicios SaaS (Vía Registros DNS TXT):**
  * **Gestión y documentación:** Atlassian (Jira/Confluence), Notion, Miro.
  * **Desarrollo e IA:** Verificaciones de dominio activas para OpenAI, Anthropic y Cursor IDE.
  * **Analítica y gestión de datos:** Mixpanel y Docusign.
* **Servicios Expuestos (Shodan / InternetDB):** La consulta pasiva no muestra servicios administrativos (SSH, RDP, bases de datos) directamente expuestos a Internet. La superficie pública está filtrada por la CDN de Fastly, permitiendo acceso únicamente a los puertos web estándar **80 (HTTP)** y **443 (HTTPS)**.

## 4. Correos y personas

* **Patrón de Correo Corporativo:** La estructura identificada corresponde a `nombre.apellido@kiwi.com` / `alias@kiwi.com`.
* **Infraestructura de Correo:** La política SPF del dominio delega la autorización de envío en un subdominio intermedio (`v=spf1 include:tmp-spf.kiwi.com ~all`). La gestión de envíos transaccionales y boletines se apoya en servicios externos como **Mailgun** (`mailgun.surveys-mg.kiwi.com`).
* **Fugas de Información y PII:** Las búsquedas pasivas con *theHarvester* no arrojaron listados públicos de direcciones de correo ni credenciales filtradas directamente asociadas a empleados en los índices generales.

## 5. Puntos de interés para la fase activa

1. **Entornos de desarrollo y staging (`staging-tequila-fe.kiwi.com`, `dev.parking.kiwi.com`):**
   * *Justificación:* Los entornos no productivos suelen presentar versiones menos restrictivas del marco de seguridad, modos de depuración (*debug*) activados o mensajes de error detallados (*stack traces*) que revelan la estructura interna de la aplicación.
2. **Endpoints de API y GraphQL (`api.tequila.kiwi.com`, `graphql.kiwi.com`):**
   * *Justificación:* Las interfaces de API son prioritarias para auditar la lógica de control de acceso (IDOR/BOLA). En el caso de GraphQL, se debe verificar si la consulta de introspección (*Introspection Query*) está habilitada en producción.
3. **Rutas sensibles descubiertas en `robots.txt` (`/logstash`, `/invoices`, `/manage`):**
   * *Justificación:* La exclusión explícita de estas rutas en los motores de búsqueda sugiere la presencia de paneles de gestión o endpoints de datos financieros que requieren verificación activa de autenticación y autorización.