# Ejemplo 1: Despliegue de la aplicación guestbook

En este ejemplo vamos a desplegar con docker-compose la aplicación *guestbook*, que estudiamos en el módulo de redes: [Ejemplo 1: Despliegue de la aplicación Guestbook](../modulo3/guestbook.md).

Puedes encontrar el fichero `docker-compose.yml`  en este [directorio](https://github.com/victoria-nr/curso_docker_ies/tree/main/ejemplos/modulo4/ejemplo1) del repositorio. 

En el fichero `docker-compose.yml` vamos a definir el escenario. El programa `docker-compose` se debe ejecutar en el directorio donde esté ese fichero. 

```yaml
version: '3.1'
services:
  app:
    container_name: guestbook
    image: iesgn/guestbook
    restart: always
    ports:
      - 80:5000
  db:
    container_name: redis
    image: redis
    restart: always
```

Para crear el escenario:

```bash
$ docker-compose up -d
Creating network "guestbook_default" with the default driver
Creating guestbook ... done
Creating redis     ... done
```

Para listar los contenedores:

```bash
$ docker-compose ps
  Name                 Command               State          Ports        
-------------------------------------------------------------------------
guestbook   python3 app.py                   Up      0.0.0.0:80->5000/tcp
redis       docker-entrypoint.sh redis ...   Up      6379/tcp            
```

Para parar los contenedores:

```bash
$ docker-compose stop 
Stopping guestbook    ... done
Stopping redis ... done
```

Para eliminar el escenario:

```bash
docker-compose down
Stopping guestbook ... done
Stopping redis     ... done
Removing guestbook ... done
Removing redis     ... done
Removing network guestbook_default
```

---

* [Ejemplo 2: Despliegue de la aplicación Temperaturas](temperaturas.md)



