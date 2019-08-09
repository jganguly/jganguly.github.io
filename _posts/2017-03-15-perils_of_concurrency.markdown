---
title: The Perils of Concurren
author: Jaideep Ganguly

---

{% include header.html %}




**Concurrency**
Managing concurrency is wickedly tricky for large programs. At each program point, you must reason about which locks are currently held. At each method call, you must reason about which locks it will try to hold, and convince yourself that it does not overlap the set of locks already held.

**A Diverging Problem**
This problem is magnified because the locks you reason about are not simply a finite list in the program since the program is free to create new locks at run time as it executes. This gets worse because testing is not reliable with locks. Threads are non‐ deterministic, you can very well successfully test a program a thousand times and yet the program could go wrong the first time it runs on deployment! With locks, you must get the program correct through logic alone and that is very hard and time consuming to do so.

**Will over Engineering work?**
Over engineering will not solve the problem. Just as you avoid locks, you cannot also put a lock around every operation. The problem is that while new lock operations remove possibilities for race conditions, itsimultaneously introduces possibilities for deadlocks. A correct lock‐using program must have neither of these. Net net, there is no good way to fix locks and make them practical to use.

**Actors and Threads**
That is why Scala provides an alternative concurrency approach, one based on Erlang's message‐passing actors. An actor is a kind of thread that has a mailbox for receiving messages. Actors are implemented on top of normal Java threads. Java threads are not cheap. Typical Java virtual machines can have millions of objects but only a few thousand of threads. And remember, switching threads can often take thousands of processor cycles. For a program to be efficient, it is important to be sparing with thread creation and thread switching.

**Example Code**
Below is a simple example of message passing with Actors that leverages Scala Case Classes.


```scala
import actors._

object Ex_Actor {
    case object Quit
    case class Message(s: String)
    case class Number(n: Int)

    /* Simple Actor receiving messages as case classes */
    class SimpleActor extends Actor {

        def act(): Unit = {
            var flag = true
            while (flag) {
                receive {
                    case Quit =>
                        flag = false
                    case Message(s) =>
                        println("Got a string: " + s)
                    case Number(i) =>
                        println("Got a number: " + i)
                    }
                }
            }
        }

        case class StartCount(n: Int, a: CountActor)
        case class CountDown(n: Int)
        class CountActor(name: String) extends Actor {         /* CountActor */
            
            def act(): Unit = {
                var flag = true
                while (flag) {
                    receive {
                        case    StartCount(n, ca) =>
                                println(name + " : " + n)
                                ca ! CountDown(n - 1)
                                
                        case    CountDown(n) =>
                                println(n)
                                if (n > 0) {
                                    sender ! CountDown(n - 1)
                                    println(name)
                                }
                                
                        case  Quit => flag = false

                    }

                }
            }
        }

def main(args: Array[String]): Unit = {
    
    val ca1 = new CountActor("Counting Actor 1")
    val ca2 = new CountActor("Counting Actor 2")
    
    ca1.start()
    ca2.start()
    
    ca2 ! StartCount(10, ca1)
}
```

