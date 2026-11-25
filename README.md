# Validador de Sitemap XML e Indices de URLs

[![Validador Sitemap](https://img.shields.io/badge/TAVARDT-Sitemap%20XML-5b3cf5.svg)](https://tools.tavardt.com/mx/validador-sitemap-xml/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Auditoria de mapas de sitio XML para optimizar el rastreo de motores de busqueda y garantizar una indexacion precisa de contenidos.

Desarrollado y mantenido por el equipo de arquitectura y rastreo perimetral de **TAVARDT**.

***

## Capacidades de Validacion de Sitemaps XML

* **Cumplimiento de Protocolo Sitemaps.org**: Auditoria de estructuras `<urlset>` e indices de enlaces `<sitemapindex>`.
* **Inspeccion de Metadatos de Rastreo**: Validacion de sintaxis en fechas `<lastmod>` y consistencia de atributos opcionales.
* **Integridad de Protocolo Seguro**: Identificacion de URLs que no implementan HTTPS y caracteres especiales sin codificar.
* **Monitoreo de Limites de Carga**: Verificacion de directivas de capacidad maxima (50.000 URLs por mapa).
* **Indice de Calidad Estructural**: Calificacion integral de 0 a 100 para corregir bloqueos en la indexacion.

***

## Instalacion y Ejecucion

Requiere Python 3.8 o superior utilizando la biblioteca estandar.

```bash
git clone https://github.com/TAVARDT/xml-sitemap-validator-mx.git
cd xml-sitemap-validator-mx
python sitemap_validator.py https://ejemplo.mx/sitemap.xml
```

Para formato estructurado JSON:

```bash
python sitemap_validator.py https://ejemplo.mx/sitemap.xml -json
```

***

## Herramienta en Linea

Para validaciones recurrentes y pruebas de arquitectura web:

* **Validador de Sitemap XML Oficial**
* **[Portal Corporativo TAVARDT](https://ag.tavardt.com/mx/)**

***

## Consultoria en Rastreabilidad Web

Para proyectos de optimizacion de sitemaps a gran escala bajo Estandares Web y Buenas Practicas SEO, contacte a **TAVARDT**.

***

## Enlaces Útiles

* **Portal Corporativo:** https://ag.tavardt.com/mx/
* **Suite de Diagnósticos:** https://tools.tavardt.com/mx/
* **Contacto Técnico:** https://ag.tavardt.com/mx/contacto/

***

### Licencia
Distribuido bajo la Licencia MIT. Consulte el arquivo [LICENSE](LICENSE) para obtener más detalles.

***

© 2026 TAVARDT. Todos los derechos reservados.
