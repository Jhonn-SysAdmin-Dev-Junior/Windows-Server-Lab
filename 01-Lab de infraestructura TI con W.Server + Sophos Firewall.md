## 🌐 Arquitectura de Red del Laboratorio TI

La infraestructura que he implementado se compone de un servidor Windows Server 2019, un firewall virtualizado y varios clientes Windows, todos integrados en un dominio corporativo.



### 🔹 Componentes principales

## Firewall (10.10.10.1)

Interfaz WAN: salida a Internet mediante NAT.

<img src="imgs/sophoswan.png">

Interfaz LAN: red interna 10.10.10.0/24 (funciona como gateway predeterminada para toda la red)

<img src="imgs/sophoslan.png">

## Windows Server (10.10.10.2)

Controlador de Dominio (AD DS): gestión centralizada de usuarios y equipos.

<img src="imgs/controlador de dominio.png">

## DNS: 
Para la correcta configuración del DNS es necesario:<br>
1. instalar Active Directory Domain Services en el servidor.<br>
2. Promover el servidor a controlador de dominio (en este caso AKEY.domain)<br>

<img src="imgs/dns2.png">

Una vez hecho esto, se debe unir el equipo cliente al dominio.

<div>
   <img src="imgs/cliente.png" height="400">
   <img src="imgs/cliente2.png" height="400">
</div>

Y de esta manera podremos iniciar sesión en cualquier usuario que haya sido creado en el servidor usando la misma maquina o terminal. 

   <img src="imgs/nany2.png">
    
   <img src="imgs/nany.png">
   
   <img src="imgs/edison.png">
   
   <img src="imgs/edson2.png" width="400" height="400">
   
   <img src="imgs/edison3.png">


Y ahora podemos comprobar que el servidor resuelve los nombres internos desde el equipo cliente con el comando nslookup + nombre del servidor.

<img src="imgs/dns.png">

DHCP: asignación automática de IPs dentro del rango 10.10.10.100 – 10.10.10.200.

<img src="imgs/dhcp.png">

File Server: carpetas compartidas con permisos por departamento.

<img src="imgs/compartida_servidor.png">

<img src="imgs/COMPARTIDA_NANY.png">

Clientes Windows (10.10.10.101, 10.10.10.102, …)

<img src="imgs/sophoswan.png">

Se unen al dominio corporativo.

<img src="imgs/sophoswan.png">

Obtienen su configuración (IP, Gateway, DNS) desde el servidor DHCP.

<img src="imgs/sophoswan.png">

Acceden a recursos de red (carpetas compartidas, impresoras, políticas de grupo).

<img src="imgs/sophoswan.png">

Internet

Acceso disponible para todos los clientes a través del firewall.

---

##🔹 Flujo de comunicación

Los clientes reciben su configuración IP vía DHCP del Windows Server.
<img src="imgs/sophoswan.png">
El gateway predeterminado (10.10.10.1) apunta al firewall, que se encarga de enrutar y aplicar políticas.
<img src="imgs/sophoswan.png">
Las consultas de nombres se envían al DNS del Server (10.10.10.2), que resuelve nombres internos y reenvía las externas a Internet.
<img src="imgs/sophoswan.png">
El firewall hace NAT y permite la salida a Internet de los clientes y del servidor.
<img src="imgs/sophoswan.png">
Los usuarios acceden a recursos compartidos (ej: \\Servidor\Marketing) y a servicios del dominio.
<img src="imgs/sophoswan.png">
---

##🔹 Diagrama de Red
   

##✅ Estado actual del laboratorio

Dominio corporativo en funcionamiento.

DHCP y DNS configurados.

Clientes unidos al dominio.

Carpetas compartidas con permisos por UO.

Acceso a Internet desde los clientes mediante firewall.
