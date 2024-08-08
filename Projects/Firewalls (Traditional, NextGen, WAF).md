### INDEX

- [Configuraciones iniciales](#configuraciones-iniciales)
    - [Enable ssh](#enable-ssh)
    - [Add user](#add-user)
    - [Disable IPv6](#disable-ipv6)
    - [Personalizar dashboard]()

- [Firewall](#firewall)
    - [Firewall rules](#firewall-rules)
    - [Firewall logs](#firewall-logs)
    - [Firewall Aliases](#firewall-aliases)
    - [Firewall ICMP](#firewall-icmp)

- [OpenVPN pfsense](#openvpn-pfsense)
    - [Configuracion de certificados](#configuracion-de-certificados)
        -[Importar certificado](#importar-certificado)
        -[Crear certificado interno]()
    - [Configuración de OpenVPN](#configuración-de-openvpn)
    - [Copia de seguridad y restauración](#copia-de-seguridad-y-restauración)
    - [Configuracion DNS](#configuracion-dns)
    - [Configuracion de reglas firewall](#configuracion-de-reglas-firewall)


### Configuraciones iniciales

#### Enable ssh

~~~bash
System / Advanced / Admin Access > Secure Shell > Secure Shell Server : Enable Secure Shell
~~~

#### Add user

~~~bash
System/User Manager/Users > Add
~~~

#### Disable IPv6

~~~bash
- System/Advanced/Networking>IPv6 Options>Allow IPv6 : uncheck
- Services/DHCPv6 Server >DHCPv6 Options>DHCPv6 Server>Enable DHCPv6 server on interface : uncheck
- Interfaces/WAN>General Configuration>IPv6 Configuration Type : Select none
- Delete or disable some rules firewall IPv6 
~~~

#### Personalizar dashboard

~~~ bash
Status/Dashboard> Select + > select option
System/General Setup> webConfigurator> theme:select theme > reload for apply changes

# Record the source, destination, protocol, ports and state the connection 
Diagnostics> States
~~~

### FIREWALL

#### Firewall rules

+ Firewall / Rules / Lan
+ El orden las reglas es importante, la primera regla sobreescribe a las reglas anteriores

[+] Bloqueo ssh

+ Interfaz LAN bloqueo puerto ssh hacia interfaz CYBER_RANGE

![img](../resources/firewall1.png)


#### Firewall logs

+ Presionamos en filter 
~~~bash
Status/System Logs/Firewall/Normal View
~~~

#### Firewall Aliases

+ Agrupar algunas reglas en una sola (ip/port/url), en este caso agrupamos por puertos

~~~bash
Firewall/Aliases/Ports
~~~

![img](../resources/firewall2.png)

#### Firewall ICMP

+ En las opciones de ICMP subtypes seleccionar estos :
~~~
Echo request
Parameter problem (invalid IP header)
Time exceeded
Destination unreachable
~~~

![img](../resources/firewall3.png)

![img](../resources/firewall4.png)


### OpenVPN pfsense

#### Configuracion de certificados

##### Importar certificado

+ Configuracion de CAS

[+] System > Certificate > Authorities > + Add
[+] Tener certificados CAs disponibles, puedes descargar [aqui](https://www.perfect-privacy.com/downloads/openvpn/get?system=pfsense)
[+] Abre cualquier archivo terminado en *.conffiles desde el recurso comprimido descargado, copiar el contenido dentro de las etiquetas <ca></ca>

![img](../resources/firewall5.png)

+ Configuracion de Certificado

[+] System > Certificate > Certificates > + Add
[+] En el campo "Certificate Data" copiar el contenido de la etiqueta <cert></cert>
[+] En el campo "Private Key data" copiar el contenido etiqueta <key></key>

![img](../resources/firewall6.png)

#### Configuración de OpenVPN

[+]VPN > OpenVPN > Clients

[+] General y mode informatiom

![img](../resources/firewall7.png)

[+] Endpoint configuration

![img](../resources/firewall8.png)

[+] User authentication settings

![img](../resources/firewall9.png)

[+] Cryptographic settings

![img](../resources/firewall10.png)
![img](../resources/firewall11.png)

[+] Tunnel settings

![img](../resources/firewall12.png)

[+] Ping settings

![img](../resources/firewall13.png)

[+] Advanced configuration

+ Copiar esto en el campo "Custom options"
~~~
hand-window 120
mute-replay-warnings
persist-remote-ip
reneg-sec 3600
resolv-retry 60
tls-cipher TLS_CHACHA20_POLY1305_SHA256:TLS-DHE-RSA-WITH-AES-256-GCM-SHA384:TLS-DHE-RSA-WITH-AES-256-CBC-SHA:TLS-DHE-RSA-WITH-AES-128-GCM-SHA256:TLS-DHE-RSA-WITH-AES-128-CBC-SHA:TLS_AES_256_GCM_SHA384:TLS-RSA-WITH-AES-256-CBC-SHA
tls-timeout 5
tun-mtu 1500
fragment 1300
mssfix
remote-cert-tls server
~~~

![img](../resources/firewall14.png)

#### Copia de seguridad y restauración

[+] Diagnostic > Backup & Restore > Backup & Restore

+ Presionamos el boton "Download configuration as XSML" para tener una copia 

![img](../resources/firewall15.png)

#### Configuracion DNS

[+] System > General Setup

![img](../resources/firewall16.png)

[+] Services > DNS resolver > General Settings

![img](../resources/firewall17.png)

+ DNSSEC: Enable DNSSEC Support

![img](../resources/firewall18.png)

#### Configuracion de reglas firewall

[+] Firewall > Rules > LAN

+ El trafico unicamente pasar por el "gateway VPN_PP_AMSTERDAM1_VPNV4"

![img](../resources/firewall19.png)

[+] Firewall > Rules > Floating

+ Bloquear trafico en caso VPN esta offline

![img](../resources/firewall20.png)

~~~
    Action: Block
    Interface: WAN
    Direction: all
    Address Family: IPv4+IPv6
    Protocol: all
    Source: all
    Destination: all
    Marked/Tagged: NO_WAN_EGRESS
~~~

[+] Firewall > Nat > Outbound

![img](../resources/firewall21.png)

[+] Revisar la conexion si activo la VPN



https://www.youtube.com/watch?v=PBLFYvUIU54&t=2166s

LAN address :  Allows or blocks traffic specifically from the pfSense firewall itself (for example, if pfSense is running a service like DNS or a web server that should be accessible only from the LAN)
LAN subnets : Applies to all devices within the LAN network


COURSE : https://www.youtube.com/watch?v=wv1qTYR3faQ


DNS Resolver (Resolutor DNS)

    Función: Es un servidor DNS que tiene la capacidad de buscar de forma recursiva la dirección IP correspondiente a un nombre de dominio.
    Proceso: Cuando recibe una solicitud de resolución, el resolver busca la respuesta en su propia caché. Si no la encuentra, consulta a otros servidores DNS hasta que obtiene una respuesta o agota todas las opciones.
    Ejemplo: Cuando ingresas "www.google.com" en tu navegador, este envía una solicitud al resolver DNS de tu red, el cual se encarga de encontrar la dirección IP correspondiente a ese nombre de dominio.

DNS Forwarder (Reenviador DNS)

    Función: Es un servidor DNS que simplemente reenvía las solicitudes de resolución a otros servidores DNS configurados.
    Proceso: Cuando recibe una solicitud, en lugar de buscar la respuesta por sí mismo, la reenvía a un servidor DNS específico o a un grupo de servidores.
    Ejemplo: Si tienes una red interna con un servidor DNS configurado como forwarder, todas las solicitudes de resolución de nombres de dominio se enviarán a un servidor DNS externo, como los de tu ISP.

¿Cuál es la diferencia clave?

    Autonomía: El resolver DNS es más autónomo, ya que puede buscar la respuesta por sí mismo. El forwarder, por otro lado, depende de otros servidores para obtener la información.
    Complejidad: La configuración de un resolver DNS suele ser más compleja, ya que implica configurar zonas DNS, registros y mecanismos de caché. Un forwarder, en cambio, es más sencillo de configurar, ya que solo requiere especificar los servidores DNS a los que se reenviarán las solicitudes.
    Control: Un resolver DNS te brinda mayor control sobre el proceso de resolución de nombres, ya que puedes personalizar la configuración para adaptarla a tus necesidades específicas. Un forwarder, en cambio, ofrece menos flexibilidad.

¿Cuándo utilizar cada uno?

    DNS Resolver:
        Redes grandes y complejas con múltiples zonas DNS.
        Cuando se requiere un alto nivel de control sobre el proceso de resolución de nombres.
        Para implementar soluciones de DNS más avanzadas, como DNSSEC.
    DNS Forwarder:
        Redes pequeñas y medianas donde se desea simplificar la configuración.
        Cuando se confía en los servidores DNS de un proveedor de servicios de Internet.
        Para evitar duplicar la información de las zonas DNS.