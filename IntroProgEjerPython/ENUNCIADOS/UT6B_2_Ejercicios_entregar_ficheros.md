# UT6B_2: Ejercicios entregables ficheros


## Ejercicio 1
Genera un informe `system_report.txt` con la fecha/hora actual, el sistema operativo detectado (`platform`) y el número de CPUs (`os.cpu_count()`).

## Ejercicio 2
Crea (si no existe) un fichero `admin_log.txt` y añade una línea con fecha/hora (`datetime`) y un mensaje pedido por teclado. No debe borrar el contenido anterior.

## Ejercicio 3
Lee `admin_log.txt` y muestra cuántas líneas contiene y cuál es la última línea (si existe).

## Ejercicio 4
Crea `paths.txt` con varias rutas (una por línea). Luego lee el fichero y crea `paths_status.txt` indicando para cada ruta si existe y si es archivo o directorio (usa `pathlib`).

## Ejercicio 5
Simula una configuración en `service.conf` guardando en el fichero líneas `clave=valor`. Léelo y crea un diccionario. Luego pregunta una clave por teclado y muestra su valor o un mensaje si no existe.

## Ejercicio 6
Pide al usuario un nombre de usuario (por ejemplo `rafa`) y guarda en `users.txt` el nombre y su ruta HOME estimada (en Linux `/home/<usuario>`) usando `pathlib`. Si el usuario ya estaba, no lo repitas.

## Ejercicio 7
Lee `users.txt` y crea `homes_check.txt` que indique si la carpeta HOME de cada usuario existe (usa `pathlib`).

## Ejercicio 8
Crea `commands.txt` con comandos típicos (texto). Por ejemplo `ls -la`, `df -h`, `uname -a`, etc. Luego lee el fichero y genera `commands_numbered.txt` numerando cada línea (usa `enumerate`).

## Ejercicio 9
Crea `cleanup_plan.txt` con una lista de carpetas temporales (una por línea). Genera `cleanup_report.txt` indicando cuáles existen y cuántos elementos contienen (usa `pathlib.iterdir()` y recuento).

## Ejercicio 10
Programa que recibe por `sys.argv` el nombre de un fichero de texto. Debe imprimir el número de líneas, palabras y caracteres del fichero (si no existe, mostrar un error amigable).

## Ejercicio 11
Crea `daily_backup_list.txt` con nombres de ficheros a “respaldar”. Genera `backup_commands.txt` con una línea por cada fichero simulando un comando `cp origen destino` (solo texto).

## Ejercicio 12
Lee `system_report.txt` y crea `system_report_history.txt` añadiendo (append) una copia del informe separada por una línea de guiones.

## Ejercicio 13
En la carpeta `logs/`, muestra por pantalla el nombre de todos los ficheros que terminen en `*.log` usando `Path.glob()`. (Para probar el ejercicio, deberás crear primero la carpeta `logs/` con ficheros con distintas extensiones: `.log`, `.txt`, `.py`, etc)

## Ejercicio 14
Cuenta cuántos ficheros `*.txt` hay dentro de `logs/` (solo esa carpeta) y muestra el total.

## Ejercicio 15
Busca `*.log` en `logs/` y muestra por pantalla: `nombre - tamaño_en_bytes` usando `path.stat().st_size`.