# CSYE7200FunctionComposition
Assignment 5 (Functional Composition)  

All the work you are going to do is in the asstfc package. Ingest hasn't changed, but Movie (and MovieSpec -- also inasstfc) have.

There are 13 TODOs in Function.scala and 2 TODOs in Movie.scala. You can get these from the class repo (see Course Material/Resources/Class Repository), the module name for this assignment is assignment-functional-composition.

Did you find it at all bothersome (in Assignments 1 and 2) that we didn't use Try (or Option) to deal with some of the String => Int conversions? Some of those invocations of toInt might easily have thrown exceptions. Part of the problem was that it was too difficult to do, given your knowledge of Scala at the time.

But now, you know all about functional composition, for comprehensions and monads.

The basic problem that I had to solve is that some of the apply functions (for example in Format) have a mixture of strings, as well as Int and Double which require conversion from String. One of the elements of a Movie (viz. Reviews) was based on seven Int conversions from seven strings. That's easy: just use map7 (!). Of course we didn't actually implement map7 in class, but you're going to implement it in this assignment. But what about mixtures like in Format? That required a rather creative solution (if I may say so). Take a look at the code in the object Format and also in the object Production. First, we need to curry the apply method. Functions in curried form are much more tractable than functions in tupled (normal) form. Now, the rest of the code transforms that curried function into a function that can be used in a for comprehension. Don't worry too much if you don't understand what's going on here. But, I believe that if you take the time to figure it out, you can see what's happening.

In any case, this code uses some utilities that I placed in the Function object.

Now, here's an important hint for the one TODO that is in the Movie.scala file: Back in assignment 2, we had a for comprehension which utilized a filter (you can see that by taking a look at Movie. scala in assignment-movie-database which is unchanged). At the time, we hadn't talked about for comprehensions but hopefully you figured it out (it is kind of obvious).

But do you remember in a recent lecture that I said that the left hand side of a generator (in a for comprehension) is actually a pattern? Yes, it's a pattern just like in the case statement of a match expression. Neat, huh? So, you are going to implement the filter on the country value by using a pattern in the for comprehension instead of a filter (thus you will not be using the method isKiwi or anything like it). Do take a look at how it was implemented (using a filter) in our previous version.

But there's one tricky bit of syntax which we haven't covered yet. In Scala there can arise a certain ambiguity when you have identifiers that are the same as keywords (not allowed in Java) or, as here, you have a variable mentioned in a pattern matching context where you don't want just to match on anything (you would be "shadowing" the variable in such a case). You actually want to match on the value of the variable. For this (and the similar case where you want to use a keyword as a variable), just enclose the variable name inside back-ticks the "`" character.
