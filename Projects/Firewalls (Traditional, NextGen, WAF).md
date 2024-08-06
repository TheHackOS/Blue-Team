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