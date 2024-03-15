#### 1.1 Features of Haskell
- **Concise programs**: Due to the high-level nature of the functional style, programs written in Haskell are often much more concise than programs written in other languages. Moreover the syntax of Haskell has been designed with concise programs in mind, in particular by having few keywords, and by allowing indentation to be used to indicate the structure of programs. Haskell programs are often between two and ten times shorter than programs written in other languages.
- **Powerful type system**: Most modern programming languages include some form of type system to detect incompatibility errors, such as erroneously attempting to add a number to a character. Haskell has a type system that usually requires little type information from the programmer, but allows a large class of incompatibility errors in programs to be automatically detected prior to their execution, using sophisticated process called **type inference**. The Haskell type system is also more powerful than most languages, supporting very general forms of polymorphism and overloading, and providing a wide range of special purpose features concerning types.
- **List comprehensions**: One of the most common ways to structure and manipulate data in computing is using lists of values. To this end, Haskell provides lists as a basic concept in the language, together with a simple but powerful comprehension notation that constructs new lists by selecting and filtering elements from one or more existing lists. Using the comprehension notation allows many common functions on lists to be defined in a clear and concise manner, without the need for explicit recursion.
- **Higher-order functions**: Haskell is a *higher-order* functional language, which means that functions can freely take functions as arguments and produce functions as results. Higher-order functions can be used to define *domain-specific languages* within Haskell itself, such as for list processing, interactive programming, and parsing.
- **Effectful functions**: Many programs require some effects other than pure functions to work, such as reading inputs from the keyboard, writing an output to the screen, while the program is running. Haskell provides a uniform framework for programming with effects, without compromising the purity of functions, based upon the use of **monads** and **applicatives**.
- **Generic functions**: Haskell, in contrast to other languages, provides a range of library functions that can be used with any type that is functorial, applicative, monadic, foldable, or traversable, and moreover, allows new structures and generic functions over them to be defined.
- **Lazy evaluation**: Haskell programs are executed using a technique called *lazy evaluation*, which is based upon the idea that no computation should be performed until its result is actually required. As well as avoiding unnecessary computation, lazy evaluation ensures that programs terminate whenever possible, encourages programming in a modular style using intermediate data structures, and even allows programming with **infinite structures.**
- **Equational reasoning**: Because programs in Haskell are pure functions, simple *equational reasoning* techniques can be used to execute programs, to transform programs, to prove properties of programs, and even to calculate programs directly from specifications of their intended behaviour. Equational reasoning is particularly powerful when combined with the use of induction to reason about functions that are defined using recursion.

#### 1.2 A taste of Haskell
##### **Summing numbers**
Recall the function $sum$ used earlier in this chapter, which produces the sum of a list of numbers. In Haskell, sum can be defined using two equations:
```
sum []     = 0          # sum of empty list is zero.
sum (n:ns) = n + sum ns # sum of non-empy list is n + sum ns
```

For example:
```
sum [1,2,3]
= {applying sum}
1 + sum [2,3]
= {applying sum}
1 + (2 + sum [3])
= {applying sum}
1 + (2 + (3 + sum []))
= {applying sum}
1 + (2 + (3 + 0))
= {applying +}
6
```

Note that even though the function sum **is defined in terms of itself and is hence recursive**, it does not loop forever. In particular each applications of sum reduces the length of the argument list by one, until the list eventually becomes empty, at which point recursion stops and the additions are performed. Returning zero as the sum of the empty list is apropiate because zero is the identity for addition. That is 0 + x = x and x + 0 = x for any number x.

In Haskell, every function has a *type* that specifies the nature of its arguments and results, which is automatically inferred from the definition of the function. For example the function sum defined above has the following type:
```
Num a => [a] -> a
```

This type states that for any type a of numbers, sum is a function that maps a list of such numbers to a single such number. In a "mathematical notation":
$$
sum: [Num_1,Num_2,...,Num_n] \to Num
$$
Haskell support many different types of numbers, including integers, floating-point numbers, etc. Hence, for example, sum could be applied to a list of integers, as in the calculation above, or to a list of floating-point numbers.

Types provide useful information about the nature of functions, but, more importantly, their use allows many errors in programs to be automatically detected prior to executing the programs themselves. In particular, for every occurrence of function application in a program, a check is made that the type of the actual arguments is compatible with the type of the function itself. For example, attempting to apply the function sum to a list of characters would be reported as an error, because the characters are not a type of numbers.

##### **Sorting values**
Let us consider  more sophisticated function concerning lists, which illustrates a number of other aspects of Haskell. Suppose we define a function called qsort by the following two equations:
```
qsort []    = []
qsort(x:xs) = qsort smaller ++ [x] ++ qsort larger
              where
                 smaller = [a | a <- xs, a <= x] 
                 larger  = [b | b <- xs, b > x]
``` 

In this definition, ++ is an operator that appends two lists together; for example, $[1,2,3] ++ [4,5] = [1,2,3,4,5]$. **Where** is a keyword that introduces local definitions, in this case a list smaller comprising all elements **a** from the list **xs** that are less than or equal to x, together with a list larger comprising all elements **b** from **xs** that are greater than x. For example if $x=3$, and $xs =[5,1,4,2]$, then smaller$=[1,2]$ and larger=$[5,4]$. 

First of all we can see that qsort $[x] = [x]$ for any x. Let's verify that:
```
qsort [x]
= {applying qsort}
qsort [] ++ [x] ++ qsort []
= {applying qsort}
[] ++ [x] ++ []
= {applying ++}
[x]
```











### References
- Graham Hutton, **Programming in Haskell** (2018).