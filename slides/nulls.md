## Null Safety
- No more Null Pointer Exceptions
- Need to explicitly state that variable/parameter allows nulls
val name: String - Cannot be assigned null
val name: String? - Can be set to a value or null
- Unsafe calls are prevented by the compiler

+++
## Compile Time Null Checks
``` Kotlin
fun getCheckNulls(): Int{
   var a: String = "abc"
   a = null // compilation error

   var b: String? = "abc"
   b = null // ok

   b = getName()  // Call a function that returns a Nullable String
   b.length // Compilation Error, invoking method on potentially Null Object
   if (b != null){
       b.length // Can now execute method on the variable
   }

   // Safe Call Operator - Returns length or Null as an Int?
   var i = b?.length

   // Elvis Operator - Returns either the length of the String or -1 if b is null
   return b?.length ?: -1
}
```
@[2-3](Can't assign null to non-null variable)
@[5-6](Use '?' suffix to indicate nullable variable)
@[8-11](Need to check if variable is null before using it)
@[13-15](Safe check returns length or Null)
@[16-18](Elvis operator check returns length or default)
