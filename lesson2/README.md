#  Instalación del servidor Nginx
---
Acceder a la documentación oficial de Docker [Instalar ngnix en docker](https://hub.docker.com/_/nginx)

## Creación de archivo Dockerfile

Crear un directorio llamado *mi-primer-dockerfile* dentro de él crear un archivo Dockerfile

```
cd mi-primer-dockerfile
nano Dockerfile
```

Dentro de él agregamos lo siguiente:

```
FROM nginx
COPY static-html-directory /usr/share/nginx/html

```

Donde instalaremos nginx y servimos la carpeta static-html-directory

---

## Creación de archivo html

Dentro del directorio mi-primer-dockerfile creamos una carpeta **static-html-directory** y dentro de el un archivo **index.html**

```
mkdir static-html-directory
cd static-html-directory
nano index.html
```

dentro del archivo **index.html** crearemos contenido cualquiera como ejemplo de mustra de encendido del servidor. P. ej.

```
hello world
```
---

## Construcción de imagen

en la carpeta padre, es decir la carpeta mi-primer-docker-file

```
cd ..
ls 
```

```
Dockerfile  static-html-directory
```

Construir la imagen de arranque con el siguiente comando

```
docker image build -t some-content-nginx .
```

Podemos listar la imagen construida y otras que se hayan construido

```
docker image ls
```

```
REPOSITORY                        TAG           IMAGE ID       CREATED         SIZE
*some-content-nginx                latest        cb02c5554924   2 days ago      133MB
mxaxaxbx/fedesoft-web             latest        cb02c5554924   2 days ago      133MB
jsgiraldoh/fedesoft-web           latest        b3153cc68e1f   2 days ago      133MB
nginx                             latest        08b152afcfae   3 days ago      133MB
ubuntu                            latest        c29284518f49   11 days ago     72.8MB
hello-world                       latest        d1165f221234   4 months ago    13.3kB
nabo.codimd.dev/hackmdio/hackmd   2.2.0         09a9a7c1d73e   12 months ago   819MB
postgres                          11.6-alpine   89ae06c2ad76   18 months ago   152MB
```
---

## Arranque de servidor

Tomaremos el contenido de la carpeta **static-html-directory** gracias a la imagen construida en un servidor en el puerto 8080

```
docker run --name some-nginx -d -p 8080:80 some-content-nginx
```

Verificar el estado con curl y/o en un browser
```
curl -k localhost:8080
```

```
hello world
```
---

## Creación de repositorio en Docker Hub

Una vez se tenga una cuenta creada en [Docker Hub](https://hub.docker.com/) autenticar en consola con **username** y **password**

```
docker login
```

```
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username:
Password:
```

```
WARNING! Your password will be stored unencrypted in /home/user/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded

```

En docker ingresamos a la [Lista de Repositorios](https://hub.docker.com/repositories) y hacer clic en [crear repositorio nuevo](https://hub.docker.com/repository/create?namespace=)

En la consola agregar los siguiente para dejar el repositorio alojado

```
docker tag local-image:some-content-nginx  new-repo:my-repo
docker push new-repo:my-repo
```
