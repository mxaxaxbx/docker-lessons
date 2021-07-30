# Archivo docker-compose
---
Un archivo Dockerfile es texto plano que lleva texto plano y contiene una serie de instrucciones necesarioas para crear una imagen que, posteriormente, se convertirpa en una aplicación. Éste archovo lleva unas propiedades especificas para la creación de una imagen. Entre ellas:

* **services**: se pudeen definir uno o varios servicios para una aplicación.
    * **nombre del servicio** puede ser cualquiera, pero único dentro de la aplicación
        * **image** nombre del servicio que queremos instalar
        * **link** los enlaces van atados o dependen de un **nombre de servicio** ya sea para usarse como proxy, balanceador de carga, etc...
        * **volumes** un contenedor es volatil y posee estados, en algun momento el contenedor debe de eliminarse, para hacer la información persistente se declara un volumen, es decir la dirección de un directorio dentro del host.
        * **ports** define el puerto de escucha de una aplicación

Por ejemplo, crear una carpeta para el proyecto

```
mkdir proxy && cd proxy
```

crear un archivo docker-compose.yml

```
vim docker-compose.yml
```

```
versio: '3'
services:
    web:
        image: dockercloud/hello-world
    lb:
        image: dockercloud/haproxy
        links:
            - web
        volumes:
            - /var/run/docker.sock:/var/run/docker.sock
        ports:
            - 80:80
```

Crear la imagen con 

```
docker compose up -d
```

Agregar el atributo -d para ejecutar en segundo plano

---

## ver logs de contenedor

Agregar atributo -f para ver registros en directo

```
docker logs <container_id> -f
``` 
---

## Establecer la cantidad de contenedores

con docker compose se pueden establecer la cantidad de contenedores que se ejecutarán para un servicio

```
docker-compose up --scale web=5
``` 

usar el atribut **up** para salir de la advertencia ambigua y el atributo --sacale acompañado del nombre de la imagen igualando el número de contenedores que se quieran crear
