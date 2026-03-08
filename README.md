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
Análisis de Captura con Wireshark

# a) Identificar y explicar cada uno de los campos de la cabecera Ethernet. ¿Qué significa el valor 0x0800 en el campo "Tipo"?
Respuesta: Cuando habla del valor 0x0800 nos esta indicando que el paquete transportado en el interior de la trama es un paquete IPv4 sin ello la tarjeta de red no sabria a que entregarle los datos.

# b) En la cabecera IPv4, ¿qué significan los campos Protocolo y TTL? ¿Por qué es importante el TTL en red?
Respuesta: Los campos protocolo significa el tipo de protocolo de capa superior está contenido dentro del paquete IP.Es decir, le dice al sistema operativo qué debe hacer con los datos cuando el paquete llega al destino, en la imagen se oberva el valor 6 corresponde a TCP (Transmission Control Protocol), en resumen indica qué tipo de datos transporta el paquete (TCP, UDP, ICMP, etc.).
El TTL indica el número máximo de saltos que un paquete puede atravesar antes de ser descartado. (en este caso, 128) que disminuye en 1 cada vez que el paquete atraviesa un router.

# C) En la cabecera TCP, explicar la función de los flags ACK y PSH. ¿Qué indica el "Puerto Destino: 80" sobre el servicio al que se intenta acceder?
Respuesta: 
cuando aparece la funcion de ACK indica que recibio bien el paquete, que el campo de número de confirmación es válido.
Y al tener el PSH activo este informa al receptor que debe entregar los datos inmediatamente a la aplicación, sin esperar a llenar el buffer.
El puerto destino 80 indica que corresponde al servicio HTTP por lo que el paquete esta dirigido a un servidor web, pero se debe tener en cuenta que este puerto no es seguro como el 443 HTTPS.

# d) Si este mismo paquete se enviara usando IPv6, ¿qué cabecera de IPv6 reemplazaría a la cabecera IPv4 mostrada y cuál sería una mejora notable en su procesamiento por parte de los routers?

# PUNTO TRES 

<img width="584" height="364" alt="image" src="https://github.com/user-attachments/assets/17b2829b-783c-4874-841a-c1e1177af540" />

A.1 Explicar qué información proporciona este comando que daría un ”ping” o un “tracert”. 

RTA: PING: al realizar un se verficara la conectividad que se tiene un con destinatario (un PC, impresora, pagina web, servidor, swith,router,Lot, etc), asi mismo se puede evidencias, los TTL (time to live) que tiene el paquete que envio al destinario, cuantas perdidas de paquetes se obtuvo (en porcentaje) al momento de finalizar el ping, cabe resalta que el ping funciona gracias al protocolo ICMP. 

TRACERT: al momento de realizar un tracert a una dirección IP en especifica sabremos cuantos “salto” realizo nuestro paquete entre router que esta conectadas entre si, para poder llegar a su destino, adicionalmente podemos visualizar las direcciones IP de cada router por donde pasa nuestro paquete y así determinar si el paquete no llego al siguiente salto y que parte de la red fue inalcanzable la entrega del paquete. 

A.2 Describir el proceso que sigue “pathping” para obtener sus resultados. 

RTA: al digitar el comando pathping como se muestra en la imagen se puede obtener una mejior información que al realizar un tracert, ya que nos suministra cuantos saltos máximos puede viajar nuestra solicitud, nos reporta cuando nuestro paquete ya llego a su destino, que en este caso son los 8 de Google y por último nos muestra la estadística promedio en segundos cuanto tardo en llegar nuestro paquete desde su origen hasta su destino. 

B. Para monitorear un router de la oficina, decides usar SNMP. El router soporta SNMPv2c con la comunidad "public" de solo lectura. ¿Qué comando de Windows  

(o herramienta de línea de comandos) podría utilizar para "caminar" por el árbol MIB y obtener todos los valores de la interfaz del router en la IP 192.168.1.1?  

RTA: Para obtener los valores de la interfaz se utilizara el comando: Net-SNMP y el comando especifico para pode ver el camino por donde pasa el árbol MIB es snmpwalk.  

Un ejemplo para poder visualizar el cambio es como el siguiente comando: 

 

Cada sentencia del comando quiere dar a entender que: 

Snmpwlak: El comando para consultar una serie de variables de forma secuencial. 

-v 2c: es la versión del SNMP 

-c public: es  para definir la comunidad, para ver la contraseña 

192.168.1.1: la dirección IP del equipo router 

1.3.6.1.2.1.2: es el objeto en especifico que se apunta a la tabla de la interfaz 

Si el router envía un mensaje “authenticationFailure” trap al gestor SNMP, ¿Qué evento lo ha provocado y cuál es la ventaja de recibir un Trap en lugar de estar consultando constantemente (polling)el estado del router? 

