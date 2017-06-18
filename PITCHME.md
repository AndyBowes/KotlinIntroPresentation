# Introduction to Kotlin

---
## What is ‘Kotlin’?
* ‘New’ programming language|
  * Developed since 2011, v1.0 released Feb 2016|
* Developed by JetBrains
  * Makers of IntelliJ & Android Studio|
* Runs on Java Virtual Machine (JVM)|
* Open Source
---
## What’s wrong with plain old Java ?
* It’s verbose.
  * Too much ‘boilerplate’ code.
* Multiple overload methods/constructors.
* Runtime Errors
* Null Pointers
* Class Cast exceptions
* Functional paradigm is still an afterthought.
  * Java 8 over-promised & under-delivered
  * Lambda functions treated as instances of interfaces
---
## 10 reasons to consider Kotlin as your next language 
* 100% Java Interoperability
* All code compiles to pure Java byte-code
* Kotlin classes can invoke methods in Java classes
* Java classes can invoke Kotlin functions
* Kotlin can use standard Java libraries
* Many Kotlin specific libraries are available but can continue to use familiar Java libraries
* Allows incremental migration to Kotlin from Java
* Deploy mixed applications as a single artifact
---
```Java
Simple Data Objects
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
```Kotlin
import java.util.Date

data class Person(val id: String,
    val forename: String,
    val surname: String,
    val dateOfBirth: Date)
```
