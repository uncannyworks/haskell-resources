# Haskell Style Guide

If something is not clear please examine the code base this is attached to in order to get a feel for how things should be written.

Modifed version of https://github.com/tibbe/haskell-style-guide/blob/master/haskell-style.md

## Formatting

### Line Length

Maximum line length is *80 characters*. This forces a style where you make things readable.

Rare exception: When pattern matching long/nested data types.

### Indentation

Tabs are illegal. Use spaces for identing. Indent your code blocks with *2 spaces*.

```haskell
sayHello :: IO ()
sayHello = do
  name <- getLine
  putStrLn $ greeting name
  where
    greeting name = "Hello, " ++ name ++ "!"
    
filter :: (a -> Bool) -> [a] -> [a]
filter _ [] = []
filter p (x:xs)
  | p x       = x : filter p xs
  | otherwise = filter p xs
```

### Blank Lines

One blank line between top-level definitions. No blank lines between type signatures and function definitions. Add one blank line between functions in a type class instance declaration if the function bodies are large. Use your judgement.

### Whitespace

Surround binary operators with a single space on either side. Use your better judgement for the insertion of spaces around arithmetic operators but always be consistent about whitespace on either side of a binary operator. Don't insert a space after a lambda.

### Data Declarations

Single newtype or data constructors can be written on a single line.

```Haskell
newtype UserId = UserId Int

data Person = Person String String Int
```

If more than one constructor align the data constructors one line down and indented *2 spaces*.

```Haskell
data Tree a
  = Branch !a !(Tree a) !(Tree a)
  | Leaf
```

Format records as follows:

```Haskell
data Person
  = Person
  { firstName :: !String  -- ^ First name
  , lastName  :: !String  -- ^ Last name
  , age       :: !Int     -- ^ Age
  } deriving (Eq, Show)
```

### List Declarations

Align the elements in the list. Example:

```Haskell
exceptions =
  [ InvalidStatusCode
  , MissingContentHeader
  , InternalServerError
  ]
```

Small easy to read lists can remain on one line. Example:

```Haskell
example = [ Foo, Bar, Baz ]
```

### Hanging Lambdas

You may or may not indent the code following a "hanging" lambda. Use your judgement. Some examples:

```Haskell
bar :: IO ()
bar =
  forM_ [1, 2, 3] $ \n -> do
     putStrLn "Here comes a number!"
     print n

foo :: IO ()
foo =
  alloca 10 $ \a ->
  alloca 20 $ \b ->
  cFunction a b
```

### Export Lists

Format export lists as follows:

```Haskell
module Data.Set
  (
    -- * The @Set@ type
    Set
  , empty
  , singleton

    -- * Querying
  , member
  ) where
```

### If-then-else clauses

Generally, guards and pattern matches should be preferred over if-then-else clauses, where possible. Short cases should usually be put on a single line (when line length allows it).

When writing non-monadic code (i.e. when not using do) and guards and pattern matches can't be used, you can align if-then-else clauses like you would normal expressions:

```Haskell
foo =
  if ...
  then ...
  else ...
  
bar =
  if ...
  then do
    ...
  else do
    ...
```

### Case expressions

Single simple expressions:

```Haskell
foobar =
  case something of
    Just j  -> foo
    Nothing -> bar
```

Complex expressions:

```Haskell
foobar =
  case something of
    Just j  -> do
      foo a b c
    Nothing -> do
      bar d e f
```

Aligning arrows to help readability is ok.

### Imports

Imports should be grouped in the following order:

1. standard library imports
2. related third party imports
3. local application/library specific imports

Put a blank line between each group of imports. The imports in each group should be sorted alphabetically, by module name.

### Naming

Use camel case (e.g. functionName) when naming functions and upper camel case (e.g. DataType) when naming data types.

For readability reasons, don't capitalize all letters when using an abbreviation. For example, write HttpServer instead of HTTPServer. Exception: Two letter abbreviations, e.g. IO.

Keep variables purposefully short and un-descriptive. If documenting what a variable does is required, prefer type synonyms instead. Example:

```Haskell
type FirstName = Text
type LastName  = Text
type Age       = Int

mkPerson :: FirstName -> LastName -> Age -> Person
mkPerson f l a = Person f l a
```

### Functions

Prefer keeping the short descriptive logic immediatley after the definition.

```Haskell
foo :: String -> [String]
foo s = bar . baz $ s
  where
    bar = ...
    baz = ...
```

If type signatures are too long format each argument one per line. Example:

```Haskell
drawAnimation :: SDL.Renderer
              -> Maybe SpriteSheet
              -> Maybe ScreenPosition
              -> Maybe [Sprite]
              -> Animation
              -> IO ()
```
