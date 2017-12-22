# Como perder datos a lo big data
(... y noSQL)

## Tips Generales

* Heartbeat & GC
  * Stop the world implica no :heart:
  * :+1: G1GC (aunque a veces no alcanza)


* Espacio libre en disco
  * :-1: Mongo y Cassandra


* :-1: Discos de red
  * Picos de latencia & IO Queue
  * A menos que tenga enlace dedicado


* Perdida de un nodo y replicación
  * O cómo la solución puede ser peor que el problema....

* Backup: no hay
  * Otro cluster....

* Monitoreo fino
  * :-1: Munnin y Nagios actualizan cada varios minutos
  * :-1: La mayoría de estos bichos generan demasiadas métricas
  * Herramientas básicas:
    * [Linux Performance Tools](https://medium.com/netflix-techblog/netflix-at-velocity-2015-linux-performance-tools-51964ddb81cf)
    * [Linux Performance Analysis in 60,000 Milliseconds](https://medium.com/netflix-techblog/linux-performance-analysis-in-60-000-milliseconds-accc10403c55)
    * Broken Linux Performance Tools: [video](https://www.youtube.com/watch?v=9U4jFpsEyYE) [slices](https://www.slideshare.net/brendangregg/broken-linux-performance-tools-2016)

-----

## Zookeper

* :+1: Anda: Jepsen certified: https://aphyr.com/posts/291-jepsen-zookeeper
* :-1: Api muy de bajo nivel, usar :+1: [Curator](https://curator.apache.org/)

### Usos:
 * Configuración global a múltiples nodos, consistente.
 * Lider elecction/lock soft (correr un batch una sola vez)
 * :-1: *NO* usar para lock intensivo
 * ProTip: usar `chroot`

### Admin
* :+1: Fácil ver situación: [4 letters commands](https://zookeeper.apache.org/doc/r3.4.11/zookeeperAdmin.html#sc_zkCommands)
* Tenes que poner las ips/nombres fijas en las config de los nodos: [Clustered (Multi-Server) Setup](https://zookeeper.apache.org/doc/r3.4.11/zookeeperAdmin.html#sc_zkMulitServerSetup)
* :-1: Cambiar un node es un dolor de huevos:
  1. [Cambiar los nodos](https://gist.github.com/miketheman/6057930)
  1. Si aplica, cambiar el [dns](https://wiki.apache.org/hadoop/ZooKeeper/FAQ#A8)
  1. Reiniciar *TODOS* los clientes (el cliente de ZQ se cachea las ips)


### Referencias Generales
* [Paper summary: ZooKeeper: Wait-free coordination for Internet-scale systems](http://muratbuffalo.blogspot.com.ar/2014/09/paper-summary-zookeeper-wait-free.html)

* [Consensus Systems for the Skeptical Architect](http://www.ustream.tv/recorded/61483409)

----

## Hadoop

* :-1: Complejo de instalar y mantener
* :+1: Al menos usar una distro

-----
## Hbase/Cassandra

-----
## Hive?

-----

## Kafka

-----
