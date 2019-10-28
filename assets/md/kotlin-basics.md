### Why Kotlin?

##### Jaideep Ganguly ◼︎ Last Updated: 4/4/18

------

**Java Interoperability**
Kotlin is 100% interoperable with Java. Its yntax is familiar to any programmer  from the OOP domain. There are some differences from Java such as the constructors or the val var variable declarations. Below is a basic snippet of code.

```Kotlin
class Foo {
    val b: String = "bar"   // val means unmodifiable
    var i: Int = 0          // var means modifiable

    fun hello() {
        val str = "Hello"
        print("$str World")	// Strings can contain template expressions which start with $
    }

    fun sum(x: Int, y: Int): Int { // return type is Int
        return x + y
    }

    fun maxOf(a: Float, b: Float) = if (a > b) a else b
}
```

**String Interpolation**
It’s as if a smarter and more readable version of Java’s String.format() was built into the language:

```kotlin
val x = 4
val y = 7
print("sum of x and y is ${x + y}")  // sum of 4 and 7 is 11

```

**Type Inference**
Kotlin will infer your types wherever you feel it will improve readability:

```kotlin
val a = "Hello"                       // type inferred to String
val b: Double = 0.7                   // type declared explicitly
val c = 4                             // type inferred to Int
val d: List<String> = ArrayList()     // type declared explicitly
```

**Smart Casts** 

The Kotlin compiler tracks your logic and auto-casts types if possible, which means no more instanceof checks followed by explicit casts:

```kotlin
if (obj is String) {
    print(obj.toUpperCase())     // obj is now known to be a String
}
```

**Intuitive Equals**
No need to call equals() explicitly,  the == operator now checks for structural equality:

```Kotlin
val ram1 = Person("Ram")
val ram2 = Person("Ram")
ram1 == ram2    // true  (structural equality)
ram1 === ram2   // false (referential equality)
```

**Default Arguments**
No need to define several similar methods with varying arguments:

```Kotlin
fun build(title: String, width: Int = 800, height: Int = 600) {
    Frame(title, width, height)
}

```

**Named Arguments**

Default and named arguments help to minimize the number of overloads and improve the readability of the function invocation. Function parameters can have default values, which are used when a corresponding argument is omitted. This allows for a reduced number of overloads compared to other languages.

```Kotlin
foo(letter = 'd')
foo(letter = 'c', num = 3)

fun foo (letter : Char) {
    println(letter)
}
fun foo (letter : Char, num : Int, area : Float = 100.00f) {
    println(num)
}
```


**When Expression**
The switch case is replaced with the much more readable and flexible when expression:

```Kotlin
when (x) {
    1 -> print("x is 1")
    2 -> print("x is 2")
    3, 4 -> print("x is 3 or 4")
    in 5..10 -> print("x is 5, 6, 7, 8, 9, or 10")
    else -> print("x is out of range")
}
```

It works both as an expression or a statement, and with or without an argument:

```Kotlin
val res: Boolean = when {
    obj == null -> false
    obj is String -> true
    else -> throw IllegalStateException()
}
```

**Properties**
Custom set & get behavior can be added to public fields, which means we can stop bloating our code with mindless getters & setters.

```kotlin
class Frame {
    var width: Int = 800
    var height: Int = 600

    val pixels: Int
        get() = width * height
}
```

**The Data Class**
It’s a POJO complete with toString(), equals(), hashCode(), and copy(), and unlike in Java it won’t take up 100 lines of code:

```Kotlin
data class Person(val name: String,
                  var email: String,
                  var age: Int)

val john = Person("John", "john@gmail.com", 112)
```


**Operator Overloading**
A predefined set of operators can be overloaded to improve readability:

```Kotlin
data class Vec(val x: Float, val y: Float) {
    operator fun plus(v: Vec) = Vec(x + v.x, y + v.y)
}
val v = Vec(2f, 3f) + Vec(4f, 1f)
```


**Destructuring Declarations**
Some objects can be destructured, which is for example useful for iterating maps:

```kotlin
for ((key, value) in map) {
    print("Key: $key")
    print("Value: $value")
}
```

**Ranges**
For readability’s sake:

```kotlin
for (i in 1..100) { ... } 
for (i in 0 until 100) { ... }
for (i in 2..10 step 2) { ... } 
for (i in 10 downTo 1) { ... } 
if (x in 1..10) { ... }
```


**Extension Functions**
Remember the first time you had to sort a `List` in Java? You couldn’t find a sort() function so you had to ask either your tutor or google to learn of `Collections.sort()`. And later when you had to capitalize a `String`, you ended up writing your own helper function because you didn’t know of `StringUtils.capitalize()`.

If only there was a way to add new functions to old classes; that way your IDE could help you find the right function in code-completion. In Kotlin you can do exactly that:

```kotlin
fun String.replaceSpaces(): String {
    return this.replace(' ', '_')
}
val formatted = str.replaceSpaces()
```

The standard library extends the functionality of Java’s original types, which was especially needed for String:

```kotlin
str.removeSuffix(".txt")
str.capitalize()
str.substringAfterLast("/")
str.replaceAfter(":", "classified")
```

**Null Safety**
Java is what we should call an almost statically typed language. In it, a variable of type String is not guaranteed to refer to a String— it might refer to null. Even though we are used to this, it negates the safety of static type checking, and as a result Java developers have to live in constant fear of Null Pointer Exceptions, i.e., NPEs.

Kotlin resolves this by distinguishing between **non-null types** and **nullable types**. Types are non-null by default, and can be made nullable by adding a ? like so:

```Kotlin
var a: String = "abc"
a = null                // compile error

class Frame {
    var width: Int = 800
    var height: Int = 600

    val pixels: Int
        get() = width * height
}
b = null                // no problem
```

Kotlin forces you to guard against NPEs whenever you access a nullable type:

```kotlin
val x = b.length        // compile error: b might be null
```

And while this might seem cumbersome, it’s really a breeze thanks to a few of its features. We still have smart casts, which casts nullable types to non-null wherever possible:

```kotlin
if (b == null) return
val x = b.length        // no problem
```

We could also use a safe call ?., which evaluates to null instead of throwing a NPE:

```kotlin
val x = b?.length       // type of x is nullable Int
```

Safe calls can be chained together to avoid those nested if-not-null checks we sometimes write in other languages, and if we want a default value other than null we can use the elvis operator ?::

```kotlin
val name = ship?.captain?.name ?: "unknown"
```

If none of that works for you, and you absolutely need a NPE, you will have to ask for it explicitly:

```Kotlin
val x = b?.length ?: throw NullPointerException()  // same as below
val x = b!!.length                                 // same as above
```

**IDE Support**
You have a number of options if you intend to get started with Kotlin, but I highly recommend using IntelliJ which comes bundled with Kotlin—its features demonstrate the advantage of having the same people design both language and IDE.

