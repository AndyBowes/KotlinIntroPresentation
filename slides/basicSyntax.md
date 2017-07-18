---?image=assets/images/ingredients.jpeg&size=cover
## Basic Syntax

+++
## Pragmatic language
- Started as JetBrains internal language |
- Kotlin is statically typed |
- Combination of OO & Functional |
- Prefers code clarity over brevity |
- 'Borrows' concepts from multiple sources |
  - Elements from Groovy, Scala, Ceylon, Swift, ...

+++
## Objects Everywhere
- Everything is an object. |
- No 'primitive' types. |
- Data types are very similar to Java |
  - Root class is Any not Object
  - Nothing - null values
  - Unit - void return type

+++
## Basic Data Types
- Numeric Types |
  - Integer : Long, Int, Short, Byte
  - Decimal : Float, Double
- Text Types |
  - Char, String

+++
## Variable Definitions
- Reverse of Java notation
  - variable name followed by type
- var - mutable variable
- val - immutable property

``` Kotlin
val customerName : String = "Andy Bowes"
val customerName = "Andy Bowes"
```
@[1](Explicitly define variable type)
@[2](Variable type is inferred by compiler)

+++
## Numeric Ranges
```
for (i in 1..100) { ... }  
for (i in 1 until 100) { ... }
for (x in 2..10 step 2) { ... }
for (x in 10 downTo 1) { ... }
if (x in 1..10) { ... }
```
@[1](Closed range: includes both 1 & 100)
@[2](Half-open range: excludes 100)
@[3](Custom increment)
@[4](Decreasing loop counter)
@[5](Range checking)

+++
## Raw Strings
- Raw Strings is deliminated by a triple quote
  - contains no character escaping
  - may contain new lines and other characters

``` Kotlin
val text = """
    for (c in "foo")
        print(c)
"""
```

+++
## String Interpolation
- Strings can contain placeholders for variables or expressions
- Cleaner alternative to String.format()

``` Kotlin
val i = 10
val s = "i = $i"

val name = "abc"
val str = "$name.length is ${name.length}"
```
@[1-2](Generates "i = 10")
@[4-5](Generates "abc.length = 3")

+++
## Function Definitions
``` Kotlin
fun getFullName( cust: Customer): String = {
  return "${cust.forename} ${cust.surname}"
}

fun getFullName( cust: Customer): String =
                "${cust.forename} ${cust.surname}"

fun getFullName( cust: Customer) = "${cust.forename} ${cust.surname}"
```
@[1-3](Full method definition with explicit return type)
@[5-6](Method closure is optional for single expression functions)
@[8](Return type can be inferred for single expression functions)

+++
## Function Parameters, Default Values
- Ability to define default values for optional parameters
- Reduces need for overloaded methods

``` Kotlin
fun createBook(title: String,
               subtitle : String? = None,
               paperback : Boolean = true,
               price: BigDecimal = BigDecimal(7.99)) : Book{
        ...
}
```
######Effective Java: Use Overloading Judiciously

+++
## Using Named Parameters
- Ability to specify optional parameters by name
- Overrides default value if supplied

``` Kotlin
createBook("Kotlin in Action",
            paperback=False,
            price = BigDecimal(14.99))
```

+++
## Extension Functions
- Add functions onto existing classes
- No need to create a sub-classes
``` Kotlin
fun <T> MutableList<T>.swap(index1: Int, index2: Int){
    val tmp : T = this[index1]
    this[index1] = this[index2]
    this[index2] = tmp
}
```

+++
## Using Extension Methods
``` Kotlin
fun String.toCamelCase() : String {
   return this.split(' ').map { it -> it.toLowerCase()
.capitalize() }
.joinToString(separator = "")
}

fun main(args: Array<String>) {
   println("this is a test".toCamelCase())
   println("ANOTHer Test Case".toCamelCase())
}
```
