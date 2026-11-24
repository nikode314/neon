# Neon
- Lenguaje de programación Neon creado por Nikode.
- Sigue en desarrollo. Sintaxis sencilla y un único ejecutable.

# Comandos de Neon (0.4, actual):
## 1. Variables

| Comando | Función  |
|---|---|
| `var nombre = "texto"` | Crea una variable de texto. |
| `var nombre = numero` | Crea una variable de numeros decimales. |
| `var nombre = falso` | Crea una variable bool falsa. |
| `var nombre = verdadero` | Crea una variable bool verdadera. |
| `var nombre = otra_variable` | Crea una variable con el valor de otra variable. |
| `preguntar nombre tex "texto"` | Solicita un texto al usuario con el promt "texto". |
| `preguntar nombre num "texto"` | Solicita un número con el promt "texto". |
| `preguntar nombre vof "texto"` | Solicita un booleano (`verdadero` o `falso`) con el promt "texto". |
| `preguntar nombre tipo_de_variable variable` | Utiliza el contenido de una variable `tex` como mensaje de entrada. |
| `preguntar nombre tipo_de_variable` | También se puede hacer sin texto. |
| `sumar var1, va2` | Suma la primera variable num con la segunda variable o número. |
| `sumar var1, doble` | Suma el doble de var1. |
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
| `decir "texto"` | Imprime texto y salta de línea. |
| `decir variable` | uestra el valor de una variable y salta de línea. |
| `decirl "texto"` | Imprime texto sin saltar de línea. |
| `decirl variable` | Muestra el valor de una variable sin saltar de línea. |
| `"texto"` | Imprime texto y salta de línea. |
| `variable` | Muestra el valor de una variable y salta de línea.

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
| `esperar numero` | Pausa la ejecución durante los segundos indicados, puedes usar numeros o variables num. |
| `lmp` | Limpia la terminal. |
| `sal` | Termina la ejecución del intérprete. |
| `<Comentario>` | Añade un comentario que no se ejecuta. |
| `pasar` | No hace nada. |
| `titulo "algo"` | Cambia el titulo de la ventana, puedes usar comillas o una variable tex. |
| `final` | Hace una pausa infinita. |
| `error "mensaje de error"` | Muestra un mensaje de error con el texto puesto. |
| `error variable_tex` | Muestra un mensaje de error con el texto de la variable. |

## 5. Ejecución

| Comando | Función |
|---|---|
| `archivo.ne` | Ejecuta un archivo de Neon. |
| `--version` | Muestra la versión del intérprete. |
| `--ayuda` | Muestra los comandos disponibles. |

## 6. Variables Por Defecto
| Comando | Funcion |
|---|---|
| `inicio` | Es una variable que viene por defecto activada. (`vof`) |
| `maxe` | Define  cual es el maximo de ejecuciones, por defecto es 531. (`num`) |
| `eje` | Cuenta las ejecuciones hechas. (No-Editable, `num`) |

## 7. Características adicionales

- Puedes poner los comandos en mayusculas (ej. DECIR "hola").
- Los bloques condicionales pueden anidarse.
- Las variables conservan sus valores entre las repeticiones del archivo.
- El intérprete admite hasta 531 ejecuciones del archivo.
- No tiene REPL, solo lee archivos .ne.
- Anteriormente dicho, solo lee los archivos que terminan en .ne.
- Solo hay un ejecutable de Windows (.exe), no hay ejecutables de Linux, pero puedes intentar con Wine.

---

# Ejemplos
```
<Terminal.>
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
                        decirl "Neon Versión: "
                        decir version
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
                                    decir "Lista De Comandos:"
                                    decir ""
                                    decir "limpiar"
                                    decir "salir"
                                    decir "decir"
                                    decir "cambiar"
                                    decir "version"
                                    decir "esperar"
                                    decir "ayuda"
                                fin

                                no comando == "ayuda":
                                    decirl "Error: Comando ""
                                    decirl comando
                                    decir "" No Existente."
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

```
Hola Mundo
```

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

```
ola
ola
pasa
pasa
``` 

```
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
```
salida esperada:

```
1.0
2.0
completado
```

```
<Nuevo Tipo De Variable (bin).>

cuando inicio:
    var encendido = falso
    var inicio = falso
fin

preguntar bin tex "Nuevo tipo de variable, bin (0/1): "
si bin == "1":
    cuando encendido:
        decir "Ya Estaba Encendido."
    fin
    cuando no encendido:
        decir "Encendido."
        var encendido = verdadero
    fin
fin

si bin == "0":
    cuando no encendido:
        decir "Ya Estaba Apagado."
    fin
    cuando encendido:
        decir "Apagado."
        var encendido = falso
    fin
fin

no bin == "0":
    no bin == "1":
        error "Tipo de variable incorreto."
        sal
    fin
fin
```

# Feliz Jueves.
