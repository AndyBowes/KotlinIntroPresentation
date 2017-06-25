## Functions




+++
## Extension Functions
- Add functions onto existing classes even those in stdlib
- No need to create a sub-classes to extend functionality
``` Kotlin
fun MutableList<Int>.swap(index1: Int, index2: Int) {
   val tmp = this[index1] // 'this' corresponds to the list
   this[index1] = this[index2]
   this[index2] = tmp
}
```
This method is now available on all MutableList<Int>

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
