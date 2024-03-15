#### 2.1 Prebuild Functions
```Haskell
head [1,2,3,4,5] -- output: 1
last [1,2,3,4,5] -- output: 5
init [1,2,3,4,5] -- output: [1,2,3,4]
tail [1,2,3,4,5] -- output: [2,3,4,5]
[1,2,3,4,5] !! 2 -- output: 3 (nth element, in this case 2th element(0,1,...))
[1,2,3,4,5] !! 4 -- output: 5
[1,2,3,4,5] !! 0 -- output: 1
take 3 [1,2,3,4,5] -- output: [1,2,3] (select first n elements of a list)
drop 3 [1,2,3,4,5] -- output:[4,5]
length [1,2,3,4,5] -- output: 5 (not considering index (0,1,2,3,...))
sum [1,2,3,4,5] -- output: 15
product [1,2,3,4,5] -- output: 120
[1,2,3] ++ [4,5] -- output: [1,2,3,4,5]
reverse [1,2,3,4,5] --output: [5,4,3,2,1]
```

#### 2.2 Function application

| Math        | Haskell   |
| ----------- | --------- |
| $f(x)$      | f x       |
| $f(x) + b$  | f x + b   |
| f$(x,y)$    | f x y     |
| $f(g(x))$   | f (g x)   |
| $f(x,g(y))$ | f x (g y) |
| $f(x) g(y)$ | f x * g y |
| $f(x+b)$    | f (x+b)   |


#### 2.3 Using ghci (script.hs + :reload (2 terminals))
```Haskell
-- script_1.hs
double x = x + x
quadruple x = double (double x)
factorial n = product [1..n]
average ns = div (sum ns) (length ns)
average2 ns = sum ns `div` length ns
```

Now we can play in the terminal (ghci) with some calculations:
```haskell
factorial 4 --output:24
quadruple 2 --output: 8
average [1,2,3,4,5] --output 3 (1+2+3+4+5)/5 =15/5 = 3
-- same for average2
```


##### **GHCi commands**

| Command          | Meaning               |
| ---------------- | --------------------- |
| :load name       | load script name      |
| :reload          | reload current script |
| :set editor name | set editor to name    |
| :edit name       | edit script name      |
| :edit            | edit current script   |
| :type expr       | show type of expr     |
| :?               | show all comands      |
| :quit            | quit GHCi             |

##### **List of special meaning keywords**
```
case  class  data  default  deriving
do  else  foreign  if  import  in
infix  infixl  infixr instance let
module newtype  of  then  type  where
```
By convention, list argument in Haskell usually have the suffix **s** on their name to indicate that they may contain multiple values. For example, a list of numbers might be named as **ns**, a list of arbitrary values might be named **xs**, and a list of lists of characters might be named **css**.


##### **The layout rule**
Within a script, each definition at the same level must begin in precisely the same column. This layout rule makes it possible to determine the grouping of definitions from their indentation. For example:
```Haskell
a = b + c
	where
		b = 1
		c = 2
d = a * 2
```

It is clear from the indentation that b and c are local definitions for use within the body of a. If desired, such grouping can be made explicit by enclosing a sequence of definitions in curly parentheses and separating each definition by a semi-colon:
```Haskell
a = b + c
	where
		{b = 1;
		 c = 2};
d = a * 2
```

Or even:
```Haskell
a = b + c where {b = 1; c = 2}; d = a * 2
```

##### **Do not use Tabs**
Configure the editor to replace tabs for spaces.

##### **Comments**
```
-- Bla bla bla
{-
Bla bla bla
-}
```

#### 2.4 Exercises

**EXERCISE 3**: Fix this 3 errors:
```Haskell
N = a `div` length xs 
	where
		a = 10
	   xs = [1,2,3,4,5]
```
**Solution**
```Haskell
n = a ´div´ length xs -- functions need to start by lowecase, Datatypes Uppercase
-- you need to use ´ ´ not ` `, to operate with div
	where
		a = 10
		xs = [1,2,3,4,5] -- you need to indent at the same level
```

**EXERCISE 4**: The library function last selects the last element of a non-empty list. Show how the function last could be defined in terms of the other library functions introduced in this chapter: 
**Solution**:
```Haskell
 my_last xs = head (reverse xs)
```

**EXERCISE 5**: The library function init removes the last element from a non empty list; for example, 
$init [1,2,3,4,5] = [1,2,3,4]$. Show how init could similarly be defined in two different ways:
**Solution 1** :
``` Haskell
my_init xs = reverse (tail (reverse xs))
```
**Solution 2**:
```Haskell
my_init2 xs = take (length xs - 2) xs
```

### References
- Graham Hutton, **Programming in Haskell** (2018).