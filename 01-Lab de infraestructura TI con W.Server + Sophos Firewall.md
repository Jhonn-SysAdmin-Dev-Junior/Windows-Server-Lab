## 🌐 Arquitectura de Red del Laboratorio TI

La infraestructura que he implementado se compone de un servidor Windows Server 2019, un firewall virtualizado y varios clientes Windows, todos integrados en un dominio corporativo.



### 🔹 Componentes principales

## Firewall (10.10.10.1)

Interfaz WAN: salida a Internet mediante NAT.

<img src="imgs/sophoswan.png">

Interfaz LAN: red interna 10.10.10.0/24 (funciona como gateway predeterminada para toda la red)

<img src="imgs/sophoslan.png">

## Windows Server (10.10.10.2)

### Controlador de Dominio y DNS para gestión centralizada de usuarios y equipos.

Para la correcta configuración del DNS es necesario:<br>
1. instalar Active Directory Domain Services en el servidor.<br>

<img src="imgs/controlador de dominio.png">

2. Promover el servidor a controlador de dominio (en este caso AKEY.domain)<br>

<img src="imgs/dns2.png">

Una vez hecho esto, se debe unir el equipo cliente al dominio.

<div>
   <img src="imgs/cliente.png" height="400">
   <img src="imgs/cliente2.png" height="400">
</div><br>

 Y de esta manera podremos iniciar sesión en cualquier usuario que haya sido creado en el servidor usando la misma maquina o terminal. 

  # <img src="imgs/nany2.png">
    
  # <img src="imgs/nany.png">
   
  # <img src="imgs/edison.png">
   
  # <img src="imgs/edson2.png" width="500" height="500">
   
  # <img src="imgs/edison3.png">


Y tambien podemos comprobar que el servidor resuelve los nombres internos desde el equipo cliente con el comando nslookup + nombre del servidor.

# <img src="imgs/dns.png">

### DHCP:<br>
Asignación automática de IPs.<br>
#### Para configuar DHCP en nuestro servidor debemos:<br>
   1.Instalar el rol DCHP

   # <img src="imgs/dhcp1.png">

   2. Crear un ambito, en cual se especificará el rango de IPs que se quiere usar en este caso usare desde la 10.10.10.100 hasta la 10.10.10.200:

   # <img src="imgs/dhcp2.png">

   3. Autorizar el servidor para que provea servicio DHCP; de lo contrario no funcionará:<br>

   En este caso yo ya le he dado a autorizar.

   # <img src="imgs/dhcp3.png">

#### Prueba de asignación automatica de IPs desde una máquina cliente:<br>

Podemos ver que recibe la IP dentro del rango que se ha establecido 10.10.10.100-200 y en este caso ha recibido la IP 10.10.10.100

# <img src="imgs/dhcp.png">

### File Server:<br>
Almacenamiento centralizado de datos y archivos dentro de la red, permitiendo a los usuarios autorizados acceder, gestionar y compartir esa información de manera remota y eficiente.

<img src="imgs/compartida_servidor.png">

Y tambien se configuro una GPO para que al iniciar sesión en cada usuario, la unidad de red para el servicio de archivos compartidos seimpre este disponible.
<img src="imgs/COMPARTIDA_NANY.png">

---

##🔹 Flujo de comunicación

Los clientes reciben su configuración IP vía DHCP del Windows Server.
El gateway predeterminado (10.10.10.1) apunta al firewall, que se encarga de enrutar y aplicar políticas.
Las consultas de nombres se envían al DNS del Server (10.10.10.2), que resuelve nombres internos y reenvía las externas a Internet.
El firewall hace NAT y permite la salida a Internet de los clientes y del servidor.
Los usuarios acceden a recursos compartidos (ej: \\Servidor\Marketing) y a servicios del dominio.

