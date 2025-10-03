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

# 5. Creación de 'dam_alp2' y prueba de ping entre contenedores
Se crea un segundo contenedor y se comprueba la comunicación de red interna entre los dos contenedores.

Comando de creación de 'dam_alp2' igual que en la creacion de dam_alp1.

<img width="730" height="352" alt="SIIII" src="https://github.com/user-attachments/assets/24cc987a-7bef-49b2-9d39-83c893b2fedf" />

# 6. Salgo del terminal, ¿qué le pasó al contenedor? 

Al escribir exit en esa ventana extra (docker exec), solo cerramos la sesión de terminal. El proceso principal del contenedor (que era /bin/sh) sigue corriendo en segundo plano, porque lo arrancamos con la opción -d (detached) para que no se detuviera.

# 7. Espacio en disco duro ocupado

```bash
docker system df
```
<img width="722" height="160" alt="sy" src="https://github.com/user-attachments/assets/d3a808e3-06e6-453c-91ed-aa7de729fa7f" />
-Imagenes : Ocupé un total de 12.88 MB de espacio en disco con la imagen base de Alpine.
-Contenedores (Containers): Los contenedores creados (la parte de escritura de cada uno) ocupan un total de 28.67 kB.

# 8. Consumo de RAM de los contenedores:

```bash
docker stats
```
<img width="1352" height="186" alt="listo" src="https://github.com/user-attachments/assets/2fbb936d-454a-45f4-ae95-f3f9b946908b" />

Contenedor dam_alp1: Está usando 1.414 MiB (Megabytes) de memoria RAM.

Contenedor dam_alp2: Está usando 520 KiB (Kilobytes) de memoria RAM.


