# Blue-Team

### PROYECTOS BLUE TEAM

#### Firewalls (Traditional, NextGen, WAF): 
To be a successful defender, I need to understand concepts around network segmentation, routing, trusted and untrusted zones. I need to understand the different layers of the OSI model and which security controls can mitigate attacks at which level- and more important which attacks a given control can NOT mitigate. As I examine alerts from these security controls, I need a decent understanding of how they operate so I can recommend and communicate to the managing teams which controls should be engaged to mitigate an attack.

1. Nivel de Experiencia:

    Principiante:
        Configuración básica de firewalls: Practica con diferentes tipos de firewalls (hardware, software, NGFW) configurando reglas simples para bloquear o permitir tráfico en base a puertos, direcciones IP y protocolos.
        Análisis de logs: Aprende a interpretar los logs de un firewall para identificar patrones de tráfico, posibles intrusiones y generar alertas.
        Simulaciones de ataques: Utiliza herramientas como Metasploit para simular ataques comunes y observa cómo responde tu firewall.
    Intermedio:
        Segmentación de redes: Diseña y implementa una arquitectura de red segmentada utilizando firewalls para aislar diferentes zonas de tu red (DMZ, red interna, etc.).
        Implementación de IDS/IPS: Integra un sistema de detección y prevención de intrusiones (IDS/IPS) con tu firewall para detectar amenazas más sofisticadas.
        Gestión de vulnerabilidades: Realiza escaneos de vulnerabilidades en tu red y configura reglas en el firewall para mitigar los riesgos identificados.
    Avanzado:
        Orquestación de la respuesta a incidentes: Automatiza la respuesta a incidentes utilizando herramientas de orquestación de seguridad y el firewall como un elemento clave.
        Análisis de amenazas: Realiza análisis de amenazas avanzados para identificar los riesgos más probables y diseñar estrategias de defensa proactivas.
        Implementación de Zero Trust: Diseña una arquitectura de seguridad basada en el principio de "confianza cero", utilizando firewalls para segmentar el tráfico y aplicar políticas de acceso granular.

2. Entorno:

    Laboratorio virtual: Utiliza plataformas como VirtualBox o VMware para crear un entorno de laboratorio seguro y flexible donde experimentar con diferentes configuraciones de firewall.
    Red doméstica: Implementa un firewall en tu red doméstica para proteger tus dispositivos personales.
    Red empresarial: Si tienes acceso a una red empresarial, puedes colaborar con el equipo de seguridad para implementar proyectos más complejos.

3. Herramientas:

    Firewalls: Explora diferentes opciones como pfSense, OPNsense, Cisco ASA, Fortigate, etc.
    IDS/IPS: Snort, Suricata, SIEM (Splunk, Elastic).
    Herramientas de gestión de configuración: Ansible, Puppet.
    Herramientas de orquestación de seguridad: SOAR (Security Orchestration, Automation and Response).

Ejemplos concretos de proyectos:

    Creación de un laboratorio de ciberseguridad: Configura un laboratorio virtual con diferentes sistemas operativos, aplicaciones y un firewall para simular un entorno empresarial.
    Implementación de un firewall en una pequeña empresa: Analiza la infraestructura de una pequeña empresa y diseña una política de seguridad basada en firewalls para proteger sus activos.
    Desarrollo de una solución de detección de intrusiones: Crea un sistema de detección de intrusiones basado en reglas personalizadas para identificar ataques específicos.
    Automatización de la respuesta a incidentes: Desarrolla un playbook para automatizar la respuesta a incidentes comunes, como la detección de malware o ataques de fuerza bruta.
    
#### Vulnerability management/patching: 
As a blue team defender, I am often the first to realize the consequence of an unpatched asset. I have often used vulnerability and patching data in conjunction with alert notifications to determine the probability a given attack was successful or not.
    
#### GRC/Policy development: 
Similar to vulnerability management, the shortcomings of insufficient policies are often first noticed by the blue team. Blue teams are a hidden goldmine of knowledge for policy writers and compliance teams if leveraged correctly. They can often tell you where policy is not being followed, where compliance regulations are being violated, and make recommendations for improvements to policies that would benefit the organization by reducing security incidents.

#### Application Security: 
After user error (e.g. Phishing), application security may be the second largest attack vector. To be fair, I am casting an exceedingly large and overarching net to include not just secure coding but the management of these systems. For the sake of space, I'll say a blue team member should have awareness of the OWASP top 10 vulnerabilities as he/she investigates attacks.
    
#### Data Loss Prevention (DLP)/Insider Threat: I'm somewhat artificially grouping these two together because there is considerable overlap. Not every attack originates external to the company. The most successful blue teamers retain the awareness that some activities could be performed by insiders. Some of the most significant security incidents I have been party to have been authorized individuals performing unauthorized activities.

#### Identity & Access Management: Unauthorized access still remains the primary threat vector for most companies- most often this is observed after a successful phishing attack. Blue team members need a conversational understanding of authentication mechanisms, trusts, 2FA & 2FA bypass, least privilege, groups and privilege inheritance, interactive logins & service account activity and more.

#### Filtering (DNS/Mail/Proxy): Phishing remains the absolute number one way attackers gain access to networks for the past several years. Understanding how attackers bypass spam filters, manipulate DNS and websites to conduct C&C activity is often some of the most investigated activity by incident investigators.

#### DoS/DDoS/CDN: Not as common as other attacks, attacks against the availability of systems remains threat vector blue teamers must maintain awareness of. Understanding the intricacies of UDP vs TCP attacks and amplification attacks is often outside the working knowledge maintained by many infosec specializations- but necessary for blue teamers. Understanding the role the content delivery networks play to mitigate these attacks and understanding when attackers are bypassing CDN networks is key to keeping business availability intact.

#### Threat Intelligence/Research: I suspect one thing that is held in common by any person who has ever been charged with incident response is investigating an attack you don't understand. The thing that separates the good from the great is the ability to take a potential security incident that is NOT understood well and make it understandable. This skill alone is sufficient justification why you want your infosec leaders to have blue team experience- but there is still more.

#### Incident Response: If security controls and people were perfect, incident response (the role of blue team) wouldn't be necessary at all. But security controls are often deficient and NO CONTROL is 100% effective and people still make mistakes. It's not a matter of if you have a cyber incident, just a matter of when. The experienced blue team is who you want at the helm of the ship when that day comes.

#### Resources

https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro
https://www.linkedin.com/pulse/why-you-want-blue-team-experience-from-your-next-hire-anthony-morris

#### PROYECTS IMPLEMENT

+ SPLUNK implementing a SIEM https://blog.davidvarghese.dev/posts/building-home-lab-part-1/