RTA: Se genera cuando el agente SNMP del router recibe un mensaje (PDU) con un nombre de comunidad incorrecto, por ejemplo, si se llega a intenta usar admin o private en lugar de public . Esto generar  una alerta de seguridad que indica un posible acceso no autorizado o un error de configuración en un gestor SNMP. 

 

# PUNTO CUARTO

Paso 1: Verificación de conectividad y resolución de nombres 

Antes de ejecutar el git push, debemos asegurar que el camino hacia GitHub esté abierto. 

Conectividad IP: Se usaría el comando ping github.com. 

 <img width="581" height="202" alt="image" src="https://github.com/user-attachments/assets/5f27f67c-c0cb-4472-82a2-f238faf63c23" />


Capa OSI: Capa 3 (Red). 

Protocolo: ICMP (Internet Control Message Protocol). Verifica la 

 <img width="604" height="122" alt="image" src="https://github.com/user-attachments/assets/ba03ee5b-4fe2-4806-8fa8-c9dfe555f767" />


 alcanzabilidad de un host. 

Resolución de Nombres (DNS): El equipo obtiene la IP mediante el protocolo DNS (Domain Name System). 

Proceso: El cliente envía una consulta UDP al puerto 53 de un servidor DNS. 

Capa OSI: Capa 7 (Aplicación). 

Diagnóstico: Si falla, se usaría nslookup github.com o dig github.com. 

 <img width="383" height="156" alt="image" src="https://github.com/user-attachments/assets/1b85a831-61ba-451c-942e-2d5625a998ba" />


Teletráfico (Latencia y Jitter): Si el ping es exitoso pero variable, la métrica afectada es el Jitter (variación de la latencia). 

Impacto: Un jitter alto puede causar que los paquetes lleguen en desorden, obligando a TCP a reordenarlos, lo que disminuye el Throughput efectivo y hace que el git push se sienta "pesado" o lento. 

 

Paso 2: Establecimiento de la conexión para el Push 

Git suele utilizar HTTPS (puerto 443) para subir cambios. 

Protocolo de Transporte: Se utiliza TCP 

Three-way Handshake: 1. SYN: El cliente envía una solicitud de sincronización.  

2. SYN-ACK: El servidor responde confirmando y solicitando sincronización.  

3. ACK: El cliente confirma. Conexión establecida. 

Herramienta de Monitoreo: Se usaría Wireshark. 

Filtro: ip.addr == [IP_de_GitHub] && tcp.port == 443. 

 <img width="348" height="102" alt="image" src="https://github.com/user-attachments/assets/3e1a9546-948c-489a-b286-fec39d42fb69" />


Puertos y Capas: 

Puerto Origen: Un puerto aleatorio efímero (ej. 51234). 

Puerto Destino: 443 (HTTPS). 

Capa OSI: Capa 4 (Transporte) gestiona estos puertos. 

 

Paso 3: Encapsulamiento y enrutamiento de los datos 

Aquí es donde los archivos del commit se empaquetan para el viaje. 

Proceso de Encapsulamiento: 

Aplicación: Datos (Mensaje del commit + archivos). Unidad: Datos/Mensaje. 

Transporte: Se añade cabecera TCP. Unidad: Segmento. 

Red: Se añade cabecera IP (Origen/Destino). Unidad: Paquete. 

Enlace: Se añade cabecera Ethernet (MAC). Unidad: Trama. 

Física: Los bits viajan por el cable/aire. 

Congestión y Pérdida: Si un router descarta paquetes, el git push se ralentiza. TCP activaría el mecanismo de Retransmisión (Fast Retransmit) y el control de congestión (reduciendo la ventana de transmisión). 

Comando de diagnóstico: tracert github.com (Windows) para ver en qué salto ocurre la pérdida. 

Campo IP crítico: El TTL (Time To Live). Evita bucles infinitos; cada router resta 1 al valor; si llega a 0, el paquete se descarta. 

 

Paso 4: Confirmación y fin de la comunicación 

Confirmación: GitHub envía mensajes TCP ACK para confirmar la recepción de cada segmento. Si no llega un ACK, el cliente asume "pérdida de paquetes" y reenvía los datos. 

Cierre de Conexión: Se realiza mediante un Four-way Handshake: 

Cliente envía FIN. 

Servidor envía ACK. 

Servidor envía su propio FIN. 

Cliente envía ACK final. 

Gestión con SNMP: Como administrador, observaría en el router: 

ifOutOctets (Bytes transmitidos). 

ifOutDiscards (Paquetes descartados por congestión). 

Versión de SNMP: Usaría SNMPv3, ya que es la única versión que soporta cifrado y autenticación fuerte. 

