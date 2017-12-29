Here's my own copy of the main Nim repository. See original at https://github.com/nim-lang/Nim

* Fixed: main module name can start with a digit. Proabably also with underscore, but that needs test.

Some notes...

* No `%` and `//` ops, only `mod` and `div`. Aha, there's `%%`. Where then `//`? (Aha, rationals. Never-used :) Can define own div)    
* Other ops... we'll see. Documentation on expressions is absent, or split over different parts.
* Parameters are const. WTF! I have to create a mutual copy not only for complex data, but even for ints! Yes, this feature sucks but I see the idea and not clear how to fix it. Also weird: variables -- `var i: int`, arguments -- `i: var int`.
* `discard` is disgusting. Why not `skip`?  
* `incl` for sets must be `add` (as well). OK, can have alias.. probably.
* No `loop`/`forever`, again stupid `while true`. GSD it's not True. Ok, can be defined with template.
* Probably must be reverse: `@[...]` <--> `[...]`. Aha, `@` is op. Interesting. But still not sure if wise.  
* `const A=1,B=2,C=3` should work!
* as well as `var a=1, b=2`. Let's do it!
* really annoying that you can't write `a=-1` or `b+=+1` or `c=@[]` -- there must be ' ' after '='. This should be fixed!
* `foldl`, `map`, `split`, `join`, `sum`, `^` (power) `%%` and `//` for ints must be in system module. Also `<< >> & | ~ (xor)`
* `var a: enum A,B` -- internal error pfffff. Reported.
* also error with `a=a*b` vs `a*=b` under `overflowchecks`.
* `type S = 0..1 \n var good: array[S,S] = [S(0),S(1)] \n var bad: array[S,S] = [0,1]` -- should work too! in definition
* what's wrong with `for i in 0..10: if a[i]>0: echo a[i]; t+=a[i] else: echo "!",i`? what can be misunderstood there?
* Ids have case-sensitive first letter, the tail is case-insensitive and underscores `_` inside it are ignored. Wow this is weird!
