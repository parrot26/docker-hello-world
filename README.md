# hello-world

_Ejecutamos el primer contenedor en **Docker** y nada mejor que con un **Hello World**._

### Comenzando 🚀

* _Nos fijamos si tenemos alguna imagen descargada en nuestro repo local_

```ssh
$docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```

* _Revisamos si hay algún contenedor corriendo (**ps**) o detenido (**-a**):_

```ssh
$docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

* _Iniciamos una búsqueda de la imagen hello world y utilizamos la palabra **world** para ver que pasa._

```ssh
$docker search world
NAME                                         DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
hello-world                                  Hello World! (an example of minimal Dockeriz…   1562      [OK]       
wowstack/world-server                        Provides a Vanilla WoW game world server        3                    
worldcon75/api-kansa-server                  Kansa server service for Worldcon 75 API        1                    [OK]
cedricbl/world-cup-2018-cli-dashboard        ⚽🏆A World Cup 2018 CLI dashboard – Watch m…     1                    
worldcon75/api                               API service for Worldcon 75                     1                    [OK]
worldcon75/api-nginx                         nginx service for Worldcon 75 API               1                    [OK]
worldcon75/api-postgres                      Postgres master service for Worldcon 75 API     1                    [OK]
worldcon75/api-kyyhky                        kyyhky service for Worldcon 75 API              1                    [OK]
worldcon75/api-hugo                          Hugo service for Worldcon 75 API                1                    [OK]
worlddatacenter/dj-portal                    dj-portal                                       0                    [OK]
raintank/worldping-api                       Worldping Backend API server                    0                    
worldhosts/game                                                                              0                    
worldsense/devserver                                                                         0                    
worlddirect/wd-k8s-operator                                                                  0                    
worldpeaceio/wordpress-integration           The easiest way to run WordPress integration…   0                    
ironarachne/worldapi                         The full world generation API                   0                    
worldwinner/fitnessfriend-ui                                                                 0                    
worldwinner/fitnessfriend-app                                                                0                    
cfcommunity/worlds-simplest-service-broker                                                   0                    
worldiety/k8s-deploy                                                                         0                    
bihero/world                                                                                 0                    
worldcon75/api-client                        Client static assets for Worldcon 75 API        0                    [OK]
worldsibu/forma-client-k8s                   Forma Client for k8s service                    0                    
worldpak/hss-repo                            Holds docker images used for HSS microservic…   0                    
edgardohriv/worldcitiesapi                                                                   0                    
```

* _Sale un resultado bastante sucio. Hay que aplicar un filtro:_

```ssh
$docker search -f is-official=true --filter stars=3 world
NAME          DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
hello-world   Hello World! (an example of minimal Dockeriz…   1562      [OK]       
```

###### _Ahora sí! Mucho más limpio. Se le agregó dos filtros (-f es igual a --filter) a la palabra world. Uno para que busque solo una imagen oficial y el segundo que tenga como mínimo 3 estrellas._

* _Corremos la aplicación:_

```ssh
$docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:37a0b92b08d4919615c3ee023f7ddb068d12b8387475d64c622ac30f45c29c51
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

###### _Al no encontrarla en el repo local, primero la descarga desde el repositorio de Docker y luego la ejecuta._

* _Ahora podemos volver a ver las imágenes que tenemos:_

```ssh
$docker images
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
hello-world   latest    feb5d9fea6a5   5 weeks ago   13.3kB
```

###### _Ya tenemos la imagen hello-world en el repositorio local. El lastest en el **TAG** nos dice que es la última versión de esa imagen, y fue creada (**CREATED**) hace 5 semanas en el repositorio de Docker y que pesa (**SIZE**) 13.3kB._

* _Al revisar los contenedores corriendo (**Up**) vemos que no aparece nada._

```ssh
$docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

* _Pero si nos vamos a ver los contenedores corriendo o detenidos sí aparece._

```ssh
docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
340fd81b0ad1   hello-world   "/hello"   51 seconds ago   Exited (0) 45 seconds ago             elegant_ellis
```

###### _El contenedor no aparece en estado Up porque se ejecutó solamente para lanzar el hello world y salir. Esta es una imagen muy pequeña y solo fue creada para ejecutar el famoso Hola Mundo_

_Otra forma de descargar una imagen es realizando un **pull** primero (**docker pull hello-world**) y luego el **run** para hacerla correr._ 

_En el ejemplo, ejecutamos primero el **run** sin el **pull** y siempre busca primero en el repo local y si la encuentra la ejecuta. En caso contrario, como vimos, la descarga y luego la lanza._

_Para buscar imágenes disponibles vía web y no utilizar la línea de comandos nos podemos dirigir a [DockerHub](https://www.docker.com/products/docker-hub). Ahí podemos ver todas las imágenes disponibles y las versiones (**TAG**) que tenemos._

###### _Para descargar una imagen con una versión específica solo alcanza con colocarle después del nombre :+versión y listo:_
```ssh
docker pull ubuntu:21.04
```

# 
### Contribuyendo 🖇️

_Las contribuciones son lo que hacen que la comunidad de código abierto sea un lugar mejor. Cualquier contribución que hagas será muy apreciada._

_Si queres aportar con alguna sugerencia para mejorarlo, simplemente un **fork** en el repo y crear un **pull request**. También podes abrir un issue con la etiqueta **enhancement**. ¡No te olvides de sumar una estrella al repo! **¡Gracias de nuevo!**_

# 
### Autor ✒️

* **Juan Pablo Soto** - [GitHub](https://github.com/parrot26) - [Linkedin](www.linkedin.com/in/juanpablosoto26)


# 
### Expresiones de Gratitud 🎁

* Comenta a otros sobre este repo 📢
* Invita una cerveza 🍺 o un café ☕ a alguien del equipo. 
* Da las gracias públicamente 🤓.

#### _Gracias a:_

* [Docker](https://www.docker.com/)


---
⌨️ con ❤️ por [Juan Pablo Soto](https://github.com/parrot26)





