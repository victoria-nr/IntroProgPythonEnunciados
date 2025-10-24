# UT3_1: Librerías útiles para administradores de sistemas en Python 

En esta unidad vamos a introducir algunas de las librerías más útiles para la administración de sistemas. A continuación se explican las librerías más importantes y se incluyen ejemplos prácticos. Recuerda ir a cada uno de los enlaces de las librerías correspondientes y explorarlas para entender su funcionamiento. 

[SYS](https://docs.python.org/es/3.13/library/sys.html) 

Permite acceder a variables y funciones del intérprete de Python. Útil para obtener información del sistema o finalizar la ejecución del programa. 

Funciones importantes: 

`sys.version` — versión de Python 

`sys.platform` — tipo de sistema operativo 

`sys.exit()` — termina el programa 

`sys.argv` — devuelve la lista de argumentos de la línea de comandos pasados a un script de Python. `argv[0]` es el nombre del script, `argv[1]` es el primer argumento, etc. 

 

Ejemplo 1:

```python
import sys 
 
print("Versión de Python:", sys.version) 
print("Sistema operativo:", sys.platform) 
 
# Finalizar el programa si no es Windows 
if sys.platform != "win32": 
    print("Este script solo funciona en Windows.") 
    sys.exit() 
``` 

Ejemplo 2: 

```python
import sys 

if len(sys.argv) >= 2: 
    argumento = int(sys.argv[1]) 

else: 
    print('No hay argumentos') 
``` 
 

[OS](https://docs.python.org/es/3.13/library/os.html) 

Permite interactuar con el sistema operativo: rutas, directorios, variables de entorno, etc. A la hora de trabajar con rutas y directorios, utlizaremos mejor la librería pathlib, que es más moderna. 

Funciones importantes:

`os.getcwd()` — devuelve el directorio actual — `Path.cwd()`

`os.listdir()` — lista el contenido del directorio 

`os.getenv('PATH')` — obtiene variables de entorno 

`os.mkdir('carpeta')` — crea un directorio — `Path.mkdir()` 

Ejemplo:

```python
import os 
 
print("Directorio actual:", os.getcwd()) 
print("Contenido:", os.listdir(".")) 
 
# Crear carpeta si no existe 
if "carpeta" not in os.listdir("."): 
    os.mkdir("carpeta") 
    print("Carpeta 'carpeta' creada.") 
```

[DATETIME](https://docs.python.org/es/3.13/library/datetime.html)

Permite trabajar con fechas y horas, ideal para planificar tareas o generar nombres de archivos con fecha. 

Funciones importantes:

`datetime.now()` — obtiene fecha y hora actuales 

`date.today()` — devuelve solo la fecha actual 

`timedelta(days=1)` — permite restar o sumar días 

Revisar los atributos que tiene la clase datetime 

Revisar la función `strftime` para formatear fechas 

Ejemplo:

```python
from datetime import datetime, timedelta 
 
hoy = datetime.now() 
print("Fecha y hora actuales:", hoy) 
 
ayer = hoy - timedelta(days=1) 
print("Ayer fue:", ayer.strftime("%Y-%m-%d")) 
 
# Crear nombre de backup con fecha 
nombre_backup = f"backup_{hoy.strftime('%Y_%m_%d')}.zip" 
print("Nombre de backup:", nombre_backup) 
```

[PLATFORM](https://docs.python.org/es/3/library/platform.html)

Proporciona información sobre el sistema operativo y el hardware. 

Funciones importantes:

`platform.system()` — devuelve el nombre del SO 

`platform.release()` — versión del SO 

`platform.processor()` — tipo de procesador 

Ejemplo:

```python
import platform 
 
print("Sistema operativo:", platform.system()) 
print("Versión:", platform.release()) 
print("Procesador:", platform.processor()) 
 
if platform.system() == "Windows": 
    print("Configurando entorno para Windows...") 
```

[PATHLIB](https://docs.python.org/es/3.13/library/pathlib.html#module-pathlib) 

Ofrece una forma moderna de trabajar con rutas de archivos y directorios. Normalmente utlizaremos la clase `Path`

Funciones y propiedades importantes:

`Path.cwd()` — devuelve el directorio actual 

`Path.iterdir()` — itera sobre los elementos de un directorio (lo veremos más adelante) 

`Path.exists()` — comprueba si un archivo o carpeta existe 

`Path.is_dir()` — comprueba si es carpeta 

`Path.is_file()` — comprueba si es un archivo  

`Path.mkdir()` — crea carpeta 

`Path.rmdir()` — elimina carpeta 

`Path.rename()` — renombra carpeta 

`Path.stat()` — devuelve objeto con información sobre la ruta (id de usuario, id de grupo, tamaño, etc) 

`Path.suffix` — la última parte de la ruta que queda separada por un punto. Por ejemplo, si la ruta es: `“/my/library/setup.py”`, devolverá `“.py”`

`Path.parent` — el padre lógico de la ruta. Por ejemplo, si la ruta es `“/a/b/c”`, devolverá `“/a/b”` 

Ejemplo:

```python
from pathlib import Path 
 
ruta = Path.cwd() 
print("Ruta actual:", ruta) 
 
# Crear carpeta ejercicios si no existe 
carpeta_ejer = ruta / "ejercicios" 
if not carpeta_ejer.exists(): 
    carpeta_ejer.mkdir() 
    print("Carpeta 'ejercicios' creada.") 
```

[SHUTIL](https://docs.python.org/es/3.13/library/shutil.html) 

Permite copiar, mover o eliminar archivos y carpetas fácilmente. 

Funciones importantes:

`shutil.copy('origen', 'destino')` — copia un archivo 

`shutil.move('origen', 'destino')` — mueve un archivo 

`shutil.rmtree('carpeta')` — elimina una carpeta 

`shutil.disk_usage('carpeta')` —retorna las estadísticas de uso de disco sobre la ruta de acceso dada como un named tuple con los atributos total, used y free, que son las cantidades del espacio total, el usado y el libre, en bytes. 'carpeta' puede ser un archivo o un directorio. 

Ejemplo:

```python
import shutil 
from pathlib import Path 
 
origen = Path("backup.zip") 
destino = Path("copias/backup.zip") 
 
# Crear carpeta destino si no existe 
destino.parent.mkdir(exist_ok=True) 
 
if origen.exists(): 
    shutil.copy(origen, destino) 
    print("Backup copiado a carpeta 'copias'.") 
```