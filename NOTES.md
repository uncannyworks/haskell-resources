# Notes

## Category Theory for Programmers (Bartosz Milewski)

> The details of our understanding of the human short-term memory might be changing, but we know for sure that it’s limited. The bottom line is that we are unable to deal with the soup of objects or the spaghetti of code. We need structure not because well-structured programs are pleasant to look at, but because otherwise our brains can’t process them efficiently. We often describe some piece of code as elegant or beautiful, but what we really mean is that it’s easy to process by our limited human minds. Elegant code creates chunks that are just the right size and come in just the right number for our mental digestive system to assimilate them.

> In object-oriented programming, an idealized object is only visible through its abstract interface (pure surface, no volume), with methods playing the role of arrows. The moment you have to dig into the implementation of the object in order to understand how to compose it with other objects, you’ve lost the advantages of your programming paradigm.

> One of the important advantages of having a mathematical model for programming is that it’s possible to perform formal proofs of correctness of software. This might not seem so important when you’re writing consumer software, but there are areas of programming where the price of failure may be exorbitant, or where human life is at stake. But even when writing web applications for the health system, you may appreciate the thought that functions and algorithms from the Haskell standard library come with proofs of correctness.

## Interview with Edward Kmett

https://theinitialcommit.com/2017/01/10/edward-kmett/

> Before I found Haskell I believed that every programming language I learned was really just a matter of figuring out the syntax and few peculiar local idioms. Trying to wrestle with Haskell in that same way was an exercise in futility. People kept telling me that and I just didn’t get it.

> I love that there always something to learn. But I think the thing that I love most about this community is that it goes out of its way to destroy the notion that there is a dichotomy between the elegant solution and a fast solution. The Haskell community will keep throwing people with PhD’s at a problem until they come up with a way to make the elegant solution compile into the fast solution – and the type system offers enough structure that unlike most other popular languages, these code transformations are possible and safe.

> The thing I think most people hate about this community is that there is always something else you feel you HAVE to learn.
