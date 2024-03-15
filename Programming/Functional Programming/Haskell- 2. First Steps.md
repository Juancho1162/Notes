#### 2.1 Prebuild Functions
```Haskell
head [1,2,3,4,5] -- output: 1
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

