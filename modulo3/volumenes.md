# Volúmenes docker y bind mount

## Los contenedores son efímeros

**Los contenedores son efímeros**, es decir, los ficheros, datos y configuraciones que creamos en los contenedores sobreviven a las paradas de los mismos pero, sin embargo, son destruidos si el contenedor es destruido. 

## Los datos en los contenedores

![docker](img/types-of-mounts.png)

Ante la situación anteriormente descrita Docker nos proporciona varias soluciones para persistir los datos de los contenedores. En este curso nos vamos a centrar en las dos que considero que son más importantes:

* Los **volúmenes docker**.
* Los **bind mount**
* Los **tmpfs mounts**: Almacenan en memoria la información. (No lo vamos a ver en este curso)

## Volúmenes docker

Si elegimos conseguir la persistencia usando volúmenes estamos haciendo que los datos de los contenedores que nosotros decidamos se almacenen en una parte del sistema de ficheros que es gestionada por docker y a la que, debido a sus permisos, sólo docker tendrá acceso. En linux se guardan en `/var/lib/docker/volumes`. Este tipo de volúmenes se suele usar en los siguiente casos:

* Para compartir datos entre contenedores. Simplemente tendrán que usar el mismo volumen.
* Para copias de seguridad ya sea para que sean usadas posteriormente por otros contenedores o para mover esos volúmenes a otros hosts.
* Cuando quiero almacenar los datos de mi contenedor no localmente sino en un proveedor cloud.

### Gestionando volúmenes

Algunos comandos útiles para trabajar con volúmenes docker:

* **docker volume create**: Crea un volumen con el nombre indicado.
* **docker volume rm**: Elimina el volumen indicado.
* **docker volume prune**: Para eliminar los volúmenes que no están siendo usados por ningún contenedor.
* **docker volume ls**: Nos proporciona una lista de los volúmenes creados y algo de información adicional.
* **docker volume inspect**: Nos dará una información mucho más detallada de el volumen que hayamos elegido.

## Bind mounts

Si elegimos conseguir la persistencia de los datos de los contenedores usando bind mount lo que estamos haciendo es "mapear" (montar) una parte de mi sistema de ficheros, de la que yo normalmente tengo el control, con una parte del sistema de ficheros del contenedor. Por lo tanto podemos montar tanto **directorios** como **ficheros**. De esta manera conseguimos:

* Compartir ficheros entre el host y los containers.
* Que otras aplicaciones que no sean docker tengan acceso a esos ficheros, ya sean código, ficheros etc...

---

* [Asociando almacenamiento a los contenedores: volúmenes Docker](asociacion_volumen.md)
