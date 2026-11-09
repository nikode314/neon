# Neon
- Lenguaje de programación Neon creado por Nikode.
- Sigue en desarrollo. Sintaxis sencilla y un único ejecutable.

# Comandos de Neon (0.1, actual):
## 1. Variables

| Comando | Función |
|---|---|
| `var nombre = valor` | Crea una variable. |
| `preguntar nombre/tex/"texto opcional"` | Solicita un texto al usuario. |
| `preguntar nombre/num/"texto opcional"` | Solicita un número. |
| `preguntar nombre/vof/"texto opcional"` | Solicita un booleano (`verdadero` o `falso`). |

### Tipos de variables
- `tex`: texto.
- `num`: números.
- `vof`: valores booleanos.

`preguntar` admite un mensaje personalizado entre comillas o una variable `tex` como mensaje.

## 2. Mostrar información

| Comando | Función |
|---|---|
| `decir "Hola"` | Imprime texto y salta de línea. |
| `decir variable` | Muestra el contenido de una variable. |
| `decirl "Hola"` | Imprime texto sin saltar de línea. |
| `decirl variable` | Muestra una variable sin saltar de línea. |

## 3. Condiciones

| Comando | Función |
|---|---|
| `cuando variable:` | Ejecuta el bloque si la variable `vof` es verdadera. |
| `cuando no variable:` | Ejecuta el bloque si la variable `vof` es falsa. |
| `si a == b:` | Ejecuta el bloque si ambos valores son iguales. |
| `no a == b:` | Ejecuta el bloque si ambos valores son distintos. |
| `fin` | Cierra un bloque condicional. |

## 4. Control y utilidades

| Comando | Función |
|---|---|
| `esperar numero` | Pausa la ejecución durante los segundos indicados. |
| `lmp` | Limpia la terminal. |
| `sal` | Termina la ejecución del intérprete. |
| `: comentario` | Añade un comentario que no se ejecuta. |

## 5. Ejecución

| Comando | Función |
|---|---|
| `archivo.ne` | Ejecuta un archivo de Neon. |
| `--version` | Muestra la versión del intérprete. |

## 6. Características adicionales

- `|` permite separar varias instrucciones en una misma línea.
- Los bloques condicionales pueden anidarse.
- Las variables conservan sus valores entre las repeticiones del archivo.
- El intérprete admite hasta 531 ejecuciones del archivo.
- No tiene REPL, solo lee archivos .ne.
- Anteriormente dicho, solo lee los archivos que terminan en .ne.
- Solo hay un ejecutable de Windows (.exe), no hay ejecutables de Linux, pero puedes intentar con Wine.
- Hay una variable vof llamada "inicio", que viene activada desde el principio.
- El archivo .ne se ejecutará hasta tener 531 ejecuciones, el máximo.

---

# Ejemplos
```
::Terminal.
cuando inicio:
    decir "Terminal Neon"
    var promt = ": "
    var inicio = falso
    var consola = verdadero
    var version = "0.0.1"
fin

cuando consola:
    preguntar comando/tex/promt
    si comando == "limpiar":
        lmp
    fin

    no comando == "limpiar":
        si comando == "salir":
            sal
        fin

        no comando == "salir":
            si comando == "decir":
                preguntar dicho/tex/"Qué Quieres Decir: "
                decir dicho
            fin

            no comando == "decir":
                si comando == "cambiar":
                    decir "Promt Nuevo:"
                    preguntar promt/tex/""
                fin

                no comando == "cambiar":
                    si comando == "version":
                        decirl "Neon Versión: "| decir version
                    fin

                    no comando == "version":
                        si comando == "esperar":
                            preguntar espera/num/"Cuanto Quieres Esperar: "
                            esperar espera
                        fin
                        
                        no comando == "esperar":
                            decir "Error: Comando No Existente."
                        fin
                    fin
                fin
            fin
        fin
    fin
fin

```

```
decir "Hola Mundo"
```

# Feliz Jueves.
