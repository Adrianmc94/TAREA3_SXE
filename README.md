# Práctica Docker Alpine
## 1. Descarga de la imagen Alpine

Descargamos la imagen sin iniciar ningún contenedor con los comandos:

```bash
docker pull alpine
docker images
```

# 2. Crear un contenedor sin nombre

Creamos un contenedor a partir de la imagen:
```bash
docker create alpine
docker ps -a
```
El comando docker create crea la estructura del contenedor a partir de la imagen alpine pero no lo arranca inmediatamente. Solo lo prepara.
El comando docker ps -a lista todos los contenedores, incluidos los detenidos.
