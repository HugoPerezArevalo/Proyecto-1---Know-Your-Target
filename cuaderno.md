# Cuaderno de Trabajo - Proyecto 1
28/10/2026 12:03 - objetivo: kiwi.com (en scope)
    $ dig kiwi.com MX
    -> Hay 5 servidores de correo apuntando a :
    - alt4.aspmx.l.google.com.
    - alt3.aspmx.l.google.com.
    - alt2.aspmx.l.google.com.
    - aspmx.l.google.com.

    30/10/2026 15:30 · objetivo: kiwi.com (en scope)
    $ dig +short txt kiwi.com
    -> El registro SPF apunta a un subdominio específico (include:tmp-spf.kiwi.com).
    -> Las verificaciones de dominio revelan el uso extensivo de herramientas de terceros: Atlassian (Jira/Confluence), Notion, Miro, Mixpanel, Docusign, Microsoft (MS), Mail.ru y herramientas de IA (OpenAI, Anthropic, Cursor).

30/10/2026 13:40 - objetivo: kiwi.com (en scope)
    $ subfinder -d kiwi.com -silent
    -> 223 subdominios encontrados. 
    -> Se identifican entornos de desarrollo, staging, paneles internos (Jira, Confluence) y APIs de proyectos paralelos (Tequila, Banana).

30/10/2026 13:45 - objetivo: kiwi.com (en scope)
    $ curl -s https://www.kiwi.com/robots.txt
    -> El archivo contiene múltiples reglas 'Disallow'. 
    -> Se ignoran las exclusiones de regionalización (/ag/, /es/, /de/, etc.) por ser de bajo valor.
    -> Rutas interesantes descubiertas (fuera del índice público): /api, /additional_action, /aggregation_flights, /invoices, /logstash, /payment, /manage, /account.
    -> Sitemaps identificados: sitemap.xml, stories/sitemap.xml, help/sitemap.xml.

30/10/2026 15:21 - Objetivo: kiwi.com (en scope)
    $ whois kiwi.com
    -> connect: Network is unreachable.

30/10/2026 16:00 - objetivo: kiwi.com (en scope)
    $ Análisis con extensión Wappalyzer en el dominio principal
    -> Stack principal identificado: React y Next.js (versión 16.4.2).
    -> Infraestructura y Rendimiento: CDN Fastly, Caché con Varnish (1.1) y soporte para HTTP/3.
    -> Herramientas adicionales: Datadog (Analítica/RUM), PayPal (Pagos) y seguridad web mediante Forter.

30/10/2026 16:30 - objetivo: kiwi.com (en scope)
    $ (https://sitereport.netcraft.com/?url=https://kiwi.com)
    -> Proveedor de Red / CDN: Fastly, Inc.
    -> IP principal: 151.101.195.42 (Rango 151.101.0.0-151.191.255.255).
    -> Registrar / DNS: Gestionado a través de Registrador, DNS en ns-cloud-c1.googledomains.com

10/30/2026 14:30 - objetivo: kiwi.com (en scope)
    $ theHarvester -d kiwi.com -b all
    -> Agregación OSINT completada.
    -> Resultados: 9 ASNs identificados (tráfico distribuido en CDN y proveedores Cloud), 82 direcciones IP resolviendo a capas de proxy/CDN, 248 hosts/subdominios correlacionados y 10 URLs de estructura interna.

30/10/2026 15:00 - objetivo: kiwi.com (en scope)
    $ Búsqueda pasiva mediante Google Dorks (ej. 'site:kiwi.com filetype:pdf', 'site:kiwi.com inurl:admin', 'site:kiwi.com "index of"')
    -> Sin hallazgos de interés. Los resultados corresponden a páginas públicas estándar; no se detectaron documentos sensibles, backups ni paneles de administración expuestos.


30/10/2026 15:30 - objetivo: kiwi.com (en scope)
    $ Consulta pasiva en Shodan / InternetDB (búsquedas por 'hostname:kiwi.com' y rangos de IP asociados)
    -> No se identifican servicios anómalos ni puertos de administración (ej. SSH 22, RDP 3389, Elastic 9200) expuestos directamente a Internet sin protección. La totalidad de las IPs responden únicamente en los puertos estándar HTTP/HTTPS (80/443).