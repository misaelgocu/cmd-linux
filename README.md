
---
## Comandos de la terminal Linux

***Basics**
Estos no los explico porque son los de cajón
```
cd
pwd
ls
ls -la
-h
man
hostname -I
neofetch

```


***
1. locate
***
Sirve para encontrar archivos de forma rápida consultando una base de datos indexada del sistema (llamada mlocate). Es mucho más veloz que `find`, pero si el archivo es muy nuevo, es posible que no aparezca hasta que se actualice la base de datos con el comando `updatedb`.

* Ejemplo: Buscar todos los archivos que empiecen con "archivo" y tengan cualquier extensión.

    `locate archivo.*`

***
2. whereis
***
Se utiliza para localizar el binario (ejecutable), las fuentes y las páginas del manual de un comando específico. No busca archivos de usuario comunes, sino archivos del sistema relacionados con programas instalados.

Sintaxis: `whereis [nombre_del_programa]`

Ejemplo: Ver dónde están los archivos relacionados con el comando PHP.  
`whereis php`
***
3. find
***
Es la herramienta de búsqueda más potente y versátil. A diferencia de locate, busca en el disco duro en tiempo real, permitiendo filtrar por nombre, tipo, tamaño, permisos o fecha de modificación.

Sintaxis: `find [ruta] [opciones] [expresión]`

Significado del ejemplo:

/: Busca en todo el sistema de raíz.

-type f: Filtra para que solo devuelva archivos (no carpetas).

-name: Indica el patrón del nombre a buscar.

Ejemplo: `find / -type f -name app.*`


***
***4. ps aux | grep***
***
Este no es un comando único, sino la combinación de dos herramientas mediante una tubería (pipe |).

ps aux: Lista todos los procesos que se están ejecutando en el sistema en este momento.

grep: Filtra la salida para mostrar solo las líneas que coincidan con un texto.

¿Para qué sirve? Para localizar procesos específicos que están corriendo en segundo plano, ver cuánta memoria consumen o identificar su PID (ID de proceso) para detenerlos.

Ejemplo: Buscar si hay algún proceso activo relacionado con "app". 
`ps aux | grep app.*`

***
***5. cat > name***

Este comando nos ayuda a crear un archivo, una vez se ejectuta escribe lo que sea y ese texto estara ahí en ese texto, se cierra con ctrl + D

---
***6.  cat >> name***

nos ayuda agregar contenido del archivo ya existente

---

***7. cat >| name***

Sobre escribe el archivo, borra el anterior y escribe lo nuevo

---
***8. touch name***

Crear un archivo nuevo

---

***9. cp file /root/folder/newfile***

copiar un archivo a la dirección donde lo mandes

---

***10. mv file file2***

Renombrar  un archivo

---

***11. rm name***

Eliminar un archivo

***12. rmdir folder*** 

Eliminar una carpeta que está vacía

---

***13. rm -r folder***

Eliminar un folder con su contenido

---

***14. head /etc/snort/snort.conf***

para ver el principio de un archivo

* Para ver las primeras 20 líneas de un archivo
    ```
        head -20 /etc/snort/snort.conf
    ``` 

***15. tail /etc/snort/snort.conf***

Para ver las ultimas lineas de un archivo
* Para ver las ultimas 20 líneas de un archivo
    ```
        tail -20 /etc/snort/snort.conf
    ``` 

***16. nl /etc/snort/snort.conf***

Numerar la cantidad de las lineas de un archivo

`nl /etc/snort/snort.conf`

---

***17. cat /etc/snort/snort.conf | grep output***

Para filtrar palabras clave de un archivo, en este caso output

---
***18. nl /etc/snort/snort.conf  | grep output***

Para encontrar las lineas donde se encuentran las palabras clave

`tail -n+ 507 /etc/snort/snort.conf | head -n 6`

Este comando extrae un rango específico de líneas (de la 507 a la 512) del archivo de configuración de Snort.

Desglose rápido:

`tail -n+ 507 `: Empieza a leer el archivo desde la línea 507 en adelante (omite las primeras 506).

`/etc/snort/snort.conf`: Es la ruta del archivo que estás consultando.

| (pipe): Pasa el resultado del primer comando al segundo.

`head -n 6`: Toma solo las primeras 6 líneas que recibió del tail.

En resumen: Estás visualizando exactamente las líneas 507, 508, 509, 510, 511 y 512 de ese archivo.

---

***19. sed para encontrar y reemplazar***

Buscar coincidencias de una palabra 

``

Busquemos mysql en snort.conf 

`cat /etc/snort/snort.conf | grep mysql`

Este comando encuentra todas las coincidencias

Para reemplazar con MySQL

`sed s/mysql/MySQL/g /etc/snort/snort.conf > snort2.conf`

El comando `s` realiza la búsqueda

con `/` le das la palabra clave a buscar (mysql)

con `/`  le das la palabra a reemplazar

El cmd `g` para indicar que reemplazaras todas las coincidencias


---
***20. Ver archivos con more y less***

Esto nos sirve para archivos largos

***more***

`more /etc/snort/snort.conf `
Puedes bajar con enter y te muestra un barra de tiempo que muestra el % de la página que estas recorriendo.
Para salir presion `q`


***less***

