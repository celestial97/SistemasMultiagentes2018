# Sistemas Multiagentes 2018
Proyecto de clase de Sistemas Multiagentes impartido en la ESIIAB

-----

# Partes diferenciadas y equipo que las realiza
+ Monitor: 
  + Oscar Rodríguez
  + Guillermo Fernández
  + Luis González
+ Servidor PHP (Tienda):
  + Bernardo
  + Anselmo
  + Mercedes
+ Servidor Java (Tienda):
  + ...
+ Cliente Python (Consumidor):
  + ...
+ ...

-----

# Mensajes Necesarios
+ Monitor - Tienda: 
  + Inicialización
    + Estructura: ...
    + Equipos involucrados: ...
  + Cierre de tienda
      + Estructura: ...
      + Equipos involucrados: ...
  + ...
+ Monitor - Consumidor: 
  + Inicialización
    + Estructura: ...
    + Equipos involucrados: ...
  + Compra de producto
    + Estructura: ...
    + Equipos involucrados: ...
  + Fin de compra 
    + Estructura: ...
    + Equipos involucrados: ...
  + ...
+ Consumidor - Tienda: 
  + ...

------

# Propuesta de mensaje común XML
```XML
<mensaje>
  <emisor>
    <direccion>
      <ip>192.168.1.1</ip>
      <puerto>80</puerto>
    </direccion>
    <rol>tienda</rol>
  </emisor>
  <receptor>
    <direccion>
      <ip>192.168.1.2</ip>
      <puerto>80</puerto>
    </direccion>
    <rol>comprador</rol>
  </receptor>
  <tipo>venta</tipo>
  <cuerpo>
    ...
  </cuerpo>
</mensaje>
```
