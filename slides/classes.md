
---?image=assets/images/blackboard.jpeg&size=cover
## Classes

+++
## Classes
- Similar to Java class definition |
- Multiple classes can be defined in the same file|
- File name is independent of class name|
- Default visibility is public |
- Final by default |

+++
## Primary Constructors

``` Kotlin
class Customer(name: String) {
    init {
        logger.info("Customer initialized with value ${name}")
    }
}

val customer = Customer("Guy Edwards")
```
- No code in primary constructor body
- Code placed in optional init blocks
- Instances created without new keyword

+++
## Constructors - Default Values
- Constructor arguments can have default values
- Reduces need for overloaded constructors

``` Kotlin
DummyHashMap(val initialCapacity: Int = 16,
             val loadFactor : Float = 0.75F)
```

+++
## Secondary Constructors
- Class may have secondary constructor
- Each secondary constructor *must* invoke primary constructor

``` Kotlin
class Person(val name: String) {
    constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
    }
}
```

+++
## Inheritance
- All classes are final unless explicitly declared otherwise
- Overridable methods must be declared open.
- Overrided methods must be declared.

``` Kotlin
open class Base(p: Int){
  fun deleteName(name: String){ ... }
  open fun addName(name: String){...}
}

class Derived(p: Int) : Base(p) {
  override fun addName(name:String) {...}
}
```

######Effective Java: Design and document for inheritance or else prohibit it
######Effective Java: Consistently use the override annotation

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
######Effective Java: Always override hashCode when you override equals
######Effective Java: Make defensive copies when needed

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
######Effective Java: Enforce the singleton property with a private constructor or an enum type

+++
## Companion Objects
- Provide similar functionality to Java static methods

``` Kotlin
class MyClass {
    companion object Factory {
        fun create(): MyClass = MyClass()
    }
}

val myInstance = MyClass.create()
```

+++
## Sealed Classes
- Conceptually similar to Enums

``` Kotlin
sealed class ChessPiece
class King() : ChessPiece()
class Queen() : ChessPiece()
class Rook() : ChessPiece()
class Bishop() : ChessPiece()
class Knight() : ChessPiece()
class Pawn() : ChessPiece()

fun move(piece: ChessPiece): Unit = when(piece) {
    is King -> ...
    is Queen -> ...
    is Rook -> ...
    is Bishop -> ...
    is Knight -> ...
    is Pawn -> ...
}
```
@[1](Define Sealed class)
@[2-7](Define implementations of sealed class)
@[9-16](Exhaustive checking in when statements)

+++
## Type Aliases
- Added in Kotlin 1.1 |
- Provides a alias for existing types |
- ```typealias MovieCast = List<Actor>``` |
- Can improve code readability and maintainability |

+++
## Delegation

Joshua Bloch, Effective Java:
>Inheritance is a powerful way to achieve code reuse, but it is not always the best tool for the job. Used inappropriately, it leads to fragile software.

######Effective Java: Favour Composition over Inheritance

+++
## Delegation Example
```
interface Printable {
    fun print(message: String)
}

class PrintableImpl(val copies: Int) : Printable {
    override fun print(message: String) { for (i in 1..copies) { ... } }
}

class Derived(b: Printable) : Printable by b

val printer = PrintableImpl(copies=2)
val derived = Derived(printer)

derived.print("Test Message")
```
@[1-3](Define Interface)
@[5-7](Provide implementation of interface)
@[9](Define subclass of interface using delegation)
@[11-12](Inject implementation of interface via constructor)
@[14](Invoking method will delegate to injected instance)
