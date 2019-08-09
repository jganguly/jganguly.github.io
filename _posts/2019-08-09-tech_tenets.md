---
title: Tech Tenets
author: Jaideep Ganguly
---

{% include header.html %}

1.	**Adopt functional programming style, use JVM compatible languages**. Use Kotlin (and not Scala). Kotlin with rule along with Java. It is everything Scala wanted to be before they lost their focus and overloaded it with functional arcana that almost all domain models have no use for. Java has a lot of unnecessary boilerplate code, with Kotlin one will realize just how much code you write in Java to make the compiler happy without really advancing anyone's knowledge of the problem domain. Kotlin is literally the opposite, with most language features geared towards creating clear, expressive DSLs, without losing performance. It is not extremely innovative, as a lot of things Kotlin introduces echo features from Scala, Groovy and Swift, but the point of a language is not innovation, it's pragmatism and usability, and Kotlin has it in plenty. Since Kotlin is fully JVM compatible, it is interoperable with existing Java libraries. 
2.	**Business Rules and Configurations shall not be encoded in software procedures**. Instead, they will be expressed declaratively outside the code so that changes can be made quickly.
3.	**Adopt visualization techniques over boring reports.**
4.	**Adopt machine learning and deep learning techniques where desirable and pragmatic.**
  * [Machine Learning](http://jganguly.aka.corp.amazon.com/html/ML.pdf)
  * [Deep Learning Demystified](http://jganguly.aka.corp.amazon.com/html/DL.pdf)
  * [A Brief History of Machine Learning](https://www.linkedin.com/pulse/brief-history-machine-learning-dr-jaideep-ganguly)
  * [Machine Learning & the Grand Challenge](https://www.linkedin.com/pulse/machine-learning-grand-challenge-dr-jaideep-ganguly)
5.	**Anything that we build should be simple, intuitive and silky smooth.** Wherever feasible, the usability experience should encompass voice and touch and span multiple devices. **Over time, fewer and fewer engineers should be required to accomplish more and more complex engineering tasks**.

