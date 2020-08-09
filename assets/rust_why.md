[TOC]

# WHY RUST?

The Rust programming language has been Stack Overflow's most loved language for five years in a row, clearly establishing the fact that a significant section of the developer population love it. Rust solves many pain points present in current popular languages and has a limited number of downsides.

# STATICALLY TYPED

Rust is a `statically` and  `strongly typed` systems programming language. Statically means that all types are known at compile-time, strongly means that these types are designed to make it harder to write incorrect programs. A successful compilation means you have a much better guarantee of correctness than with language such as C or Java, generating the best possible machine code with full control of memory use. 

The debate between dynamic versus static typed is long standing and will continue. However, dealing with dynamic typing in large code bases is difficult. Statically typed languages allow the compiler to check for constraints on the data and its behavior and thereby significantly reducing cognitive overheads on the developer to produce correct code. Statically typed languages differ from each other. An important aspect is how they deal with the concept of `NULL`, which means the value may be something or `nothing`. Like Haskell and some other modern programming languages, Rust encodes this possibility using an optional type and the compiler requires you to handle the `None` case.

# SAFETY

The basis for computers and computer programs is the Von Neumann model which is over seventy years old. This architecture has one memory that holds both the instructions as well as program data. The commonly used programming languages C and C++ offer no support for automatic memory management. The programmer has to deal with memory management making the program error prone. A common source of error is the well known buffer overflow. Buffer overruns are the cause of many computer problems, such as crashing and vulnerability in terms of attacks. The past years have revealed multiple exploits: vulnerabilities that are the result of these types of errors and which could have significant consequences. 

Recently, a serious vulnerability known as Heartbleed was discovered. The bug was in OpenSSL which is commonly used in network routers and web servers. This vulnerability allowed encryption keys to be read remotely from these systems and thereby compromised their security. This vulnerability would have been avoided Rust was used to develop OpenSSL.

Rust is safe by default. All memory accesses are checked and It is not possible to corrupt memory by accident. With direct access to hardware and memory, Rust is an ideal language for embedded and bare-metal development. One can write extremely low-level code, such as operating system kernels or micro-controller applications. However, it is also a very pleasant language to write  application code as well. Rust’s core types and functions as well as reusable library code stand out in these especially challenging environments. However, unlike many existing systems programming languages, Rust does not require developers to spend their time mired in nitty-gritty details. 

Rust’s strong type system and emphasis on memory safety, all enforced at compile time, mean that it is extremely common to get errors when compiling your code. This can be a frustrating feeling for programmers not used to such an opinionated programming language. However, the Rust developers have spent a large amount of time working to improve the error messages to ensure that they are clear and actionable. One must not gloss over Rust compile time error messages.

# RUNTIME

Rust strives to have as many zero-cost abstractions as possible,  abstractions that are as equally  performant as corresponding hand-written code. Zero-cost abstraction means that there's no extra runtime overhead that you pay for certain powerful abstractions or safety features that you do have to pay a runtime cost for other languages. However, be aware that not every abstraction or every safety feature in Rust is truly zero-cost.

A programming language runtime, is all the machinery provided by the language itself and which is injected into and supports the execution environment. This can include things as small as some minimal routines for laying out and freeing memory, as in C, to entire virtual machines, interpreters, and standard libraries, as in Java, Python or Ruby. Think of it as the minimal machinery that is both part of the language and must be present, either in the executable itself or installed on the computer, for any given program written in that language to run.

Rust strives to have a very fast run time. It does this in part by compiling to an executable and injecting only a very minimal language runtime and \em{does not provide a memory manager, i.e., a garbage collector that operates during the executable’s runtime.

# PERFORMANCE

Rust gives you the choice of storing data on the stack or on the heap and determines at compile time when memory is no longer needed and can be cleaned up. This allows efficient usage of memory as well as more performant memory access. Tilde, an early production user of Rust in their Skylight product, found they were able to reduce their memory usage from 5GB to 50MB by rewriting certain Java HTTP endpoints in idiomatic Rust. Savings like this quickly add up when cloud service providers charge premium prices for increased memory or additional machines.

Without the need to have a garbage collector continuously running, Rust projects are well-suited to be used as libraries by other programming languages via foreign-function interfaces. This allows existing projects to replace performance critical pieces with speedy Rust code without the memory safety risks inherent with other systems programming languages. Some projects are being incrementally rewritten in Rust using these techniques.

The fundamental principles of Rust are:

- ownership and safe borrowing of data
  
- functions, methods and closures to operate on data
  
- tuples, structs and enums to aggregate data
  
- matching pattern to select and destructure data
  
- traits to define behavior on data



