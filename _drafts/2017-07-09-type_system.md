<!--### Type System and it's features in Swift-->
### Value of Type System (new title)

Type system is something which comes up so many times, especially when you are reading about the features of any programming language. What I knew about the Type System is that it has something to do with types, that's it. :p. Unknowingly we do know about the functionality of type system but we don't know what exactly is Type system and how it works.

I will try to summarize whatever I have learned about the Type system.

In simple words, it's a system whose job is to perform checks, it can be at different stages like compile time or run time. By 'checks' I mean, put constraints to prevent illegal program states. Now depending on when this constraints are applied, it will be known whether it's a dynamic type system or static type system. So the stage at which they are applied will decide what type of type system it is. If it's done at compile time then it is static type system and if it's done at runtime then it's dynamic system.

Now let's go beyond the basic definition. A good type system will remove the need for dynamic type checking, rather it will allow you to check statically, which will remove the type errors at runtime. This is what a strongly typed language is, when it's compiler can guarantee that there will be no type errors in any program.

When people talk about type system in any language they don't just mean what we learned above but more than that. They talk about specific features of any language like different types, how types work in that language, Type inference etc. In our case we will take example of Swift.

We will talk about one main feature of Swift's Type system:


**Type Inference**: If you just declare a variable with an initial value then compiler will infer the type of this variable. In Swift it's very common and most of the times you will not see type variable. Swift has pretty good inference.

Let's discuss how this works. There is a very famous algorithm called **Hindley-Milner type inference algorithm**. Swift implements type inference using a constraint-based type checker, which is very similar to Hindley-Milner type inference algorithm. Hindley-Milner Type Inference algorithm provides us certain rules which we can use to determine the type of any expression. These are the rules:

\begin{array}{cl}
 \displaystyle\frac{x:\sigma \in \Gamma}{\Gamma \vdash x:\sigma} & \trule{T-Var} \\ \\
 \displaystyle\frac{\Gamma \vdash e_1:\tau_1 \rightarrow \tau_2 \quad\quad \Gamma \vdash e_2 : \tau_1 }{\Gamma \vdash e_1\ e_2 : \tau_2} & \trule{T-App} \\ \\
 \displaystyle\frac{\Gamma,\;x:\tau_1 \vdash e:\tau_2}{\Gamma \vdash \lambda\ x\ .\ e : \tau_1 \rightarrow \tau_2}& \trule{T-Lam} \\ \\
 \displaystyle\frac{\Gamma \vdash e_1:\sigma \quad\quad \Gamma,\,x:\sigma \vdash e_2:\tau}{\Gamma \vdash \mathtt{let}\ x = e_1\ \mathtt{in}\ e_2 : \tau} & \trule{T-Let} \\ \\
 \displaystyle\frac{\Gamma \vdash e: \sigma \quad \overline{\alpha} \notin \mathtt{ftv}(\Gamma)}{\Gamma \vdash e:\forall\ \overline{\alpha}\ .\ \sigma} & \trule{T-Gen}\\ \\
 \displaystyle\frac{\Gamma \vdash e: \sigma_1 \quad\quad \sigma_1 \sqsubseteq \sigma_2}{\Gamma \vdash e : \sigma_2 } & \trule{T-Inst} \\ \\
\end{array}

You can read more about these rules [here](https://en.wikipedia.org/wiki/Hindley%E2%80%93Milner_type_system#Typing_rules). To understand these rules first you should read about Lambda Calculus. You can watch [this](https://youtu.be/eis11j_iGMs) video where Professor Graham Hutton explains Lambda Calculus.

Type system is very valuable. When you have type system which checks statically, it removes a lot of bugs and makes it easier for you to write code. You will realize it when you work on other languages, where the expectation was int and you are allowed to pass an string.

<!-- See JS note -->

<!-- All of that is really abstract so let’s look at a concrete example.

let a = 1 + 2
The constraints system representation of this expression looks something like this:

a simple constraints graph -->


<!-- https://www.cocoawithlove.com/blog/2016/07/12/type-checker-issues.html -->
<!-- // http://akgupta.ca/blog/2013/05/14/so-you-still-dont-understand-hindley-milner/
// http://www.cs.cornell.edu/courses/cs3110/2011sp/Lectures/lec26-type-inference/type-inference.htm
// write it in this way: https://softwareengineering.stackexchange.com/questions/279316/what-exactly-makes-the-haskell-type-system-so-revered-vs-say-java
// http://dev.stephendiehl.com/fun/006_hindley_milner.html
// https://github.com/apple/swift/blob/master/docs/TypeChecker.rst
// Read this: https://medium.com/@slavapestov/the-secret-life-of-types-in-swift-ff83c3c000a5
// and: https://academy.realm.io/posts/altconf-2017-manu-rink-secret-life-of-types-in-swift/
// Refer to type system pdf saved http://digital.cs.usu.edu/~allan/Compilers/Notes/TypeChecking.pdf
// https://stackoverflow.com/questions/29924477/is-swift-a-dynamic-or-static-language -->
