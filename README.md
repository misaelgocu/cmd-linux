Link de instrucciones en video:
https://www.youtube.com/watch?v=B6YiXInMPRA

Ver carpetas de archivos 
'eza' 
'''
eza --icons
eza -l
eza -ls la
eza -T

BUsca en internet o IA para que sirve cada herramienta
---
Instalación:
'''
sudo apt install eza
sudo apt install glances
sudo apt install cmatrix
sudo apt install ncdu

'''

'''
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



'''
---
## Comandos de la terminal Linux
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


---
### Resumen de comandos
---

| Comando | Velocidad | Fuente de información | ¿Qué busca? |
| :--- | :--- | :--- | :--- |
| **locate** | Muy rápida | Base de datos indexada | Cualquier archivo por nombre. |
| **whereis** | Rápida | Rutas estándar de sistema | Binarios, manuales y fuentes de comandos. |
| **find** | Lenta | Escaneo de disco en vivo | Búsqueda exhaustiva con filtros avanzados. |
| **ps \| grep** | Instantánea | Memoria RAM (procesos) | Programas que se están ejecutando ahora. |