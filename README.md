# Validador de Sitemap XML y Estructura de Protocolo

[![Validador Sitemap](https://img.shields.io/badge/TAVARDT-Sitemap%20XML-5b3cf5.svg)](https://tools.tavardt.com/mx/validador-sitemap-xml/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

El **TAVARDT Validador de Sitemap XML** proporciona inspección automatizada de sintaxis, validación de esquemas de protocolo, control de volumen de URLs y detección de contenido mixto para sitios web en México.

***

## Arquitectura del Protocolo y Matriz Diagnóstica

Los motores de búsqueda emplean sitemaps XML estructurados para descubrir contenidos y programar sus visitas. Errores de sintaxis, ficheros sobredimensionados o enlaces HTTP inseguros consumen presupuesto de rastreo y retrasan la indexación orgánica.

Esta herramienta analiza la integridad XML, valida esquemas urlset y sitemapindex, supervisa el límite de 50.000 URLs y detecta enlaces no seguros desde una base de 100 puntos sin librerías externas.

El motor de análisis evalúa los sitemaps según las directrices de Sitemaps.org y los estándares de rastreo e indexación:

<table>
  <thead>
    <tr>
      <th>Comprobación de Protocolo</th><th>Criterio de Validación</th><th>Deducción</th><th>Impacto en Rastreo y SEO</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Integridad de Sintaxis XML</strong></td><td>Parsing completo mediante ElementTree. Detecta caracteres reservados (&amp;) no escapados, etiquetas abiertas y errores de codificación.</td><td>Puntuación reseteada a 0</td><td>Fallo crítico; los rastreadores de búsqueda rechazan el documento íntegramente.</td>
    </tr>
    <tr>
      <td><strong>Validación del Esquema Raíz</strong></td><td>Exige conformidad con el estándar oficial: la etiqueta raíz debe ser <code>&lt;urlset&gt;</code> o <code>&lt;sitemapindex&gt;</code>.</td><td>-40 pts</td><td>Estructura no reconocida que impide la lectura de los enlaces incluidos.</td>
    </tr>
    <tr>
      <td><strong>Control de Límite de Entradas</strong></td><td>Supervisa el umbral de 50.000 elementos. Penaliza sitemaps vacíos (-30 pts) y ficheros sobredimensionados (&gt;50.000 URLs, -20 pts).</td><td>Hasta -30 pts</td><td>Rastreo incompleto, saturación de memoria del bot o envío de sitemaps inocuos.</td>
    </tr>
    <tr>
      <td><strong>Enlaces HTTP Inseguros</strong></td><td>Localiza enlaces <code>http://</code> declarados en sitemaps de sitios web configurados bajo protocolo seguro HTTPS.</td><td>-15 pts</td><td>Desperdicio de presupuesto de rastreo en redirecciones forzadas.</td>
    </tr>
    <tr>
      <td><strong>Disponibilidad de Red</strong></td><td>Verifica código de respuesta HTTP 200 y latencia durante la negociación TLS.</td><td>Puntuación reseteada a 0</td><td>Host inaccesible impidiendo la extracción automatizada del archivo XML.</td>
    </tr>
  </tbody>
</table>

### Escala de Calidad y Niveles de Estado

La herramienta determina un índice consolidado de calidad clasificando el estado del fichero XML:

* <strong>85 a 100 (OPTIMAL)</strong>: Conformidad plena; sintaxis XML impecable, enlaces seguros HTTPS y volumen de entradas reglamentario.
* <strong>65 a 84 (WARNING)</strong>: Fichero funcional que presenta alertas menores de protocolo mixto o advertencias de volumen.
* <strong>0 a 64 (CRITICAL)</strong>: Defectos sintácticos graves, esquemas inválidos o fichero vacío que exigen corrección inmediata.

***

## Instalación y Ejecución

Construido íntegramente con la librería estándar de Python 3.8+ sin dependencias externas.

```bash
git clone https://github.com/TAVARDT-Mexico/xml-sitemap-validator-mx.git
cd xml-sitemap-validator-mx
```

### Ejecución Estándar CLI

```bash
python sitemap_validator.py https://ejemplo.mx/sitemap.xml
```

### Salida Estructurada para Pipelines en JSON

```bash
python sitemap_validator.py https://ejemplo.mx/sitemap.xml -j
```

### Configuración de Timeout Personalizado

```bash
python sitemap_validator.py https://ejemplo.mx/sitemap.xml -j -t 15
```

***

## Ciberseguridad e Integridad Web en México

El control de calidad en sitemaps y el uso exclusivo de URLs seguras apoya las buenas prácticas de ciberseguridad en México. Eliminar enlaces no cifrados protege a los usuarios y asegura una presencia digital robusta.

Se sugiere incorporar revisiones automatizadas de sitemaps en los flujos continuos de desarrollo para mantener estándares óptimos de visibilidad.

***

## Preguntas Frecuentes Técnicas

### ¿Cuál es el límite máximo de entradas permitido por fichero de sitemap?

El estándar de Sitemaps.org limita cada sitemap a un máximo de 50.000 URLs y 50MB sin comprimir. Ficheros que superan las 50.000 entradas sufren una penalización de 20 puntos y deben dividirse mediante un índice de sitemaps.

### ¿Por qué se penalizan los enlaces HTTP inseguros?

Incluir enlaces HTTP en un sitemap de un sitio que opera bajo HTTPS confunde a los motores de búsqueda, agota el presupuesto de rastreo en redirecciones y debilita la seguridad de transporte. Se deducen 15 puntos al hallar enlaces HTTP.

### ¿Cómo distingue el validador entre sitemapindex y urlset?

El analizador examina el elemento XML raíz, diferenciando entre <code>&lt;sitemapindex&gt;</code> para índices secundarios y <code>&lt;urlset&gt;</code> para documentos finales. Cualquier etiqueta raíz no reconocida sufre una penalización de 40 puntos.

### ¿Qué sucede ante un fallo de sintaxis en el archivo XML?

La presencia de caracteres (&amp;) sin escapar o etiquetas mal cerradas impide que los motores procesen el archivo. El analizador resetea la puntuación a 0 y clasifica el estado como CRITICAL.

### ¿Qué indican los niveles de puntuación y estados de conformidad?

Puntuaciones entre 85 y 100 reflejan conformidad OPTIMAL. Entre 65 y 84 puntos se clasifica como WARNING, indicando mejoras recomendadas, y por debajo de 65 puntos el estado es CRITICAL, requiriendo acción urgente.

***

## Soporte Técnico y Consultoría Especializada

Para soporte prioritario en optimización de sitemaps, SEO técnico y ciberseguridad web, contacte a **TAVARDT**.

***

## Enlaces Útiles

* **Portal Corporativo:** https://ag.tavardt.com/mx/
* **Suite de Diagnósticos:** https://tools.tavardt.com/mx/
* **Contacto Técnico:** https://ag.tavardt.com/mx/contacto/

***

### Licencia
Distribuido bajo la Licencia MIT.

***

© 2026 TAVARDT. Todos los derechos reservados.
