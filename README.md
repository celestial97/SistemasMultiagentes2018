# Sistemas Multiagentes 2018
Proyecto de clase de Sistemas Multiagentes impartido en la ESIIAB

-----

# Partes diferenciadas y equipo que las realiza
+ Monitor _G6_: 
  + Oscar Rodríguez
  + Guillermo Fernández
  + Luis González
+ Servidor PHP (Tienda) _G5_:
  + Bernardo
  + Anselmo
  + Mercedes
+ Servidor Java (Tienda):
  + Óscar Gómez Monedero
  + Jose Antonio Serrano Esparcia
  + Mónica Sánchez Ruiz
+ Cliente Python (Consumidor):
  + ...
+ ...

-----

# Mensajes Necesarios
+ Monitor - Tienda: 
  + Inicialización
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionTienda.xml
  + Cierre de tienda
      + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploEvento.xml
+ Monitor - Consumidor: 
  + Inicialización
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionCliente.xml
  + Compra de producto
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G5/comprar.xml
  + Fin de compra 
    + Estructura: ...
    + Equipos involucrados: ...
  + ...
+ Consumidor - Tienda: 
  + Compra de producto
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G5/comprar.xml
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
