# inline-clr

`inline-clr` provides a quasiquoter to inline C# and F# code in Haskell modules. Inspired by [`inline-c`](http://hackage.haskell.org/package/inline-c), [`inline-r`](http://hackage.haskell.org/package/inline-r) and  [`inline-java`](http://hackage.haskell.org/package/inline-java).

## Examples

```haskell
{-# LANGUAGE DataKinds   #-}
{-# LANGUAGE QuasiQuotes #-}

module Main where

import Data.Int (Int32)
import Data.String (fromString)
import Foreign.CLR (withCLR)
import Language.CLR.CSharp.Inline
import System.Environment (getArgs)

main :: IO Int32
main = do
  args <- getArgs
  withCLR (map fromString args) $ 
    [csharp|
     -- C# code goes here
    |]
```

