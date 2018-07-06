# Fold Right

``` haskell
>> foldr (+) 0 [1, 2, 3, 4, 5]
(1 + (2 + (3 + (4 + (5 + 0))))) 

= 1 + (foldr (+) 0 [2, 3, 4, 5])
= 1 + 2 + (foldr (+) 0 [3, 4, 5])
= 1 + 2 + 3 + (foldr (+) 0 [4, 5])
= 1 + 2 + 3 + 4 (foldr (+) 0 [5])
= 1 + 2 + 3 + 4 + 5 (foldr (+) 0 [])
= 1 + 2 + 3 + 4 + 5 + 0
```

# Fold Left

``` haskell
>> foldl (+) 0 [1, 2, 3, 4, 5]
(((((0 + 1) + 2) + 3) + 4) + 5)

= foldl (+) (0 + 1) [2, 3, 4, 5]
= foldl (+) (0 + 1 + 2) [3, 4, 5]
= foldl (+) (0 + 1 + 2 + 3) [4, 5]
= foldl (+) (0 + 1 + 2 + 3 + 4) [5]
= foldl (+) (0 + 1 + 2 + 3 + 4 + 5) []
= 0 + 1 + 2 + 3 + 4 + 5
```

Fold left reversing a list
``` haskell
>> foldl (flip (:)) Nil [1, 2, 3, 4, 5]
(5 : (4 : (3 : (2 : (1 : Nil)))))

= foldl (flip (:)) (1 : Nil) [2, 3, 4, 5]
= foldl (flip (:)) (2 : 1 : Nil) [3, 4, 5]
= foldl (flip (:)) (3 : 2 : 1 : Nil) [4, 5]
= foldl (flip (:)) (4: 3 : 2 : 1 : Nil) [5]
= foldl (flip (:)) (5 : 4 : 3 : 2 : 1 : Nil) []
= (5 : 4 : 3 : 2 : 1 : Nil)
```
