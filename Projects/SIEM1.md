### INDEX

- [Creacion de consultas y extracción de datos](#creacion-de-consultas-y-extracción-de-datos)

#### Creacion de consultas y extracción de datos

[+] Consultar logs de ssh, validar intentos de login

+ Query splunk
~~~bash
source="tcp:2211" index="ssh-logs" src_ip="*.*.*.*" accepted=* | stats count by src_ip,accepted | sort -count
~~~

![img](../resources/splunk1.png)

[+] Comparar direcciones ip con una lista negra

+ Query splunk
~~~bash
source="tcp:2211" index="ssh-logs" src_ip=* accepted=*
| lookup ip_blacks ip_blacks AS src_ip OUTPUT ip_blacks AS blacklisted
| where isnotnull(blacklisted) | eval datetime=strftime(_time, "%d/%m/%Y") | stats count by datetime, src_ip, accepted
~~~

![img](../resources/splunk2.png)

[+] Mostrar la distribución de códigos de estado HTTP

+ Query splunk
~~~bash
source="tcp:2211" index="ssh-logs" ip_req=* method=* resource=* status_code=*
| stats count by method, status_code
| eventstats sum(count) as total
| eval percentage=round((count/total)*100, 2)
| eval method=method . " - " . status_code
| fields method, status_code, count, percentage
| table method, status_code, count, percentage
~~~

![img](../resources/splunk3.png)



1.	Implementación Básica de Splunk:
    o	Instalación y Configuración: Instala Splunk en un entorno de prueba y realiza la configuración inicial.
    o	Indexación de Datos: Configura y agrega fuentes de datos como archivos de registro (logs), datos de red, y eventos del sistema.
2.	Creación de Dashboards:
    o	Dashboards Personalizados: Diseña dashboards que muestren información clave sobre la seguridad, como actividad sospechosa, tendencias de eventos y análisis de amenazas.
    o	Paneles Interactivos: Crea paneles que permitan a los usuarios interactuar con los datos y ver información en tiempo real.
3.	Desarrollo de Alertas y Correlaciones:
    o	Análisis y Consultas: Search Language - Practica el uso del lenguaje de búsqueda de Splunk (SPL) para crear consultas y extraer información útil de los datos.
    o	Reglas de Alerta: Configura alertas para eventos específicos como intentos de inicio de sesión fallidos, actividad inusual en la red, o cambios en los archivos críticos.
    o	Correlación de Eventos: Usa Splunk para correlacionar eventos de diferentes fuentes para detectar patrones que puedan indicar un incidente de seguridad.
4.	Investigación y Análisis de Incidentes:
    o	Simulación de Incidentes: Genera datos simulados que imiten un incidente de seguridad, como un ataque de malware o una intrusión en la red.
    o	Análisis Forense: Utiliza Splunk para investigar y analizar los datos generados durante el incidente y documenta tus hallazgos.
5.	Optimización y Gestión del Rendimiento:
    o	Optimización de Consultas: Mejora el rendimiento de las búsquedas y consultas en Splunk, optimizando las consultas para tiempos de respuesta más rápidos.
    o	Manejo de Recursos: Administra los recursos de Splunk para asegurar que el sistema esté funcionando de manera eficiente.
6.	Integración con Otras Herramientas:
    o	Integración con Threat Intelligence: Conecta Splunk con fuentes de inteligencia de amenazas para enriquecer los datos de seguridad.
    o	Integración con otras soluciones de seguridad: Configura Splunk para trabajar con otras herramientas de seguridad como sistemas de prevención de intrusiones (IPS), antivirus, o soluciones de firewall.
7.	Documentación y Reportes:
    o	Informes y Documentación: Crea informes sobre las actividades, incidentes y el rendimiento del sistema de seguridad. Documenta el proceso de configuración, las alertas configuradas y cualquier ajuste realizado.
8.	Proyectos de Investigación:
    o	Análisis de Nuevas Funcionalidades: Investiga y experimenta con nuevas funcionalidades de Splunk y cómo pueden ser utilizadas en un entorno de seguridad.
    o	Casos de Uso Reales: Investiga y documenta casos de uso reales en los que Splunk ha sido utilizado exitosamente para resolver problemas de seguridad.

    https://docs.splunk.com/Documentation/Splunk/latest/Data/WhatSplunkcanmonitor?_gl=1*4vmvd8*_gcl_au*ODYxMzIyMzIxLjE3MjI2MjkyNzI.*FPAU*ODYxMzIyMzIxLjE3MjI2MjkyNzI.*_ga*NjU3NDY1NjM0LjE3MjI2MjkyNzI.*_ga_5EPM2P39FV*MTcyMjYyOTI3Mi4xLjEuMTcyMjYzMDQxMC4wLjAuODE4NjQ3Njc1

Cómo Incluir Esto en Tu CV
1.	Experiencia de Proyectos:
    o	Descripción de Proyectos: Detalla los proyectos específicos que has realizado con Splunk, incluyendo las tareas que llevaste a cabo y los resultados obtenidos.
    o	Resultados y Logros: Destaca cualquier impacto positivo que hayas tenido, como la mejora en la detección de amenazas o la optimización del rendimiento del sistema.
2.	Habilidades y Competencias:
    o	Habilidades Técnicas: Enumera las habilidades específicas relacionadas con Splunk y la gestión de SIEM que has desarrollado.
    o	Certificaciones: Si has obtenido alguna certificación relacionada con Splunk o ciberseguridad, asegúrate de incluirla en tu CV.
3.	Documentación y Pruebas:
    o	Portafolio: Si es posible, incluye ejemplos de tu trabajo, como capturas de pantalla de dashboards, ejemplos de informes, o documentación técnica.
    o	Presentación de Resultados: Prepárate para hablar de tus proyectos en entrevistas, incluyendo la metodología que utilizaste y cómo resolviste problemas específicos.
