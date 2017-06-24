## The Basics
+++
## Objects Everywhere
- Everything is an object. |
- No 'primitive' types. |
- Data types are very similar to Java |
+++
## Numeric Data Types
- Numeric Types |
  - Integer : Long, Int, Short, Byte
  - Decimal : Float, Double
- Compiles to primitive types (unless nullable) |
+++
## Numeric Conversion
- No automatic conversion between types
  - Use toInt(), toLong(), ... methods
``` Kotlin
val b: Byte = 1 // OK, literals are checked statically
val i: Int = b // ERROR

val i: Int = b.toInt() // Ok Explicitly widened
```
+++
## Numeric Ranges
```
for (i in 1..100) { ... }  // closed range: includes 100
for (i in 1 until 100) { ... } // half-open range: does not include 100
for (x in 2..10 step 2) { ... }
for (x in 10 downTo 1) { ... }
if (x in 1..10) { ... }
```
+++
## Text Data Types
- Char |
  - no automatic conversion to numbers.
  - Use c.toInt() to get ASCII code
- String |
  - immutable sequences of Char
  - may contain escape characters e.g. "Hello, world!\n"
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
## String Templates
- Strings can contain placeholders for variables or expressions.
``` Kotlin
val i = 10
val s = "i = $i"

val name = "abc"
val str = "$name.length is ${name.length}"
```
+++
## Variable Definitions
- Reverse of Java notation |
  - variable name followed by type 
- var - mutable variable
- val - immutable property
+++
``` Kotlin
val customerName : String = "Andy Bowes"
val customerName = "Andy Bowes"
```
+++
## Function Definitions
- Functions are 'fun'
``` Kotlin
fun getFullName( cust: Customer): String = {
  return "${cust.forename} ${cust.surname}"
}

fun getFullName( cust: Customer): String = "${cust.forename} ${cust.surname}"

fun getFullName( cust: Customer) = "${cust.forename} ${cust.surname}"
```
