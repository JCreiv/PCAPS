# Universidad Estatal de Nitroba 

## Contexto del incidente

- **Víctima:** Profesora
- **Situación:** Ha recibido correos electrónicos de acoso dirigidos a ella
- **Sospecha:** Cree que el remitente podría ser un alumno/a de la universidad
- **Alumnos:**
	- Amy Smith
	- Burt Greedom
	- Tuck Gorge
	- Ava Book
	- Johnny Coach
	- Jeremy Ledvkin
	- Nancy Colburne
	- Tamara Perkins
	- Esther Pringle
	- Asar Misrad
	- Jenny Kant

---

## Evidencia inicial

- El Departamento de IT solicita a la profesora los **encabezados completos (headers)** del correo electrónico.
- Tras recibir los headers, se detecta la **IP de origen** desde la cual fue enviado el mensaje 140.247.62.34. 
- La IP corresponde a una **habitación de estudiantes del campus universitario**.

---

## Información de la habitación implicada

- La habitación es compartida por tres alumnas:
  - Alice
  - Barbara
  - Candice

- Características de red:
  - Cada habitación cuenta con conexión **Ethernet**
  - **No se ofrece Wi-Fi oficial** por parte de la universidad
  - El novio de Barbara, **Kenny**, instaló un **router Wi-Fi sin contraseña**

## Problemas a resolver

1. **Mapear la red del dormitorio de Nitroba**  

#### Filtramos por la ip obtenida previamente

![](ANEXOS/Pasted%20image%2020250601214027.png)

### IP pública
- 140.247.62.34  
  Dirección IP pública desde la que se envió el correo acosador.  
  Está asignada a la habitación del dormitorio investigada.

### Red interna
- Red local: 192.168.15.0/24
- Puerta de enlace: 192.168.15.1  
  Es la dirección del router Wi-Fi instalado en la habitación.

- IP frecuente: 192.168.15.4  
  Esta dirección aparece con actividad constante en el archivo .pcap.  
  Es una posible candidata para ser el dispositivo utilizado en el ataque.


2. **Encontrar quién envió el correo a lilytuckrige@yahoo.com**  
3. **Buscar información que pueda enlazar el mensaje a un navegador y sistema operativo.

![](ANEXOS/Pasted%20image%2020250601215325.png)

Usando el filtro `frame contains "lilytuckrige"` en el análisis del archivo `.pcap`, se identificó uno de los mensajes enviados a la profesora.  
Este filtro permitió localizar el flujo HTTP que contiene el contenido del correo ofensivo dirigido a `lilytuckrige@yahoo.com`.


![](ANEXOS/Pasted%20image%2020250601220313.png)

Dentro del mensaje identificado, se observa la cabecera `User-Agent`, la cual indica que el navegador utilizado fue **Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)**.  
Esto sugiere que el atacante utilizó **Internet Explorer 6** sobre un sistema operativo **Windows XP o similar**.

Además, se puede ver que la dirección **MAC de destino** en la comunicación es `00:1d:d9:2e:4f:60`, correspondiente a un dispositivo de **Apple (Mac)**.  
Esto indica que el atacante utilizó un sistema Windows dentro de un Mac.


![](ANEXOS/Pasted%20image%2020250601221045.png)

Usando el filtro `frame contains "mail" and ip.src == 192.168.15.4` sobre el archivo de captura, se identificó un paquete con cabeceras HTTP que incluyen cookies.

Dentro de estas cookies se observa que el usuario mantiene una sesión activa con la cuenta de correo **jcoach@gmail.com**.

Esto permite vincular la IP **192.168.15.4** directamente con esa identidad, lo que refuerza la evidencia de que el propietario de dicha cuenta es el responsable del envío del mensaje ofensivo.

El propietario de esta cuenta en este caso seria ``Johnny Coach`` y el culpable de los mensajes.





  

