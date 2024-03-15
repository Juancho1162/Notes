#### Functions
**A function is a mapping that takes one or more arguments and produces a single result, and is defined using an equation that gives a name for the function, a name for each of its arguments, and a body that specifies how the result can be calculated in terms of the arguments.** For example:
``` 
double x = x + x
```

When a function is applied to actual arguments, the result is obtained by substituting these arguments into the body of the function in place of the argument names. This process may immediately produce a result that cannot be further simplified, such as a number. More commonly, however, the result will be an expression containing other function applications which must then be processed in the same way to produce the final result. For example:
```
double 3
= {applying double}
3+3
= {applying +}
6
```

Similarly we can do:
```
double (double 2)
= {applying inner double}
double (2+2)
= {applying +}
double 4
= {applying double}
4+4
= {applying +}
8
```

Alternatively the same result can also be calculated by starting with the outer application of the function double rather than the inner.
```
double (double 2)
= {applying outer double}
double 2 + double 2
= {applying the first double}
(2+2) + double 2
= {applying the first +}
4 + double 2
= {applying double}
4 + (2 + 2)
= {applying the second +}
4 + 4
= {applying +}
8
```

However, this approach requires two more steps than our original version. In general the order in which functions are applied in a calculation does not affect the value of the final result, but it may affect the number of steps required, and whether the calculation process terminates.

#### Functional Programming
**Generally speaking, functional programming can be viewed as a *style* of programming in which the basic method of computation is the application of functions to arguments. In turn, a functional programming language is one that *supports* and *encourages* the functional style.**

Consider the task of computing the sum of the integers between one and some larger number **n**. In many concurrent programming languages, this would normally be achieved using two integer variables whose values can be changed over time by means of the assignment operator =, with one such variable used to accumulate the total, and the other used to count from 1 to n. For example in Java:
```Java
int total = 0;
for (int count = 1; count <= n; count++)
	total = total + count;
```

In the above program, the basic method of computation is *changing stored values*, in the sense that executing the program results in a sequence of assignments. In general, programming languages such as Java in which the basic method of computation is changing stored values are called **imperative languages**, because program in such languages are constructed from imperative instructions that specify precisely how the computation should proceed.

In Haskell we would normally use two library functions, one called ($[..]$) that is used to produce the list of numbers between 1 and n, and the other called ($sum$), that is used to produce the sum of this list:
```Haskell
sum[1..n]
```

In this program, the basic method of computation is *applying functions to arguments*, in the sense that executing the program results in a sequence of applications. 
```
sum [1..5]
= {applying [..]}
sum [1,2,3,4,5]
= {applying sum}
1 + 2 + 3 + 4 + 5
= {applying +}
15
```

Most **imperative languages** provide some form of support for programming with functions, so the Haskell program ($sum [1..n]$)  could be translated into such languages. However, many imperative languages do not encourage programming in the functional style. For example, many languages discourage or prohibit functions from being stored in data structures such as lists, from constructing intermediate structures such as the list of numbers in the above example, from taking functions as arguments or producing functions as results, or from being defined in terms of themselves. In contrast, Haskell imposes no such restrictions on how functions can be used, and provides a range of features to make programming with functions both simple and powerful.


### References
- Graham Hutton, **Programming in Haskell** (2018).