# UT: Ejercicios de sysadmin con glob (pathlib)

Ejercicios para practicar búsqueda por patrones con `Path.glob()` y `Path.rglob()`.

💡 Consejo: crea carpetas de prueba (`logs`, `configs`, etc.) y algunos ficheros antes de ejecutar.

## Ejercicio 1
En la carpeta `logs/`, muestra por pantalla el nombre de todos los ficheros que terminen en `*.log` usando `Path.glob()`.

## Ejercicio 2
Cuenta cuántos ficheros `*.txt` hay dentro de `datos/` (solo esa carpeta) y muestra el total.

## Ejercicio 3
Busca `*.log` en `logs/` y muestra por pantalla: `nombre - tamaño_en_bytes` usando `path.stat().st_size`.

## Ejercicio 4
Busca en `temp/` ficheros que terminen en `.tmp` o `.bak` y genera un fichero `cleanup_plan.txt` con las rutas encontradas (una por línea). **No borres nada**.

## Ejercicio 5
Dentro de `configs/` (con subcarpetas), busca todos los `*.conf` usando `Path.rglob()` y guarda en `conf_list.txt` su ruta relativa.

## Ejercicio 6
En la carpeta `shared/`, encuentra ficheros cuyo nombre contenga espacios y muestra un aviso por pantalla con el nombre de cada uno.

## Ejercicio 7
En `inventario/`, crea un diccionario donde la clave sea la extensión (`.txt`, `.log`, `.conf`, sin extensión...) y el valor cuántos hay. Usa `glob('*')`. Muestra el diccionario.

## Ejercicio 8
En `logs/`, busca ficheros de logs rotados que encajen con el patrón `*.log.*` y cuenta cuántos hay. Muestra el total.

## Ejercicio 9
Copia todos los `*.conf` encontrados en `configs/` (recursivo) a una carpeta `backup_configs/` (créala si no existe). Usa `shutil.copy2`.

## Ejercicio 10
Comprueba en `proyecto/` si existe al menos: 1 fichero `*.py`, 1 fichero `*.txt` y una carpeta `data/`. Muestra `OK` o qué falta.
