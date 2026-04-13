<p align="center">
  <img src="https://github.com/user-attachments/assets/1f551bed-0986-4cf6-a2a9-7708fa182472" width="1411" height="715" />
</p>

## Índice

1. [Variables y Constantes](#1-variables-y-constantes)
2. [Tipos de Variables](#2-tipos-de-variables)
3. [Operadores](#3-operadores)
4. [Condicionales (if / switch)](#4-condicionales-if--switch)
5. [Arreglos](#5-arreglos)
6. [Tuplas, Diccionarios y Nulabilidad](#6-tuplas-diccionarios-y-nulabilidad)
7. [Bucles (for / while)](#7-bucles-for--while)
8. [Funciones](#8-funciones)
9. [Clases y Structs](#9-clases-y-structs)
10. [Ejercicios Prácticos](#10-ejercicios-prácticos)
---

## 1. Variables y Constantes

Imagina que tienes una cajita donde puedes guardar cosas. Eso es exactamente lo que hace una variable: guardar información para usarla después.

En Swift, existen dos tipos de cajitas:

- `var` → La cajita puede cambiar de contenido cuando quieras.
- `let` → La cajita está sellada. Una vez que guardas algo, ya no puedes cambiarlo. A esto se le llama **constante**.

### ¿Cómo se ve una variable?

Se divide en tres partes:
- 📦 `var / let` — Le dice a Swift: *¡Voy a crear una cajita!*
- 👩🏻‍💻 `nombre` — Es el nombre con el que vas a identificar tu cajita.
- 📄 `valor` — Es lo que vas a guardar dentro de la cajita.

```swift
var nombre = "Fernanda García"   // ✅ Se puede cambiar
let nombre2 = "Karina Silva"     // 🔒 No se puede cambiar (constante)

print(nombre)   // Imprime: Fernanda García
```

> [!NOTE]
> La función `print()` sirve para mostrar el contenido de una variable en la pantalla. ¡Es como pedirle a Swift que te diga qué hay dentro de la cajita!

> [!TIP]
> **Buena práctica:** Usa `let` siempre que puedas. Solo usa `var` cuando sepas que el valor va a cambiar. Esto hace tu código más seguro.

---

## 2. Tipos de Variables

Las cajitas no son todas iguales. Dependiendo de lo que quieras guardar, necesitas un tipo diferente. Swift es muy estricto con esto: ¡no puedes guardar un número en una cajita de texto!

### `Character` — Un solo carácter

Solo acepta **UN** carácter: una letra, un número o un símbolo.

```swift
var simbolo: Character = "e"
var corazon: Character = "\u{2665}"   // Símbolo especial: ♥
print(corazon)   // Imprime: ♥
```

### `String` — Texto

Puede guardar cualquier texto: letras, números, símbolos, frases enteras.

```swift
var nombrePerro: String = "Robin"
```

### `Int` — Número entero

Para números sin decimales: 1, 42, -100, 2026.

```swift
var año: Int = 2026
```

### `Float` — Número con decimales (básico)

Ocupa menos espacio en memoria pero es menos preciso. Soporta hasta ~7 decimales.

```swift
var piFlat: Float = 3.1416   // Swift lo redondea un poco
print(piFlat)
```

### `Double` — Número con decimales (preciso)

Más preciso que `Float`. Usa este cuando necesites decimales con mucha exactitud.

```swift
var piDouble: Double = 3.14162738932832
print(piDouble)
```

### `Bool` — Verdadero o Falso

Solo tiene dos posibles valores: `true` (verdadero) o `false` (falso). Como un interruptor de luz 💡.

```swift
var estaFeliz: Bool = true
var estaTriste: Bool = false
```

### Conversión de tipos

Swift **no mezcla tipos automáticamente**. Si quieres sumar un `Int` con un `Double`, debes convertirlos explícitamente.

```swift
let numeroEntero: Int = 34
let numeroDecimal: Double = 25.65

// ❌ Esto da error:
// let suma = numeroEntero + numeroDecimal

// ✅ Esto funciona (convertimos el Int a Double):
let suma: Double = Double(numeroEntero) + numeroDecimal
print(suma)   // 59.65
```

---

## 3. Operadores

### Operadores Aritméticos

Son como las operaciones matemáticas de siempre.

```swift
var a: Int = 5
var b: Int = 6

var suma        = a + b    // 11  → Suma
var resta       = a - b    // -1  → Resta
var multiplicar = a * b    // 30  → Multiplicación
var division    = b / 2    // 3   → División entera
var modulo      = a % b    // 5   → Residuo (lo que sobra)
```

> [!TIP]
> El módulo `%` te da el residuo de una división. Por ejemplo: `10 % 3 = 1`, porque 10 ÷ 3 = 3 y sobra 1. Es muy útil para saber si un número es par (si `num % 2 == 0`, entonces es par).

### Operadores de Asignación

Son atajos para modificar una variable de forma más rápida.

```swift
var ejemplo = 5

ejemplo = ejemplo + 10   // Forma larga
ejemplo += 10            // Forma corta (igual que arriba) ✅

ejemplo -= 5    // Resta 5
ejemplo *= 2    // Multiplica por 2
ejemplo /= 4    // Divide entre 4
ejemplo %= 3    // Guarda el residuo de dividir entre 3
```

### Operadores de Comparación

Comparan dos valores y devuelven `true` o `false`.

```swift
let edad = 20

let esMayor    = edad > 18    // true  → Mayor que
let esMenor    = edad < 18    // false → Menor que
let esIgual    = edad == 20   // true  → Igual que
let esDistinto = edad != 20   // false → No es igual
let menorIgual = edad <= 18   // false → Menor o igual
let mayorIgual = edad >= 18   // true  → Mayor o igual
```

### Operadores Lógicos

Combinan condiciones: ambas deben ser verdaderas, o al menos una.

```swift
let estaSoleado = true
let temperatura: Int = 25

// && = AND (ambas deben ser true)
let esAgradable: Bool = estaSoleado && temperatura > 25   // false

// || = OR (al menos una debe ser true)
let irPlaya: Bool = estaSoleado || temperatura > 24       // true

// ! = NOT (invierte el valor)
let llevarSombrero: Bool = !estaSoleado   // false
```

---

## 4. Condicionales (if / switch)

Los condicionales le permiten a tu código tomar decisiones. En lugar de ejecutar todo de arriba hacia abajo, el programa puede elegir qué hacer dependiendo de una situación.

### `if` / `else if` / `else`

```swift
let edadUsuario = Int.random(in: 1...30)   // Número aleatorio del 1 al 30

if edadUsuario >= 18 {
    print("Eres mayor de edad (\(edadUsuario))")
} else {
    print("Eres menor de edad (\(edadUsuario))")
}
```

Encadenando varias condiciones con `else if`:

```swift
func saludo(_ hora: Int) {
    if hora < 12 {
        print("Buenos días")
    } else if hora < 18 {
        print("Buenas tardes")
    } else {
        print("Buenas noches")
    }
}
saludo(18)   // Imprime: Buenas noches
```

> [!TIP]
> Dentro de un texto, usamos `\(nombreVariable)` para insertar el valor de una variable. Es como un hueco en la oración que Swift llena automáticamente.

### `switch` — El semáforo de múltiples opciones

Cuando tienes muchas opciones posibles, el `switch` es más limpio y legible que un montón de `else if`.

```swift
func mesConSwitch(_ mes: Int) {
    switch mes {
    case 1:  print("Enero")
    case 2:  print("Febrero")
    case 3:  print("Marzo")
    // ... etc
    case 12: print("Diciembre")
    default: print("Mes inválido")
    }
}
mesConSwitch(3)   // Imprime: Marzo
```

### `switch` con grupos de casos

```swift
func trimestre(_ mes: Int) {
    switch mes {
    case 1, 2, 3:    print("Primer Trimestre")
    case 4, 5, 6:    print("Segundo Trimestre")
    case 7, 8, 9:    print("Tercer Trimestre")
    case 10, 11, 12: print("Cuarto Trimestre")
    default:         print("Mes inválido")
    }
}
trimestre(8)   // Imprime: Tercer Trimestre
```

### `switch` con rangos

```swift
func rango(_ numero: Int) {
    switch numero {
    case 1...10:    print("Entre 1 y 10")
    case 11...1000: print("Entre 11 y 1000")
    default:        print("Fuera de rango")
    }
}
```

---

## 5. Arreglos

Un arreglo (`Array`) es como una lista de cosas del mismo tipo, ordenadas en fila. Cada elemento tiene una posición llamada **índice**, que empieza desde **0**.

```swift
let nombres: [String] = ["Mafer", "Karina", "Abraham", "Jair"]
//                          0        1          2          3    ← posiciones

print(nombres)      // ["Mafer", "Karina", "Abraham", "Jair"]
print(nombres[1])   // Karina  ← Posición 1
```

### Modificar elementos

```swift
var diasSemana: [String] = ["Lunes", "Martes", "Miércoles",
                             "Jueves", "Viernes", "Sábado", "Domingo"]

diasSemana[4] = "Bebiernes"   // Cambiamos "Viernes" por "Bebiernes" 🍻
print(diasSemana[4])           // Bebiernes
```

### Agregar y eliminar

```swift
// Agregar al final
diasSemana.append("Día de San Mafer")

// Eliminar un elemento por posición
diasSemana.remove(at: 0)   // Elimina "Lunes"

// Eliminar todos los elementos
// diasSemana.removeAll()
```

> [!WARNING]
> Si intentas acceder a una posición que no existe, tu programa crasheará. ¡Siempre verifica que el índice exista!

---

## 6. Tuplas, Diccionarios y Nulabilidad

### Tuplas — El combo de valores

Una tupla es como una cajita que guarda varios valores juntos, aunque sean de tipos diferentes.

```swift
// Tupla por posición
let persona = ("Mafer", 20, true, "Calle mi casa")
print(persona.0)   // Mafer
print(persona.1)   // 20
```

La forma más recomendada es usar **etiquetas**:

```swift
// Tupla etiquetada ✅
let usuario = (nombre: "Elena", edad: 25, esPremium: true)
print(usuario.nombre)     // Elena
print(usuario.esPremium)  // true
```

También puedes desempacar los valores directamente:

```swift
let (nombre, edad) = ("Carlos", 40)
print(nombre)   // Carlos
```

### Diccionarios — El catálogo clave-valor

Un diccionario es como un diccionario real 📖: buscas una palabra (la **clave**) y encuentras su definición (el **valor**).

```swift
var capitales = ["Francia": "París", "Italia": "Roma", "Japón": "Tokio"]

// Acceder a un valor
print(capitales["Francia"])   // Optional("París")

// Agregar o actualizar
capitales["México"] = "CDMX"

// Eliminar
capitales["Italia"] = nil

// Recorrer todos los pares
for (pais, capital) in capitales {
    print("La capital de \(pais) es \(capital)")
}
```

### Nulabilidad y Opcionales

En Swift, una variable normal **nunca** puede ser `nil`. Para eso existen los **Opcionales**, que se declaran con `?` al final del tipo.

```swift
var apodo: String? = nil   // Puede ser texto O puede no tener nada
print(apodo)               // nil
```

#### El operador `??` (valor por defecto)

```swift
print(apodo ?? "Sin apodo")   // Sin apodo  ← porque apodo es nil
```

#### `if let` — Desempacar con seguridad

```swift
if let valorReal = apodo {
    print("El apodo es: \(valorReal)")   // Solo entra aquí si no es nil
} else {
    print("No tiene apodo")
}
```

#### `guard let` — Salir si es nil

```swift
func procesarApodo(_ texto: String?) {
    guard let valorSeguro = texto else {
        return   // Salimos si es nil
    }
    print("Apodo: \(valorSeguro)")
}
```

> [!WARNING]
> Puedes usar `variable!` para decirle a Swift *"¡yo sé que hay valor aquí!"*. Pero si en realidad es `nil`, tu app se va a caer. Úsalo solo cuando estés 100% seguro.

---

## 7. Bucles (for / while)

Un bucle (o ciclo) sirve para **repetir una acción varias veces** sin tener que escribir el mismo código una y otra vez.

### `for` — El bucle contador

```swift
for i in 1...7 {
    print("Hola")   // Se imprime 7 veces
}
```

Recorriendo un arreglo:

```swift
var diasSemana: [String] = ["Lunes", "Martes", "Miércoles",
                             "Jueves", "Viernes", "Sábado", "Domingo"]

for dia in diasSemana {
    if dia == "Jueves" {
        print("El día de hoy es \(dia)")
    }
}
```

### `while` — El bucle condicional

Repite el código mientras una condición sea verdadera.

```swift
var contador = 0

while contador < 10 {
    print("Contador vale: \(contador)")
    contador += 1   // ¡Importante! Si no incrementas → loop infinito 😱
}
```

### `repeat-while` — Primero hago, luego pregunto

El código se ejecuta **al menos una vez**, porque la condición se evalúa al final.

```swift
var cuenta = 5

repeat {
    print("Hola")   // Se ejecuta una vez aunque cuenta no sea < 0
} while cuenta < 0
```

### `break` y `continue`

```swift
for dia in diasSemana {
    if dia == "Jueves" {
        print("¡Encontré el jueves!")
        break      // Para todo el bucle aquí
    } else {
        print("\(dia) no es jueves")
    }
}
```

- `break` → Para el bucle completamente. Sale de él.
- `continue` → Salta al siguiente ciclo sin ejecutar el resto del código actual.

---

## 8. Funciones

Una función es como una **receta de cocina** 🍳. La escribes una vez y la puedes usar todas las veces que quieras.

```swift
func mostrarNombre() {
    print("Hola, soy mi primera función")
}

mostrarNombre()   // Así la llamamos (ejecutamos)
```

### Parámetros de entrada

```swift
func saludar(nombre: String) {
    print("Hola, soy \(nombre)")
}
saludar(nombre: "Mafer")   // Hola, soy Mafer
```

Múltiples parámetros:

```swift
func calcular(a: Int, b: Int) {
    let resultado = a + b
    print("El resultado es: \(resultado)")
}
calcular(a: 10, b: 20)   // El resultado es: 30
```

### El guión bajo `_` — Llamada sin etiqueta

```swift
func calcular2(_ a: Int, _ b: Int) {
    print(a + b)
}
calcular2(40, 20)   // Sin etiquetas ✅ → 60
```

### Parámetros de salida (`return`)

```swift
func calcular3(a: Int, b: Int) -> Int {   // -> Int = devuelve un entero
    let resultado = a + b
    return resultado
}

let superResultado: Int = calcular3(a: 4, b: 7)
print(superResultado)   // 11
```

> **Estructura:** `func nombre(parámetro: Tipo) -> TipoRetorno { código }`

---

## 9. Clases y Structs

### `class` — El molde de objetos

Una clase es como un **molde para galletas**. El molde define la forma, y con él puedes crear todos los objetos que quieras.

```swift
class Persona {
    var nombre: String
    var edad: Int

    // init() es el constructor
    init(nombre: String, edad: Int) {
        self.nombre = nombre   // self = esta instancia en particular
        self.edad = edad
    }

    func saludar() {
        print("Hola, soy \(nombre) y tengo \(edad) años.")
    }
}

var mafer: Persona = Persona(nombre: "Fernanda García", edad: 20)
var karina: Persona = Persona(nombre: "Karina Silva", edad: 21)

mafer.saludar()    // Hola, soy Fernanda García y tengo 20 años.
karina.saludar()   // Hola, soy Karina Silva y tengo 21 años.
```

### `struct` — La versión liviana

```swift
struct EstructuraEjemplo {
    var nombre: String
    var edad: Int
}

var ejemplo = EstructuraEjemplo(nombre: "Fernanda", edad: 20)
print(ejemplo.edad)   // 20
```

| | `struct` | `class` |
|---|---|---|
| **Uso** | Datos simples y concretos | Objetos compartidos entre partes del app |
| **Ejemplo** | `Usuario`, `Producto`, `Coordenada` | `GestorDeBaseDeDatos`, `ControladorDeVista` |

---

## 10. Ejercicios Prácticos

### Ejercicio 1 — Registro de Asistencia

```swift
let asistencias: Int = 20
let totalClases: Int = 40

let porcentaje: Float = (Float(asistencias) / Float(totalClases)) * 100
print("Porcentaje de asistencia: \(porcentaje)%")   // 50.0%
```

### Ejercicio 2 — Calculadora de IMC

```swift
let peso: Float = 50
let altura: Float = 1.65

let imc: Float = peso / (altura * altura)
print("Tu IMC es de: \(imc)")
```

### Ejercicio 3 — Cálculo de Descuento

```swift
let precioOriginal: Float = 1999
let porcentajeDescuento: Float = 20

let precioDescuento = precioOriginal - (precioOriginal * porcentajeDescuento / 100)
print("Precio original: $\(precioOriginal)")
print("Precio con descuento del \(porcentajeDescuento)%: $\(precioDescuento)")
```

### Ejercicio 4 — Área de un Círculo

```swift
func area(_ radio: Float) -> Float {
    return Float.pi * radio * radio   // π × r²
}

let resultado = area(10)
print("El área del círculo es: \(resultado)")   // 314.159...
```

### Ejercicio 5 — ¿Positivo, Negativo o Cero?

```swift
func clasificarNumero(_ num: Int) {
    if num < 0 {
        print("\(num) es negativo")
    } else if num == 0 {
        print("Es cero")
    } else {
        print("\(num) es positivo")
    }
}
clasificarNumero(-2)   // -2 es negativo
```

### Ejercicio 6 — Tabla de Multiplicar

```swift
func tablaMultiplicar(_ numero: Int) {
    for i in 1...10 {
        let mult = numero * i
        print("\(numero) × \(i) = \(mult)")
    }
}
tablaMultiplicar(2)
// 2 × 1 = 2
// 2 × 2 = 4
// ... hasta 2 × 10 = 20
```

### Ejercicio 7 — Suma de números pares del 1 al 100

```swift
var total = 0

for i in 1...100 {
    if i % 2 == 0 {
        total += i
    }
}
print(total)   // 2550
```

### Ejercicio 8 — Contar Vocales

```swift
func contarVocales(_ palabra: String) {
    var totalVocales: Int = 0

    for caracter in palabra {
        switch caracter.lowercased() {
        case "a", "e", "i", "o", "u":
            totalVocales += 1
        default:
            continue
        }
    }
    print("'\(palabra)' tiene \(totalVocales) vocal(es)")
}
contarVocales("hola")   // 'hola' tiene 2 vocal(es)
```
