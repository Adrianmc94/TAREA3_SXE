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

# 3. Creación y acceso al contenedor 'dam_alp1'
Comando de creación y arranque:
```bash
docker run -dit --name dam_alp1 alpine /bin/sh
```
run se usa para arrancar el contenedor 
--name asigna el nombre
alpine /bin/sh: Usa la imagen alpine e inicia el intérprete de comandos (/bin/sh), que mantiene el contenedor en estado de ejecución.
# Comando de acceso (para entrar a su terminal):
```bash
docker run -dit --name dam_alp1 alpine /bin/sh
```
# 4. Comprobación de IP y conectividad de 'dam_alp1'
Comando para obtener la IP:
```bash
docker inspect -f '{{.NetworkSettings.IPAddress}}' dam_alp1
```
El comando docker inspect muestra información detallada del contenedor. El flag -f se usa para filtrar y mostrar solo el valor de la dirección IP.

Comando de prueba de conectividad (debe ejecutarse dentro del contenedor, después de acceder con docker exec):
```bash
docker inspect -f '{{.NetworkSettings.IPAddress}}' dam_alp1
```
<img width="930" height="301" alt="CAPTURA" src="https://github.com/user-attachments/assets/e2403aae-7ece-49e5-b14e-deb71cbf7304" />








