# UT2: ¿Qué es la Programación Orientada a Objetos (POO)?

Aunque en este curso no vamos a programar usando POO (Programación Orientada a Objetos), sí es importante que entiendas qué es y por qué ya la estás usando sin darte cuenta.

En Python, todo es un **objeto**. Eso significa que los datos (como números, cadenas, listas, etc.) no solo contienen un valor, sino también un 'comportamiento' asociado a través de **métodos**. Por ejemplo, una cadena de texto no es solo texto: es un objeto de la **clase** 'str', y tiene **métodos** que puedes usar para modificar o analizar ese texto. En resumen:

- **Clase**: es un molde o plantilla que define cómo serán los objetos, especificando sus **atributos** (datos) y **métodos** (funciones que expresan comportamientos).
- **Objeto**: es una instancia concreta creada a partir de una clase, con sus propios valores para los atributos definidos en ella.
  
Por ejemplo, la clase *Persona* puede definir que toda persona tiene un nombre y una edad; a partir de ella se crean objetos concretos como *Ana, 25 años* o *Luis, 30 años*. De igual forma, la clase *Coche* define atributos como marca y modelo y un método para arrancar, y de ella pueden surgir objetos como un *Toyota Corolla* o un *Tesla Model 3*.

Aunque no vayamos a escribir nuestras propias clases u objetos, en Python ya estamos usando objetos todo el tiempo que pertenecen a clases predefinidas. Las cadenas, listas, números… todos son objetos con funcionalidades que podemos usar gracias a los métodos que definen su comportamiento.

Cuando escribimos algo como:

```python
    mensaje = "Hola mundo"
    mensaje.upper()
```

Estamos usando un método llamado `.upper()` que transforma el texto a mayúsculas. Ese método está definido dentro de la clase `str`, que es la clase de todas las cadenas en Python.

Algunos métodos comunes de las cadenas:

- `upper()`: convierte a mayúsculas
- `lower()`: convierte a minúsculas
- `strip()`: elimina espacios al principio y final
- `replace()`: sustituye partes de una cadena
- `split()`: divide la cadena en partes
  
Si quieres saber más sobre la Programación Orientada a Objetos en Python puedes leer el siguiente [artículo](https://kinsta.com/es/blog/programacion-orientada-objetos-python/).