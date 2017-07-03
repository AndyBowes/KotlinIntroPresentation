## Classes



+++
## Class Definitions


+++
## Primary Constructors



+++
### Inheritance
- All class are final unless explicitly declared otherwise
- All methods in subclass that override parent must be declared open in parent and marked with override in subclass

``` Kotlin
open class Base(p: Int){
  fun deleteName(name: String){ ... }
  open fun addName(name: String){...}
}

class Derived(p: Int) : Base(p) {
  override fun addName(name:String) {...}
}
```

<span class"effective">Effective Java: Design and document for inheritance or else prohibit it</span>
<span class"effective">Effective Java: Consistently use the override annotation</span>

+++
## Data Classes - Kotlin

``` Kotlin
import java.util.Date

data class Person(val id: String,
    val forename: String,
    val surname: String,
    val dateOfBirth: Date)
```

+++
## Data Classes
### Methods for Nothing
Implementations of toString(), equals, hashCode() and copy() are automatically created.
Getters created for all properties, and Setters only created for mutable properties.

``` Kotlin
person.equals()
person.hashCode()
person.toString()
person.copy()
```

<span class"effective">Effective Java: Make defensive copies when needed</span>

+++
## Implementing Singletons
- Kotlin uses Objects to create Singletons.
- These are convenient placeholders for the equivalent of static Java methods.

``` Kotlin
object DataProviderManager {
    fun registerDataProvider(provider: DataProvider) {
        // ...
    }

    val allDataProviders: Collection<DataProvider>
        get() = // ...
}
```

<span class"effective">Effective Java: Enforce the singleton property with a private constructor or an enum type</span>

+++
## Companion Objects


+++
## Sealed Classes


+++
## Delegation

Joshua Bloch, Effective Java:
>Inheritance is a powerful way to achieve code reuse, but it is not always the best tool for the job. Used inappropriately, it leads to fragile software. It is safe to use inheritance within a package, where the subclass and the superclass implementations are under the control of the same programmers.

<span class"effective">Effective Java: Favour Composition over Inheritance</span>



+++
## Delegation Example
```
interface Printable {
    fun print()
}

class PrintableImpl(val x: Int) : Printable {
    override fun print() { print(x) }
}

class Derived(b: Printable) : Printable by b

val printer = PrintableImpl(copies)
val derived = Derived(printer)
```
@[1-3](Define Interface)
@[5-7](Provide implementation of interface)
@[9](Define subclass of interface using delegation)
@[11-12](Inject implementation of interface via constructor)
