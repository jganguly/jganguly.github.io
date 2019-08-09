---
title: Calling Java from Scala
author: Jaideep Ganguly
layout: default
---

{% include header.html %}

I think attempting Scala from java is slightly skewed philosophically. Because both of them differ on paradigms. On top of my head, here are a few differences:

| **Java**                                    | Scala                                        |
| ------------------------------------------- | -------------------------------------------- |
| Three namespaces: packages, methods, fields | Uniform access principle                     |
| Has primitives                              | Single Object model. Everything is an object |
| Special (irregular) handling of arrays      | Arrays are just like any other collection    |
| void, null                                  | Unit, Nothing                                |
| ...                                         | ...                                          |

JVM does not have bytecode support for a lot of stuff scala tries. So scala has to resort to many hacks to make those paradigms a reality.

A small example:

```scala
trait J {
	private[J] val x = “Hey”
}
class Prac4 extends J

// Now lets look at the bytecode:

public class Prac4 implements J {
  private final java.lang.String J$$x;
  public java.lang.String J$$x();
  public void J$_setter_$J$$x_$eq(java.lang.String);
  public Prac4();
}
```

So `x` is supposed to be `final`. Well in bytecode it is not. Below is a working java code

```scala
Prac4 prac4 = new Prac4();
prac4.J$_setter_$prac$J$$x_$eq("jatin");	//sets `x` to `jatin`
```

`x` is technically useless. Means its visibility is only in` trait J`. But here in bytecode we can see that is public and can be accessed.

```scala
System.out.println(prac4.prac$J$$x()); //prints the `x` value
```

Now look at this:

```scala
public Prac4();
    descriptor: ()V
    flags: ACC_PUBLIC
    Code:
      stack=1, locals=1, args_size=1
         0: aload_0
         1: invokespecial #24                 // Method java/lang/Object."<init>":()V
         4: aload_0
         5: invokestatic  #30                 // Method J$class.$init$:(LJ;)V
         8: return
}
```

So it is here at `5`, it calls J\$class.class which calls `InterfaceMethod J.J\$_setter_\$J\$\$x_\$eq:(Ljava/lang/String;) V` 

Technically the compiler is fooling us. What it portrays is far from what it actually is in reality. All thus due to lack of bytecode support.

**Another example:**

```scala
def func(arr:Array[_ <: String]) = arr.length

func(Array[Nothing]())// line -a
```

Now `line-a`compiles successfully. But it throws an error at runtime. Why? Because at bycode level, func expects a `String[]`. 

At `line-(a)` we pass `Object[]`. But why `Object[]`? Because in scala, Nothing is subtype of every other type. But how do we express this at byte code. We cant >.<. Hence `Object[]` is used. 

Note this issue is only with arrays as they are reified. Works alright with List as it is type-erased.

**Bottom-Line: ** **It is futile to attempt calling scala from java. Scala has a rich type system which cannot be directly expressed from Java. Solution: Hava a java wrapper for your scala code.**
