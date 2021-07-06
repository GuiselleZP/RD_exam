# Lista de comandos.
Comandos usados en los talleres.
* **ipconfig** : muestra los valores de configuración de red de TCP/IP actuales y actualiza la configuración del protocolo DHCP y el sistema de nombres de dominio.

* **ping** : utilidad de diagnóstico en redes de computadoras que comprueba el estado de la comunicación del anfitrión local con uno o varios equipos remotos de una red que ejecute ip.

* **ping -t dir_IP_destino** : *Ping infinito en bucle continuo.* Ping crea un registro en la salida estándar (stdout) para cada paquete de respuesta. Si has establecido otra configuración, la información se escribe en el terminal.
Este registro de salida incluye la dirección IP del ordenador que ha recibido el ping, el tamaño del paquete de respuesta en bytes, el tiempo de respuesta en milisegundos (ms) y el tiempo de vida (TTL, Time to Live).

* **tracert dir_ip_destino** : determina la ruta a un destino mediante el envío de paquetes de eco de Protocolo de mensajes de control de Internet (ICMP) al destino.
En estos paquetes, TRACERT usa valores de período de vida (TTL) IP variables. 
Dado que los enrutadores de la ruta deben disminuir el TTL del paquete como mínimo una unidad antes de reenviar 
el paquete, el TTL es, en realidad, un contador de saltos. Cuando el TTL de un paquete alcanza el valor cero (0), 
el enrutador devuelve al equipo de origen un mensaje ICMP de "Tiempo agotado".

---
*Router(config)#hostname RouterA /*cambia el nombre de un router*
*Router#show running-config /*Muestra Configuración del router*


## Realización de red; direccionamiento estatico y dinamico.

* Router>enable   / *Ingresa a modo privilegiado*
* Router# config term /*Ingresa a modo configuracion*
* Router(config)# interface FastEthernet 0/0/0    /*Configuración interfaz puerto **ethernet***
* Router(config-if)#ip add <ip red> <mask> /*Asignación IP*
* Router(config-if)#no shutdown /*Activación interfaz*
* Router(config-if)#^z
* Router#copy run start  /*Guarda cambios*

---

* Router(config)# interface FastEthernet 0/0/0    /*Configuración interfaz puerto **serial***
* Router(config-if)#ip add <ip red> <mask> /*Asignación IP*
* Router(config-if)#clockrate 64000 /*Tasa de transmisión* 

---
* RouterA#show ip interface brief /*Muestra el estado de cada interfaz*
* Router#show ip route    /*Muestra tabla de enrutamiento*

#### Enrutamiento estático
* Router(config)#ip route <dir ip red> <máscara de subred> <interfaz de salida | siguiente salto> 
  
#### Enrutamiento dinámico
* Router(config)#router rip
* Router(config-router)#network <dir ip red>
* Router(config_router)#ver 2
  
## ACL (Lista de control de acceso)
* Router(config-if)#ip access-group 1 {número de la lista| nombre de la lista} {in|out} /*creación estadar de una ACL*
... opciones
  * Router(config)#access-list {número de la lista| nombre de la lista} {permit|deny} host <dir ip>
  * Router(config)#access-list {número de la lista| nombre de la lista} {permit|deny} any
  * Router(config)#access-list {número de la lista| nombre de la lista} {permit|deny} <dir red>
  
