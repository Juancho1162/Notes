#### 3.1 Basic Concepts
A **type** is a collection of related values. For example, the type ``Bool`` contains the two logical values ``False`` and ``True`` , while the type ``Bool -> Bool`` contains all functions that map arguments from ``Bool`` to results from ``Bool``, such as the logical negation function ``not``.
$$
\begin{gather}
|=\text{"such that"}\\
: = \text{"such that"}\\
Bool = \{True, False\}  \\
Bool \to Bool = \{\forall f | f:Bool \to Bool \}
\end{gather}
$$
For example, the logical negation function not would be:
$$
\begin{gather}
not:Bool \to Bool\\
\text{not True = False}\\
\text{not False = True}
\end{gather}
$$
So we can see that types can be **collections or sets of related values** such as **Bool={True, False}**, or **collections of functions that maps collections of related values** such as **Bool -> Bool**. In Haskell we would declare these examples as:
```Haskell
False :: Bool
True :: Bool
not :: Bool -> Bool
```

**I can see this as sets in set theory, with the operator ``::`` being ($\in$)**. Let's compare math notation with Haskell notation:
$$
\begin{gather}
Bool = \{True, False\} \\
mapBool = \{\forall f | f: Bool \to Bool \} \\
\text{False} \in Bool \to \text{False :: Bool}\\
\text{not False} \in Bool \to \text{not False :: Bool}\\
\text{not} \in mapBool \to not :: Bool \to Bool
\end{gather}
$$
```Haskell
not False :: Bool
not True :: Bool
not (not False) :: Bool
```
 

In Haskell, every expression must have a type, which is calculated prior to evaluating the expression by a process called type inferece. ``If f :: A -> B && e :: A then f e :: B`` 
```Haskell
f :: A -> B
e :: A
f e :: B
```

Because type inference precedes evaluation, Haskell programs are type safe, in the sense that type erros can never occur during evaluation. In practice, type inference detects a very large class of programs errors, and is one of the most useful features of Haskell.

The downside of type safety is that some expressions that evaluate successfully will be rejected on type grounds. For example, ``if True then 1 else False`` 













### References
- Graham Hutton, **Programming in Haskell** (2018).