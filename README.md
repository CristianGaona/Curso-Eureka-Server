# Curso-Eureka-Server
Eureka server, servidor para el registro de microservicios
## ¿Qué es y para qué sirve?
Cualquier microservicio debe poder localizar las diferentes instancias de otro servicio del que dependa sin ``````tener sus direcciones definidas en el código.

En el caso de que un microservicio deba acceder a otro lo ideal seria que de alguna manera pudiera saber en que direcciones esta las instancias de ese otro microservicio funcionando, pues lo más común es que se levanten diferentes instancias dependiendo de la carga.

Para ello en Spring se utiliza Eureka Server del paquete Spring Cloud NetFlix. Utilizando este paquete además de Ribbon y Feign conseguiremos que nuestra aplicación sea capaz de encontrar las diferentes instancias de un microservicio y balancear las peticiones de tal manera que se reparta la carga.

Tomado de: http://www.profesor-p.com/2019/01/03/microservicios-distribuidos-con-eureka/

## ¿Cómo funciona?
Lo primero es entender que un microservicio debe definirse como un cliente de Eureka. Una vez aclarado este detalle, vamos a explicar su funcionamiento.

Cuando un microservicio arranca, se comunicará con el servidor Eureka para notificarle que está disponible para ser consumido. El servidor Eureka mantendrá la información de todos los microservicios registrados y su estado. Cada microservicio le notificará su estado mediante heartbeats cada 30 segundos.
Si pasados tres periodos heartbeats no recibe ninguna notificación del microservicio, lo eliminará de su registro. Al igual que si después de sacarlo del registro recibe tres notificaciones, entenderá que ese microservicio vuelve a estar disponible.

Cada cliente o microservicio puede recuperar el registro de otros microservicios registrados y quedará cacheado en dicho cliente. Además, Eureka se puede configurar para funcionar en modo cluster, para que varias instancias intercambien su información.
![](https://blog.bi-geek.com/wp-content/uploads/2017/10/2017-10-31-13_58_50-Clipboard.png)


Tomado de: https://blog.bi-geek.com/arquitecturas-spring-cloud-netflix-eureka/