`less /etc/snort/snort.conf `

Muestra y filtra al igual que more puedes ver y scrolear con enter, salir con q, pero además puedes filtrar 
En la esquina inferior izquierda solo escribe un slash y una palabra a buscar y te mostrara la palabra clave sobresaltada `/ keyword`


---
## Redes
---

***21. ver redes activas***

`ifconfig`

Puedes ver la conexión de red por cable, información de la ip, mascara de red, red inalámbrica.

`iwconfig`

tener información de adaptadores 

---

***22. cambiar la ip, mascara de red, dirección broadcast***

Para cambiar la dirección ip

`ifconfig eth0 192.168.x.x`

`ifconfig eth0 192.168.x.x netmask 255.255.0.0 broadcast 192.168.x.x`

`ifconfig eth0 192.168.x.x`


Reemplaza las x por tus números correspondientes



---

***23. Falsificar tu MAC address***

Cambiar la dirección MAC (el identificador físico único) de tu tarjeta de red en sistemas Linux.

```
ifconfig eth0 down

ifconfig eth0 hw ether 00:11:22:33:44:55

ifconfig eth0 up
```

1. Desactivar la interfaz
ifconfig eth0 down

Para qué sirve: Apaga la interfaz de red llamada eth0.

Por qué es necesario: No puedes cambiar la configuración de hardware de una tarjeta de red mientras está activa y transmitiendo datos.

2. Cambiar la dirección física (MAC)
ifconfig eth0 hw ether 00:11:22:33:44:55

Para qué sirve: Cambia la dirección MAC de la tarjeta por la que tú elijas (en este caso, 00:11:22:33:44:55).

Nota importante: Este cambio es temporal. Si reinicias la computadora, la tarjeta volverá a su dirección MAC original de fábrica.

. Reactivar la interfaz
ifconfig eth0 up

Para qué sirve: Enciende de nuevo la interfaz eth0.

Resultado: Ahora la tarjeta volverá a conectarse a la red, pero identificándose con la nueva dirección MAC que configuraste en el paso anterior.

Por qué alguien haría esto?
Privacidad: Para evitar que rastreen tu dispositivo en redes Wi-Fi públicas.

Pruebas de seguridad: Para simular ser otro dispositivo dentro de una red (pentesting).

Saltar restricciones: Algunos routers limitan el acceso a internet basándose en la dirección MAC; cambiarla puede ayudar a saltar esos bloqueos.

Dato extra: El comando ifconfig se considera hoy en día "depreciado" (antiguo). En versiones modernas de Linux, se recomienda usar el comando ip. Por ejemplo: `ip link set eth0 down`.

### Asignar nueva direción ip  del servidor DHCP

EL DHCP asigna direciones IP  a todos los sistemeas en la sub red y mantiene archivos de registro del cual una direción IP está alojada en que maquina y en cualquier momento.
Para solictar un direción IP de DHCP, lamamos lal servidor DHCP con el comando ``` dhclient ``` seguido de la interfaz que quieras asignar 

```
dhclient eth0
ifconfig
```

### Examinar DNS con dig

Ofrece una forma para recolectarinformacion DNS sobre un domino, com la direción IP, servidor email, subdominios y direciones IP

Agrega ns (short nameserver)

```
dig hackers-arise.com ns
```
con el short mx es para conocer el sistema email

```
dig hackers-arise.com mx
```

---
### Resumen de comandos
---

| Comando | Velocidad | Fuente de información | ¿Qué busca? |
| :--- | :--- | :--- | :--- |
| **locate** | Muy rápida | Base de datos indexada | Cualquier archivo por nombre. |
| **whereis** | Rápida | Rutas estándar de sistema | Binarios, manuales y fuentes de comandos. |
| **find** | Lenta | Escaneo de disco en vivo | Búsqueda exhaustiva con filtros avanzados. |
| **ps \| grep** | Instantánea | Memoria RAM (procesos) | Programas que se están ejecutando ahora. |

***

Link de instrucciones en video:
https://www.youtube.com/watch?v=B6YiXInMPRA

Ver carpetas de archivos 
'eza' 
'''
eza --icons

eza -l

eza -ls la

eza -T

Busca en internet o IA para que sirve cada herramienta

---

Instalación:

```
sudo apt install eza
sudo apt install glances
sudo apt install cmatrix
sudo apt install ncdu
```


```
 cmatric -c color

 ~  cmatrix -e
 Usage: cmatrix -[abBcfhlsmVx] [-u delay] [-C color]
 -a: Asynchronous scroll
 -b: Bold characters on
 -B: All bold characters (overrides -b)
 -c: Use Japanese characters as seen in the original matrix. Requires appropriate fonts
 -f: Force the linux $TERM type to be on
 -l: Linux mode (uses matrix console font)
 -L: Lock mode (can be closed from another terminal)
 -o: Use old-style scrolling
 -h: Print usage and exit
 -n: No bold characters (overrides -b and -B, default)
 -s: "Screensaver" mode, exits on first keystroke
 -x: X window mode, use if your xterm is using mtx.pcf
 -V: Print version information and exit
 -u delay (0 - 10, default 4): Screen update delay
 -C [color]: Use this color for matrix (default green)
 -r: rainbow mode
 -m: lambda mode



```