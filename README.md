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
+ Cliente JavaScript (Consumidor):
  + Pedro José Villena
  + Jaime Tolosa
+ ... 

-----

# Flujo de trabajo de una simulación

1. Todos los agentes se inicializan en sus máquinas respectivas. 
2. Los agentes Tienda y Consumidor le mandan una petición XML (plantilla) de conexión al Monitor
3. El Monitor responderá a la petición (plantilla) y los agentes Tienda y Consumidor se quedarán a la espera.
4. El Monitor enviará un mensaje de inicialización a los agentes Tienda ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionTienda.xml)) y Consumidor ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionCliente.xml)).
5. Los agentes Tienda y Consumidor le mandarán una respuesta (plantilla) de confirmación y quedarán a la espera. Aquellos clientes que no envíen una confirmación no entrarán en la simulación.
6. El Monitor enviará un mensaje de confirmación (plantilla) a los agentes Tienda y Consumidor, y quedarán a la espera. 
7. El Monitor enviará un mensaje de inicio de simulación a los agentes Tienda y Consumidor, que no tendrá que ser respondido, y los agentes Tienda y Consumidor iniciarán la simulación

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
