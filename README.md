# Parcial-1

# primer punto - conceptual
# a) Explicar la diferencia fundamental entre la latencia y el jitter. ¿Cuál de estas dos métricas tendría un impacto más negativo en una llamada VoIP y por qué?
Respuesta: 
Latencia: tiempo que tarde un paquete en llegar desde su origen hasta su destino - PC A - PC B
Jitter: Es la variación en tiempo (milisegundos) que tarda en llegar un paquete a su destino, dependiendo ciertos parametros y a su vez distancias de un punto A a un punto B. 
Ejemplo: si un paquete tarde menos de diez milisegundos es una conectividad buena. 
El que tendría un impacto mas negativo en una llamada VoIP seria el jitter, ya que esto causa que al momento de entregar el mensaje y tenga un alta tasa de milisegundos la voz del remitente se escucha robotica.

# b) Una aplicación envía datos usando protocolo TCP, mientras que otra usa UDP para la misma tarea de transmisión de video. ¿Cuál es más eficiente en términos de throughput y cuál ofrece mayor control de la pérdida de paquetes? Justifique su respuesta basándote en la "anatomía" de sus cabeceras.
Respuesta: En este caso el mas eficiente seria el protocolo TCP debido a que este al obtener una capa mas de seguridad a la hora de entregar los paquetes a su destino genera una menor perdida de paquetes, caso contrario del protocolo UDP que entrega los paquetes mas rápido pero con mayor perdida de paquetes. 

# C) Al ejecutar el comando “arp -a” en la CMD de Windows, se obtienen una lista de direcciones IP y direcciones físicas. ¿Qué protocolo de la suite TCP/IP llena esta tabla y cuál es su función principal dentro de una red local? Relacionar la respuesta con la estructura de una trama Ethernet.
Respuesta: El protocolo de la suite que llena esta tabla es el del ARP su funcion principal es traducir una dirección IP a una dirección MAC para evitar la repeticion de solicitudes de conectividad. 

<img width="1312" height="807" alt="image" src="https://github.com/user-attachments/assets/17e50fa2-c1c1-48f5-bd56-6fbd424783ef" />

# d) Mencionar dos diferencias clave entre las arquitecturas SNMPv2c y SNMPv3. Enfocarse en los aspectos de seguridad y el tipo de mensajes que manejan.
Respuesta: 
En temas de seguridad SNMPv3 es mas segura SNMPv2c, ya que cuenta con una autenticación como lo es SHA o MD5, con un cifrado bien sea AES o  DES 
También en temas de autenticación SNMPv2 cuenta con solamente la opción de texto plano para dicha autentica,para SNMPv3 utiliza un protocolo como lo es: HMAC, MD5 o GMAC-SHA, para un mayor seguridad para usuarios y contraseñas.

# e) Define qué es un OID y cuál es su relación con la MIB. Si un administrador quiere saber la cantidad de bytes que ha recibido una interfaz de red, ¿qué operación SNMP (Get, Set, Trap) debe utilizar y por qué no sería adecuado usar un Trap para esto?
Respuesta:
Un OID es un identificador unico unico que se encuentra alojado dentro de un MIB (Base de información general)
Al utilizar Get y Set el administrador tomara el rol de gestor en el MIB, el administrador no debe utilizar el Trap ya que dicha solicitud la utiliza el agente para solicitar si sucedio un reinicio de un equipo o una caida de un puerto. 

# PUNTO DOS 

Identificar y explicar cada uno de los campos de la cabecera Ethernet. ¿Qué significa el valor 0x0800 en el campo "Tipo"?
Respuesta:
El valor 0x800 es la asiganción que se le da al protoclo ipv4 en el encabezado del segmento de TCP
B. En el encabezado IPv4, ¿Que significa los campos protocolo y TTL? ¿porque es importante  el TTL en red?
Respuesra
