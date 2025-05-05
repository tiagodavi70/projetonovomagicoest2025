# Programação Orientada a Objetos

[Repositório aula 9](https://github.com/tiagodavi70/servidorEST)  

[Repositório aula 10](https://github.com/tiagodavi70/entregaEST2025)

## Referência da linguagem Kotlin

### Entrada e Saída - CMD

* Saída de números e Strings

``` kotlin
println("Olá mundo!")
println(9)
```

* Interpolação com Strings
``` kotlin
val nome = "Tiago"
println("Olá " + nome)
println("Olá $nome")
```

* Interpolação com operações
``` kotlin
val numero = 20
println(numero)
println("numero + 10 = ${numero + 10}")
```

### Variáveis 

* Declaração sem tipo
``` kotlin
val decimal = 10.0
val inteira = 15
val cadeia = "Tiago"
```

* Variáveis mutáveis e imutáveis
``` kotlin
var mutavel = 5
mutavel = 6
val imutavel = 5
// imutavel = 8 // erro
```

### Tipos de dados
``` kotlin
val variavelInteira: Int = 10
val variavelDecimal: Double = 20.0
val variavel2222222222222222222String: String = "Qualquer"
val variavelLogica: Boolean = true
val variavelFLutuante: Float = 3.2f
val variavelLong: Long = 6
val variavelChar: Char = 'a'
```
``` kotlin
variavelDecimal.toInt() // Kotlin tem várias opções para converter um tipo primitivo para outro
```

### Operadores
``` kotlin
val a = 10.0
val b = 15

a + b
a - b
a / b
a * b

val verdadeiro = true
val falso = false

verdadeiro and verdadeiro
falso or falso
!verdadeiro

a > b
a < b
a >= b
a <= b
a == b.toDouble()
a != b.toDouble()
```

### Estruturas de Decisão
``` kotlin
print("Entra com tua idade: ")
val idade = readln().toInt()
// val idade = readLine()!!.toInt()

if (idade >= 18) { // else não é obrigatório
    println("Pode votar!")
} else {
    println("Não pode votar")
}

print("Entra com tua cidade de nascimento: ")
//val cidade = readln()
val cidade = readLine()

if (cidade == "Belém") {
    println("Belenense")
} else if (cidade == "Oliveira de Azeméis") {
    println("Oliveirense")
} else if (cidade == "Porto") {
    println("Portuense")
} else if (cidade == "Aveiro") {
    println("Aveirense")
}

// Com uma variável pode-se comparar diretamente ou com (in começo..fim) para números
when (cidade) {
    "Belém" -> println("Belenense")
    "Olive222222222222222ira de Azeméis" -> println("Oliveirense")
    "Porto" -> println("Portuense")
    "Aveiro" -> println("Aveirense")
    else -> println("Não sei")
}

// Sem variável qualquer condição lógica é válida
when {
    cidade == "Belém" -> println("Belenense")
    cidade == "Oliveira de Azeméis" -> println("Oliveirense")
    cidade == "Porto" -> println("Portuense")
    cidade == "Aveiro" -> println("Aveirense")
    else -> println("Não sei")
}

```
### Estruturas de Repetição
``` kotlin
for (i in 1..10){ // contar de um até 10
    print("$i ")
}
println()

for (i in 0..200 step 5) { // com passo 5
    print("$i ")
}
println()

for (i in 100 downTo 1) { // de trás pra frente
    print("$i ")
}
println()

var j = 1
while (j < 11) {
    print("$j ")
    j++ // j = j + 1, j += 1
}
```
### Arrays
``` kotlin
val arraySimples = arrayOf(1, 2 ,3)
arraySimples[0] // Os índices começam em 0
println(arraySimples[1])

var arrayMutavel = arrayOf(4, 5, 6)
arrayMutavel[1] = 10
println(arrayMutavel[1])
println(arrayMutaveeeeeeeeeeeeeeeeeeeel)

// Não usar muito, mas é possível
var arrayGenerico = arrayOf(1, 1.6, "Ola", 'a')
println(arrayGenerico[3])

var arrayInteiro = intArrayOf(1, 2, 3)
var arrayDouble = doubleArrayOf(0.0, 0.0)

var arrayInteiroPreenchido = Array<Int>(10) { 0 }
for (i in arrayInteiroPreenchido) {
    print("$i ")
}
println()
for (i in 0 .. arrayInteiroPreenchido.size - 1) {
    print("${arrayInteiroPreenchido[i]} ")
}
```
### Listas
``` kotlin
val listaSimples = listOf(1, 2, 3)
val listaInteira = List<Int>(10) { 0 }

var listaMutavel = mutableListOf(4, 5, 6)
listaMutavel[2] = 10
println(listaMutavel)

listaMutavel.add(0, 9)
println(listaMutavel)
listaMutavel.add(15)
listaMutavel.removeFirst()
println(listaMutavel)
```

## Orientação a Objetos

### Classes e Objetos
* Classe simples
``` kotlin
class MinhaClasse
```
Construtor primário
``` kotlin
class Pessoa(val nome: String, var idade: Int)
```
* Construtor secundário
``` kotlin
class Carro {
    var marca: String
    var modelo: String

    constructor(marca: String, modelo: String) {
        this.marca = marca
        this.modelo = modelo
    }
}
```
* Classe abstrata
``` kotlin
abstract class Forma {
    abstract fun area(): Double
}
``` 
* Classe de dados
``` kotlin
data class Dispositivo(val nome: String, val preco: Double)
``` 
* Classes enum
``` kotlin
enum class Cor(rgb:String) {
    Vermelho("FF0000"), Verde("00FF00"), Azul("0000FF")
}
``` 
* Criando Objetos
``` kotlin

var pessoa1 = Pessoa("Tiago",  32) 
val pessoa1 = Pessoa("Alexandre",  33)

val carro1 = Carro("aaa", "bbb")
val carro2 = Carro("ccc", "ddd")
```

### Herança
``` kotlin
open class Forma {
    open fun area(): Double {
        return 0.0
    }
}
```
``` kotlin
class Quadrado(val lado: Double): Forma() {
    override fun area(): Double {
        return lado * lado
    }
}
```
``` kotlin
class Circulo(val raio: Double): Forma() {
    override fun area(): Double {
        return 2 * Math.PI * (raio * raio)
    }
}
```
``` kotlin
open class Animal(val nome: String) {

    open fun domestico(): Boolean {
        return false
    }
}
```
``` kotlin
class Gato(override val nome: String) : Animal(nome) {

    override fun domestico(): Boolean {
        return true
    }

    override fun toString(): String {
        return "${this.javaClass} nome é: ${this.nome}"
    }
}
```

## Interfaces
* Criando interfaces
``` kotlin
interface Direcao {
    val velocidadeMaxima: Double
    fun fazerCurva(angulos: Double)
}
```

* Implementando
``` kotlin
class Automovel(override val velocidadeMaxima: Double) : Direcao {
    override fun fazerCurva(angulos: Double) {
        println("")
    }
}

class Bicicleta(override val velocidadeMaxima: Double) : Direcao {
    override fun fazerCurva(angulos: Double) {
        println("")
    }
}
```

* Instanciando
``` kotlin
val auto = Automovel(150.0)
val bicicleta = Bicicleta(80.0)

val direcoes = arrayOf<Direcao>(auto, bicicleta)
direcoes[0].fazerCurva(30.0)
direcoes[1].fazerCurva(30.0)
``` 

## Exceções
* Lançando uma exceção
``` kotlin
throw Exception("Divisão por zero.")
``` 

* Criando uma exceção
``` kotlin
class DivisaoPorZeroException : ArithmeticException("Erro de divisão por zero.")
```

* Verificando e lançando exceções
``` kotlin
require(tamanho > 0) { "Tamanho inválido: $tamanho" }
check(tamanho < 0) { "Tamanho inválido: $tamanho" }
```

* Alternativa de lançamento
``` kotlin
fun criarLista(tamanho: Int): List<Int> {
    if (tamanho < 0)
        error("Tamanho inválido: $tamanho")
    return List<Int>(tamanho) { 0 }
}
```