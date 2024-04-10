## Comandos de Docker
Bajar imágenes de Docker Hub.
`docker pull [Image Name]`

Correr un contenedor.
`docker run [Image Name]`

Corre un contenedor en segundo plano.
`docker run -d [Image Name]`

Correr un contenedor basado en un nombre que asignamos al contenedor .
`docker start [Container Name]`

Lista los contenedores activos en el SO.
`docker ps`

Lista los contenedores tanto activos como no activos en el SO.
`docker ps -a`

Detener el contenedor.
    - Detiene el contenedor pero no libera los recursos que está usando.
`docker stop [Container Name]`

Remover el contenedor.
    - Se remueve el contenedor y libera los recursos usados del sistema.
`docker rm [Container Name]`

Matar el contenedor.
    - Mata el contenedor y libera los recursos del sistema, no es muy recomendable.
`docker kill [Container Name]`

Especificaciones de la imagen.
`docker images inspect [image]`

## Límites de Docker
Definir la memoria maxima a usar.
`docker run --memory="128m" nginx`

Definir el porcentaje de procesadore a usar .
`docker run --cpu="0.6" nginx`

## Ejercicio 1
Se generara un servidor web creado a partir de la Imagen de Nginx a la cual llamaremos webserver y funcionara en el puerto 80 de la maquina local y en el puerto 80 del docker.
`docker run --publish 80:80 --name webserver nginx`

En este caso el terminal seguira mostrando el despliegue del contenedor por lo que para trabajar debemos abrir otra terminal, no obstante podemos usar la misma terminal si usaramos la opcion -d que desplegara el docker en segundo plano liberando la terminal.
`docker run -d --publish 80:80 --name webserver nginx`

Podemos observar que el contenedor esta desplegado y activo en el SO con el comando:
`docker ps`

Podemos detener el contenedor con:
`docker stop webserver`

Se detendra el servidor pero como tal los recursos de memoria usados por el contenedor no se veran liberados, para observar los contenedores actualmente detenidos podemos ejecutar el comando:
`docker ps -a`

Ahora si queremos liberar la memoria y terminar como tal todo el trabajo del contenedor podemos usar el comando:
`docker rm webserver`

## Ejercicio 2
Replicar el ejercicio 1 con una imagen distinta disponible en Docker Hub.

`docker run -d --publish 80:80 --name backserverjs node`
`docker ps`
`docker ps -a`
`docker rm backserverjs`

Como nota hay qe decir que en esta ocasion el docker nunca se pudo levantar o activar, como tal esto puede darse debido a que el docker no esta cumpliendo ningun proceso por lo cual esta no se llega a levantar

## Vincular una terminal a Docker

### Contenedor Pausado
Shell (Linux)
`docker run -it nginx bash`

Powershell (Windows)
`docker run -it nginx microsoft/powershell`

### Contenedor activo
Shell (Linux)
`docker container exec -it nginx bash`