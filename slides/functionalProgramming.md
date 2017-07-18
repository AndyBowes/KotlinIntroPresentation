---?image=assets/images/gears.jpeg&size=cover
## Functional Programming
+++
## Higher Order Functions
- Kotlin supports functional programming |
- Kotlin functions can: |
  - Accept functions as parameters
  - Return functions as results
- Functions can also be declared as variables |

+++
## Higher Order Functions - Example

``` Kotlin
fun getTaxCalculation(state:String) : (BigDecimal) -> BigDecimal {
    ...
}

fun BigDecimal.calculateTax(calculator: (BigDecimal) -> BigDecimal) = calculator(this)

val calculator = getTaxCalculation("CA")
val orderValue = BigDecimal(1789.25)
val taxValue = orderValue.calculateTax(calculator)
```
@[1-3](Define function which returns a function)
@[5](Define function a function as a argument)
@[7](Fetch tax function for California)
@[7-9](Use this function to calculate tax)
+++
## Lambda Functions
- Kotlin supports lambda functions|
- Cleaner syntax than Java |
- No need for functional interfaces |
- Any function passed as a parameter can be replaced by a lambda

+++
## Lamda Functions - Example

``` Kotlin
people.filter({person -> person.name.startsWith("S")})
people.filter{person -> person.name.startsWith("S")}
people.filter{it.name.startsWith("S")}
```
@[1](Pass lambda function to filter method)
@[2](Parentheses can be omitted for last parameter)
@[3](Keyword 'it' can be used as implicit item name)

+++
## Collections
- Similar to Java 8 Streams |
- Cleaner syntax than Java |
- Fluent interface for |
  - Filtering
  - Sorting
  - Mapping
  - Grouping/Partitioning
- Supports potentially infinite sequences

+++
## Collections Example
``` Kotlin
data class Person(val name:String, val age: Int )

val people = peopleRepository.fetchAll()
val longestName = people.filter{ it.age < 20 }
        .map{ it.name }
        .maxBy{ it.length }
```

+++
## Functional Support
- In terms of inbuilt functional support |
  - Java < Kotlin < Scala
- Additional functional support |
  - funKTionale library
  - Future versions of Kotlin
