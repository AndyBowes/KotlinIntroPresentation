## Smart Casting
- Type checks with the is or !is operator |
- Compiler tracks is checks and performs automatic cast |
- No need to create extra variables for cast results |
+++
### Smart Casting Examples
```
fun demo(x: Any, y:Any?) {

   if (x is String) {
       print(x.length)
   }

   if (x !is String) return
   print(x.length) // x is automatically cast to String

   when (x) {
       is Int -> print(x + 1)
       is String -> print(x.length + 1)
       is IntArray -> print(x.sum())
   }

   val answer: String = y as String
   val answer3: String? = y as? String
}
```
@[3-5](x is automatically cast to String within closure)
@[7-8](x is automatically cast to String)
@[10-14](Can be used on each condition of a when statement)
@[16](Unsafe Case will fail if y is not a String)
@[17](Safe Case will return Null if y is not a String)
