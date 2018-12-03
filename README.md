# SistemasMultiagentes2018
Proyecto de clase de Sistemas Multiagentes impartido en la ESIIAB

-----

## Tabla de contenidos

- [Sistemas Multiagentes 2018](#sistemas-multiagentes-2018)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Partes diferenciadas y equipo que las realiza](#partes-diferenciadas-y-equipo-que-las-realiza)
  - [Flujo de trabajo de una simulación](#flujo-de-trabajo-de-una-simulaci%C3%B3n)
    - [Tiendas](#tiendas)
    - [Consumidores](#consumidores)
  - [Mensajes necesarios](#mensajes-necesarios)
  - [Propuesta de mensaje común XML](#propuesta-de-mensaje-com%C3%BAn-xml)
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

### Tiendas

1. Todos los agentes se inicializan en sus máquinas respectivas.
2. Los agentes Tienda le mandan una petición XML ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploPeticionConexion.xml)) de conexión al Monitor. Para ello, se realizará una petición POST a `direccionMonitor:puertoMonitor/init`
3. El Monitor responderá a la petición ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploACKInicio.xml)) donde se asignará el ID y los agentes Tienda se quedarán a la espera.
4. El Monitor enviará un mensaje de inicialización a los agentes Tienda ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionTienda.xml))
5. Los agentes Tienda le mandarán una respuesta ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploACKAgenteIniciado.xml)) de confirmación y quedarán a la espera. Aquellos clientes que no envíen una confirmación no entrarán en la simulación.
6. El Monitor enviará un mensaje de inicio de simulación ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploGO.xml)) a los agentes Tienda, que no tendrá que ser respondido, y los agentes Tienda y Consumidor iniciarán la simulación

### Consumidores

1. Todos los agentes se inicializan en sus máquinas respectivas.
2. Los agentes Consumidor le mandan una petición XML ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploPeticionConexion.xml)) de conexión al Monitor. Para ello, se realizará una petición POST a `direccionMonitor:puertoMonitor/init`
3. El Monitor responderá a la petición ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploACKInicio.xml)) donde se asignará el ID.
4. Los agentes Consumidor se quedarán a la espera realizando un polling ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploPolling.xml)) con una petición POST a `direccionMonitor:puertoMonitor/prepareCliente`
5. El Monitor responderá con un mensaje negativo ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploNotReady.xml)) mientras la simulación no esté preparada. Cuando lo esté, pasará al paso 6
6. El Monitor responderá con un mensaje de inicialización a los agentes Consumidor ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploInicializacionCliente.xml)).
7. LLos agentes Consumidor se quedarán a la espera realizando un polling ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploPolling.xml)) con una petición POST a `direccionMonitor:puertoMonitor/simulationReady`
8. El Monitor responderá con un mensaje negativo ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploNotReady.xml)) mientras la simulación no esté iniciada. Cuando lo esté, pasará al paso 9
9. El Monitor enviará un mensaje de inicio de simulación ([plantilla](https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G6/EjemploGO.xml)) a los agentes Consumidor, que no tendrá que ser respondido, y los agentes Consumidor iniciarán la simulación

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
    + Estructura G1: https://github.com/Kaysera/SistemasMultiagentes2018/tree/master/Grupos/G1
    + Estructura G5: https://github.com/Kaysera/SistemasMultiagentes2018/blob/master/Grupos/G5/comprar.xml
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
      <id>123</id>
    </direccion>
    <rol>tienda</rol>
  </emisor>
  <receptor>
    <direccion>
      <ip>192.168.1.2</ip>
      <puerto>80</puerto>
      <id>456</id>
    </direccion>
    <rol>comprador</rol>
  </receptor>
  <tipo>venta</tipo>
  <fecha>2018-10-25</fecha>
  <hora>15:58:32</hora>
  <cuerpo>
    ...
  </cuerpo>
</mensaje>
```

## FAQ
Q: ¿Qué valores puede tomar el campo `<rol>`?

A: __Comprador__, __Tienda__ y __Monitor__

Q: ¿Cómo se identifica a cada agente?

A:
  + Al __Monitor__ se le identificará por una _IP_ y _puerto_, que serán conocidos por todos de antemano
  + A los __Compradores__ y __Tiendas__ se les identificará por una _IP_, un _puerto_ y un _ID_. Una misma combinación de _IP_ y _puerto_ puede tener varios agentes, por lo que el _ID_ será necesario. Dicho _ID_ será porporcionado por el __Monitor__
