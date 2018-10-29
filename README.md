# Sistemas Multiagentes 2018

Proyecto de clase de Sistemas Multiagentes impartido en la ESIIAB

-----

## Tabla de contenidos


- [Tabla de contenidos](#tabla-de-contenidos)
- [Partes diferenciadas y equipo que las realiza](#partes-diferenciadas-y-equipo-que-las-realiza)
- [Flujo de trabajo de una simulación](#flujo-de-trabajo-de-una-simulación)
- [Mensajes necesarios](#mensajes-necesarios)
- [Propuesta de mensaje común XML](#propuesta-de-mensaje-común-xml)
- [FAQ](#faq)

-----

## Partes diferenciadas y equipo que las realiza

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

## Flujo de trabajo de una simulación

1. Todos los agentes se inicializan en sus máquinas respectivas.
2. Los agentes Tienda y Consumidor le mandan una petición XML ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploPeticionConexion.xml)) de conexión al Monitor
3. El Monitor responderá a la petición ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploACKInicio.xml)) y los agentes Tienda y Consumidor se quedarán a la espera.
4. El Monitor enviará un mensaje de inicialización a los agentes Tienda ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionTienda.xml)) y Consumidor ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionCliente.xml)).
5. Los agentes Tienda y Consumidor le mandarán una respuesta ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploACKAgenteIniciado.xml)) de confirmación y quedarán a la espera. Aquellos clientes que no envíen una confirmación no entrarán en la simulación.
6. El Monitor enviará un mensaje de inicio de simulación ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploGO.xml)) a los agentes Tienda y Consumidor, que no tendrá que ser respondido, y los agentes Tienda y Consumidor iniciarán la simulación

-----

## Mensajes necesarios

+ Monitor - Tienda:
  + Inicialización
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionTienda.xml
  + Cierre de tienda
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploEvento.xml
+ Monitor - Consumidor:
  + Inicialización
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionCliente.xml
  + Compra de producto
    + Estructura: ...
    + Equipos involucrados: ...
  + Fin de compra 
    + EstructuraG1: https://github.com/Kaysera/SistemasMultiagentes2018/tree/master/Grupos/G1
    + EstructuraG5: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G5/comprar.xml
    + Equipos involucrados: G1, G5
  + Fin de compra
    + Estructura: ...
    + Equipos involucrados: ...
  + ...
+ Consumidor - Tienda: 
  + Inicialización
    + Estructura: 
      + https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G3/Inicializaci%C3%B3n_Cliente_Tienda.xml
      + https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G3/Inicializaci%C3%B3n_Cliente_Tienda.xml
    + Equipos involucrados: Grupo 3
  + Compra de producto
    + Estructura: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G5/comprar.xml
    + Equipos involucrados: 
  + Fin de compra 
    + Estructura: ...
    + Equipos involucrados: ...



## Propuesta de mensaje común XML

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

## FAQ
Q: ¿Qué valores puede tomar el campo `<rol>`?

A: __Comprador__, __Tienda__ y __Monitor__
