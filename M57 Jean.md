# Escenario M57 Jean

## Descripción del caso

Este caso se basa en un escenario de análisis forense digital centrado en la posible **filtración de información confidencial** desde el portátil de una ejecutiva de la empresa ficticia **M57.Biz**.

### Contexto
Una hoja de cálculo que contiene los **nombres y salarios de empleados clave** de la empresa apareció publicada en la sección de comentarios del sitio web de un competidor.  
Este documento, según los registros, **solo existía en el portátil de Jean**, una de las ejecutivas de M57.

### Objetivo
Has recibido una **imagen forense del disco** del portátil de Jean. Tu trabajo consiste en:

- Determinar **cómo se produjo la filtración**
- Establecer si Jean **dice la verdad o está implicada**

# Solución:


##### Primero confirmamos el excel el cual fue filtrado

![](ANEXOS/Pasted%20image%2020250601234359.png)

![](ANEXOS/Pasted%20image%2020250601235314.png)

##### Para solucionar este caso deberemos buscar donde se almacenan los correos almacenados en outlook en este caso son archivos .pst



![](ANEXOS/Pasted%20image%2020250601234230.png)

##### Una vez visualizada la información almacenada en el archivo .pst podemos confirmar que Jean no mentía y podemos afirmar que Alison recibió el excel y fue el quien lo filtro.

![](ANEXOS/Pasted%20image%2020250601235900.png)



