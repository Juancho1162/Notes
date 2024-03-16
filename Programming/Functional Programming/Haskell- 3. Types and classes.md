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
 

In Haskell, every expression must have a type, which is calculated prior to evaluating the expression by a process called type inference. ``If f :: A -> B && e :: A then f e :: B`` 
```Haskell
f :: A -> B
e :: A
f e :: B
```

Because type inference precedes evaluation, Haskell programs are type safe, in the sense that type erros can never occur during evaluation. In practice, type inference detects a very large class of programs errors, and is one of the most useful features of Haskell.

The downside of type safety is that some expressions that evaluate successfully will be rejected on type grounds. For example, ``if True then 1 else False``  evaluates to the number 1, but contains a type error, because the types of all expressions in an `if-then-else` construct must match. 

If you want to check the type of any value or expression you can do it by preceding the expression by the command ``:type`` in ``GHCi`` .
```
:type not --output: not :: Bool -> Bool
:type False -- output: False :: Bool
```

#### 3.2 Basic types
- **Bool** - logical values. Bool = {True, False}
- **Char** - single characters. It contains all single characters in the Unicode system. ``´a´`` , ``´b´`` , also control characters as ``´\n´``  (move to a new line) and ``´\t´`` (move to the next tab stop).
- **String** - strings of characters. This contains all sequences of characters such as ``"abc"``.
- **Int** - fixed-precision integers. $[-2^{63}, 2^{63} -1]$ . Such as ``-100, 0, 999``, with a fixed amount of memory being used for their storage. 
- **Integer** - arbitrary-precision integers. The limit is the memory. 
- **Float** - single-precision floating-point numbers. This type contains numbers with a decimal point, ``3.1415827``.
- **Double** - double-precision floating-point numbers. It has twice as much memory as Float in order to increase their precision.

#### 3.3 List types
**A list is a sequence of elements of the same type**. We write ``[T]`` for the type of all lists whose elements have type T. For example:
```Haskell
[False, True, False] :: [Bool]
['a', 'b', 'c'] :: [Char]
["One", "Two", "Three"] :: [String]
```

```
[] -- This is called the empty-list
[[]] -- This is called a singleton list, this contains the empty list as its only element.
['a'] -- This is a singleton list, because it has a lenght of one.
```

We can also have:
```Haskell
[['a','b'],['c','d','e']] :: [[Char]]
```

**Finally, there is no restriction that a list must have a finite length.**  In particular due to the use of lazy evaluation in Haskell, lists with an infinite length are both natural and practical.

#### 3.4 Tuple types
A tuple is a **finite sequence of components of possibly different types**. For example:
```Haskell
(False, True) :: (Bool,Bool)
(False, 'a', True) :: (Bool, Char, Bool)
("Yes", True, 3) :: (String, Bool, Int)
```

The number of componentes in a tuple is called its *arity*. The tuple () of arity zero is called the empty tuple, tuple of arity two are called pairs, and so on. Tuples of arity one, such as ``(False)`` , are not permitted because they would conflict with the use of parentheses to make the evaluation order explicit, such as in ``(1+2)*3``.

We can also have:
```Haskell
('a', (False, 'b')) :: (Char,(Bool,Char))
(['a','b'],[False, True]) :: ([Char],[Bool])
[('a', False),('b', True)] :: [(Char, Bool)]
```

#### 3.5 Function types

### References
- Graham Hutton, **Programming in Haskell** (2018).