# CSharp
This Repo is intended to publish small to medium-sized C# Samples and Gists

These Samples typically demonstrate a particular Coding- and Architecture Style that has evolved and is still changing according to the availability of new Languages and Idioms. One Example is the Java practice of writing Methods in small and Classes in capital Letters. 
This aligns with the german Habit of capitalizing Nouns, which takes slightly more time to type, but as we know by now (although very late), Code and Text are much more often read than written. 

## Architecture Style:
Architecture Guidelines provide a perspective for deciding over alternative Approaches and focusing Resources. 
* Functional Code provides best Composability. 
Choosing a functional Language would be the most consequent choice, but that asks for a different Repository.
In C# this often results in static Methods with multiple (often defaulted) Parameters. Sometimes multiple Overloads are necessary to provide Call-Convenience. 

* Object-Orientation provides Abstraction and Safety 
Small Classes and Structures that form a closed (mathematical) Group are excellent examples of so-called Abstract Data Types. 
Larger Classes or Hierarchies often become Monoliths AKA Blobs. 

## Coding Style:
C# is a very complex language. It has a long history reaching back to 1969 when C was created at AT&T Bell Labs and lately it has been re-invigorated by Roslyn, which allows the C# Language to evolve further. 
This results in the situation that the same Logic can often be written in many different ways. 
Styles have evolved, not only for formatting the Code but also for solving small Programming Tasks, so that at least within a certain Region the same Patterns and Idioms are used. 

We acknowledge the fact that a foreign Style makes the Code harder to read, in Fact as McConnel describes, Code Language and Formatting have a major Impact on Productivity. But the Code in this Repository also serves to demonstrate alternative Solutions and hopefully inspires some Tolerance to new, experimental Idioms. 

### Brevity rules 
This is the to Occams Razor: explain a Phenomenon with the briefest possible Model. 

The human Brain can only handle a few 'items' concurrently, between 3 and 7. It is therefore necessary to break up Code with many Instructions and Data into manageable Pieces to be able to 'handle' it. 

* Simple procedural Code-Style caters for that, but often leads to long, unstructured Lists of Instructions. 
* Functional Style on the other hand tends to grow ever-larger Expressions that are extremely dense and hard to debug (Expressions are typically evaluated in one Step). 
Briefer Code does not necessarily mean shorter Code. The Number of Characters is very much dependent of the Naming of Objects and Methods, which should not be artificially abbreviated. Mathematicians did that for centuries, because writing and transforming Expressions with longer Names is tedious and Paper was not cheap. This tradition can still be found in naming Loop Variables i, j and k, Dimensions x, y and z and many C-Programs from the 70s and 80s. 
* OO-Style has also liberated Naming so that full and combined_Names are common nowadays, beware though of unwieldyAndUnnecessarilyLongVariableNamesThatDontAddToTheirMeaning. 

This results in very readable Code where medium-sized Variable and Method Names are separated by Operators and/or Spaces. That makes it easy for the Reader to parse it (mentally) and understand it. 
When e.g. Operators cannot be easily distinguished from Letters, they should be surrounded by additional Spaces, even if the Compiler does not need it.  

### Redundancy is bad
* SPoC (Single Point of Change)
Removing Redundancy increases Brevity (see above) and reduces the risk of inconsistencies. One goal in this Repository is to avoid implementing the same Algorithm twice. This often requires restructuring and may introduce Regression Bugs, because existing Algoritms need to be extended by new Features or hardened for new Situations. We still go to great lengths in doing this, because the resulting Algorithms will be very robust and reusable. 

### Align Code Formatting and Structure
The Reader has to (mentally) parse the Code. This starts at the highest (Folder)-Level and  goes down to Files, Methods and Lines. 
Instructions that need to be executed together are formed into Blocks. This is done in one of the following Ways, depending on the Programming Language: 
* Fortran, Basic etc use `BEGIN type` and `END type` Statements to delimit a Block  
* C-like Languages use { Braces } to indicate the Block which is briefer
* F#, Python and modern Scheme use Indentation which enforces proper Formatting. 
It is common to indent Lines into Blocks, according to Coding Structure in nearly any Programming Language anyway. 
Part of Pythons appeal is its clean Layout, making Syntactical Noise like {;} obsolete. 
