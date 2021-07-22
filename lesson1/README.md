# Instalación de Docker
---
Acceder a la documentación oficial de Docker [Instalar docker en Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

## Instalación de docker en Linux Ubuntu
---
Desinstalar versiones anteriores
```
 sudo apt-get remove docker docker-engine docker.io containerd runc
```
---

### Instalar componentes necesarios
```
  sudo apt-get update
```

```
  sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Agregar llave PGP
```
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

```
---

### Instalar Docker
```
  sudo apt-get update
```
```
   sudo apt-get install docker-ce docker-ce-cli containerd.io
```
---

### Verificar instalación
Descarga imagen de prueba y ejecutar en un contenedor
```
 sudo docker run hello-world
```

Una vez has corrido el comando anterior y si la instalación se realizó con exito verá los siguiente en pantalla.

```
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
---
### Verificar versión de Docker
```
sudo docker version
```

## Instalación de docker compose en linux
Docker composer permite simplificar el uso de docker a partir de archivos **YAML**, siendo más sencillo crear contenedores, conectarlos, habilitar puertos, volumenes, etc. Más info en [DockerTips](https://dockertips.com/utilizando-docker-compose#:~:text=Docker%20Compose%20es%20una%20herramienta%20que%20permite%20simplificar%20el%20uso%20de%20Docker.&text=En%20vez%20de%20utilizar%20Docker,Engine%20a%20realizar%20tareas%2C%20programaticamente.).

### Instalar la ultima versión estable de Docker Compose:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

```
---
### Dar permisos de ejecución al archivo descargado
```
sudo chmod +x /usr/local/bin/docker-compose
```

### Comprobar versión
```
docker-compose --version
```
```
docker-compose version 1.29.2, build 5becea4c
```
---

## Clonar repositorio de ejemplo
```
git clone https://github.com/jsgiraldoh/Codimd.git
```
Navegar hasta el directorio
```
cd Codimd
```

Construir del archivos YML
```
docker-compose up -d
```


Ver lista de imagenes disponibles
```
sudo docker container ls
```

Probar herramienta de markdown
```
http://localhost:3000
```

---
### Habilitar docker sin superusuario
```
sudo systemctl enable docker
```

Ver estado
```
sudo systemctl status docker
```
dar permisos de docker al usuario actual
```
sudo usermod -aG docker ubuntu
```

Por ultimo reiniciar el equipo
```
sudo reboot
```
