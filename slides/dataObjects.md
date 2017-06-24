## Data Objects
+++
## Simple Data Objects - Java
```Java
import java.util.Date;

public class Person {
   private final String id;
   private final String forename;
   private final String surname;
   private final Date dateOfBirth;

   public Person(String id, String forename, String surname, Date dateOfBirth) {
       this.id = id;
       this.forename = forename;
       this.surname = surname;
       this.dateOfBirth = dateOfBirth;
   }

   public String getId() {
       return id;
   }

   public String getForename() {
       return forename;
   }

   public String getSurname() {
       return surname;
   }
```

---
## Simple Data Objects - Kotlin
``` Kotlin
import java.util.Date

data class Person(val id: String,
    val forename: String,
    val surname: String,
    val dateOfBirth: Date)
```

---
## Simple Data Objects - Kotlin (continued)
Implementations of toString(), equals, hashCode() and copy() are automatically created.
Getters created for all properties, and Setters only created for mutable properties.

``` Kotlin
person.equals()
person.hashCode()
person.toString()
person.copy()
```
