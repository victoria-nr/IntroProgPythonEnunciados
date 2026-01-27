# Recordatorio: `Path` (pathlib) para trabajar con rutas y ficheros y glob/rglob

En Python, `pathlib` nos permite manejar rutas (carpetas y ficheros) de forma cómoda y **multiplataforma**.  
La clase principal es `Path`.

```python
from pathlib import Path

ruta = Path("logs")        # ruta relativa
ruta_abs = Path.cwd()      # ruta absoluta al directorio actual
```

---

## 1) Comprobar si existe y qué tipo de ruta es

### `exists()`
Sirve para comprobar si una ruta (archivo o directorio) **existe**.

```python
from pathlib import Path

p = Path("config.txt")

if p.exists():
    print("Existe")
else:
    print("No existe")
```

### `is_file()`
Comprueba si la ruta existe y además es un **archivo**.

```python
p = Path("config.txt")

if p.is_file():
    print("Es un archivo")
```

### `is_dir()`
Comprueba si la ruta existe y además es un **directorio** (carpeta).

```python
p = Path("logs")

if p.is_dir():
    print("Es un directorio")
```

> ✅ Consejo: lo normal es usar `exists()` si solo te importa “existe o no”, y `is_file()` / `is_dir()` cuando te importa el tipo.

---

## 2) Leer y escribir texto con `read_text()` y `write_text()`

Estas dos funciones son muy prácticas para **ficheros de texto**.

### `read_text()`
Lee el contenido completo del fichero y te devuelve un **string**.

```python
from pathlib import Path

p = Path("mensaje.txt")

texto = p.read_text(encoding="utf-8")
print(texto)
```

### `write_text()`
Escribe un string en el fichero.

```python
from pathlib import Path

p = Path("mensaje.txt")
p.write_text("Hola\nEsto es una prueba\n", encoding="utf-8")
```

⚠️ Importante: `write_text()` **sobrescribe** el contenido anterior.  
Si quieres **añadir al final** (append), lo normal es abrir el fichero en modo `"a"` con `open()`.

---

## 3) ¿Diferencia entre `read_text()/write_text()` y `read()/write()`?

### A) `read_text()` / `write_text()` (Path)
- Son métodos de `Path`.
- Están pensados para **texto**.
- Son rápidos para tareas sencillas: “leer todo” o “escribir todo”.
- **No** trabajan línea a línea directamente: leen/escriben el contenido completo.

### B) `read()` / `write()` (del archivo abierto)
`read()` y `write()` son métodos del **objeto fichero** que obtienes al abrir un archivo con `open()`:

```python
with open("mensaje.txt", "r", encoding="utf-8") as f:
    texto = f.read()  # esto es read() del objeto fichero

with open("mensaje.txt", "w", encoding="utf-8") as f:
    f.write("Hola\n")  # write() del objeto fichero
```

✅ ¿Cuándo conviene `open()` con `read()/write()`?
- Cuando quieres:
  - Leer **línea a línea** (más eficiente con archivos grandes).
  - Escribir en modo **append** (`"a"`).
  - Controlar mejor lo que haces (por ejemplo, procesar el archivo mientras lo lees).

Ejemplo: leer línea a línea:

```python
from pathlib import Path

p = Path("logs.txt")

with p.open("r", encoding="utf-8") as f:
    for linea in f:
        print(linea.rstrip())
```

> 🧠 Resumen rápido  
> - **Pequeño y simple** → `read_text()` / `write_text()`  
> - **Grande / línea a línea / append** → `open()` + `read()`/`write()` o recorrer `for linea in f`

---

## 4) Buscar ficheros por patrón: `glob()` y `rglob()`

Muchas tareas de sysadmin empiezan con:  
> “Encuentra todos los ficheros que cumplan un patrón…”

Ahí es donde `glob` es muy útil.

### `glob(patrón)`
Busca dentro de **una carpeta** (no recursivo).

```python
from pathlib import Path

carpeta = Path("logs")

for fichero in carpeta.glob("*.log"):
    print(fichero.name)
```

Ejemplos de patrones comunes:
- `"*.txt"` → todos los `.txt`
- `"backup_*.zip"` → backups que empiezan por `backup_` y acaban en `.zip`
- `"*.log.*"` → logs rotados tipo `auth.log.1`, `syslog.log.2`, etc.

---

### `rglob(patrón)`
Busca dentro de la carpeta **y sus subcarpetas** (recursivo).

```python
from pathlib import Path

base = Path("configs")

for fichero in base.rglob("*.conf"):
    print(fichero)
```

> ✅ `rglob()` es equivalente a decir “busca por todo el árbol de directorios”.

---

## 5) Ejemplos prácticos de sysadmin con `glob/rglob`

### A) Contar ficheros `.log`
```python
from pathlib import Path

carpeta = Path("logs")
contador = 0

for _ in carpeta.glob("*.log"):
    contador += 1

print("Logs encontrados:", contador)
```

### B) Guardar un listado de `.conf` encontrados
```python
from pathlib import Path

base = Path("configs")
rutas = []

for fichero in base.rglob("*.conf"):
    rutas.append(str(fichero))

Path("conf_list.txt").write_text("\n".join(rutas) + "\n", encoding="utf-8")
print("Listado generado en conf_list.txt")
```

### C) Mostrar tamaño de ficheros encontrados
```python
from pathlib import Path

carpeta = Path("logs")

for fichero in carpeta.glob("*.log"):
    tam = fichero.stat().st_size
    print(f"{fichero.name} -> {tam} bytes")
```

---

## 6) Mini-guía: errores típicos

- **La carpeta no existe**: comprueba con `exists()` antes de hacer `glob()` o `rglob()`.
- **El patrón no encuentra nada**: puede que no haya ficheros que coincidan o estés en otra ruta.
- **Rutas relativas**: recuerda que dependen del directorio desde el que ejecutas el programa.
  - Puedes imprimir `Path.cwd()` para comprobar dónde estás.

```python
from pathlib import Path
print("Estoy en:", Path.cwd())
```
