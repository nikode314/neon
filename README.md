# Neon
- Lenguaje de programación Neon creado por Nikode.
- Sigue en desarrollo. Sintaxis sencilla y un único ejecutable.

# Comandos de Neon (0.2, actual):
## 1. Variables

| Comando | Función  |
|---|---|
| `var nombre = valor` | Crea una variable. |
| `preguntar nombre tex "texto"` | Solicita un texto al usuario con el promt "texto". |
| `preguntar nombre num "texto"` | Solicita un número con el promt "texto". |
| `preguntar nombre vof "texto"` | Solicita un booleano (`verdadero` o `falso`) con el promt "texto". |
| `preguntar nombre tipo_de_variable variable` | Utiliza el contenido de una variable `tex` como mensaje de entrada. |
| `preguntar nombre tipo_de_variable` | También se puede hacer sin texto. |
| `sumar var1, va2` | Suma la primera variable num con la segunda variable o número. |
| `quitar variable tipo` | Elimina la variable escrita. |

### Tipos de variables
| Nombre | Valoe |
|---|---|
| `tex` | texto. |
| `num` | número. |
| `vof` | booleano. |

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
| `si a == b:` | Ejecuta el bloque si ambos valores son iguales (Solo usan las variables `tex`, `num`, texto entre comillas ("") y numero decimales o enteros). |
| `no a == b:` | Ejecuta el bloque si ambos valores son distintos. |
| `fin` | Cierra un bloque condicional. |

## 4. Control y utilidades

| Comando | Función |
|---|---|
| `esperar numero` | Pausa la ejecución durante los segundos indicados. |
| `lmp` | Limpia la terminal. |
| `sal` | Termina la ejecución del intérprete. |
| `:` | Añade un comentario que no se ejecuta. |
| `pasar` | No hace nada. |


## 5. Ejecución

| Comando | Función |
|---|---|
| `archivo.ne` | Ejecuta un archivo de Neon. |
| `--version` | Muestra la versión del intérprete. |

## 6. Variables Por Defecto
| Comando | Funcion |
|---|---|
| `inicio` | Es una variable que viene por defecto activada. (`vof`) |
| `maxe` | Define  cual es el maximo de ejecuciones, por defecto es 531. (`num`) |
| `eje` | Cuenta las ejecuciones hechas. (No-Editable, `num`) |

## 7. Características adicionales

- `|` permite separar varias instrucciones en una misma línea, pero cada `|` se intepreta como una linea didferente.
- Los bloques condicionales pueden anidarse.
- Las variables conservan sus valores entre las repeticiones del archivo.
- El intérprete admite hasta 531 ejecuciones del archivo.
- No tiene REPL, solo lee archivos .ne.
- Anteriormente dicho, solo lee los archivos que terminan en .ne.
- Solo hay un ejecutable de Windows (.exe), no hay ejecutables de Linux, pero puedes intentar con Wine.

---

# Ejemplos
```
::Terminal.
cuando inicio:
    decir "Terminal Neon"
    var promt = ": "
    var inicio = falso
    var consola = verdadero
    var version = "0.0.2"
    var sae = falso
fin

cuando consola:
    preguntar comando tex promt
    si comando == "limpiar":
        lmp
    fin

    no comando == "limpiar":
        si comando == "salir":
            sal
        fin

        no comando == "salir":
            si comando == "decir":
                preguntar dicho tex "Qué Quieres Decir: "
                decir dicho
            fin

            no comando == "decir":
                si comando == "cambiar":
                    decir "Promt Nuevo:"
                    preguntar promt tex
                fin

                no comando == "cambiar":
                    si comando == "version":
                        decirl "Neon Versión: "| decir version
                    fin

                    no comando == "version":
                        si comando == "esperar":
                            preguntar espera num "Cuanto Quieres Esperar: "
                            esperar espera
                        fin
                        
                        no comando == "esperar":
                            si comando == "":
                                pasar
                            fin

                            no comando == "":
                                si comando == "ayuda":
                                    decir "Lista De Comandos:"| decir ""
                                    decir "limpiar"
                                    decir "salir"
                                    decir "decir"
                                    decir "cambiar"
                                    decir "version"
                                    decir "esperar"
                                    decir "ayuda"
                                fin

                                no comando == "ayuda":
                                    decirl "Error: Comando ""| decirl comando| decir "" No Existente."
                                fin
                            fin
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
sal
```
salida esperada:

`Hola Mundo`

```
cuando inicio:
    var maxe = 33
    var inicio = falso
    var hola = verdadero
    var adios = falso
fin

cuando hola:
    decir "ola"
fin

si eje == 2:
    var hola = falso
    var adios = verdadero
fin

cuando adios:
    decir "pasa"
    si eje == 3:
        sal
    fin
fin
```
salida esperada:

`ola
ola
pasa
pasa
`

`
cuando inicio:
    var maxe = 100000000000000000000000000000
    var x = 0
    var y = 1
    var inicio = falso
    var hola = verdadero
fin

cuando hola:
    sumar x, y
    decir x
fin

si x == 2:
    var hola = falso
    var x = 0
    decir "completado"
    sal
fin
`
salida esperada:

`
1.0
2.0
completado
`

# Feliz Jueves.
