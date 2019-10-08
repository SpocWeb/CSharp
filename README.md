# CSharp
This Repo is intended to publish small to medium-sized C# Samples and Gists

These Samples typically demonstrate a particular Coding- and Architecture Style that has evolved and is still changing according to the availability of new Languages and Idioms. One Example is the Java practice of writing Methods in small and Classes in capital Letters. 
This aligns with the german Habit of capitalizing Nouns, which takes slightly more time to type, but as we know by now (although very late), Code and Text are much more often read than written. 

## Knowledge Capture
Programs is Knowledge captured in a Form that is applicable by Machines. By breaking it up into small, well-defined Instructions it becomes not only executable, but simultaneously (hopefully) better comprehensible for Humans. It is the purest Form of Knowledge: automated, but we aspire it to be also readable in the best possible way. Therefore the following Requirements are made: 

### Good Naming 
The Names of Classes and Methods should succinctly describe their Purpose using well-known Analogons. Method Names should be Verbs, otherwise they may rather describe querying Properties. in will take the Form VerbObject(object arg) so the full Invocation yields Subject.VerbObject(arg)

### API Documentation
Unless a Method is completely trivial and self-describing, at least a &lt;summary>Documentation&lt;/summary> should be given; this is mandatory for public Methods. The Summary should fit on a single Line (up to 130 Characters). Everything else should be written into a separate &lt;remarks>Section&lt;/remarks>. 

Parameter Documentation is often more tedious than helpful, especially if completeness is required by the Environment as soon as the first Parameter is described. Rather use the <paramref name='...'> in the Summary or Remarks to document their Role and possible considerations. 
  
### Tests as Documentation
Unit Tests provide for a very concrete Documentation by showing the expected Result for a given Set of Parameters. Therefore Tests should be written close to the Implementation. Rather use conditional Compilation if the Test Cases must not be delivered with the compiled DLL. 

### Conceptual Documentation
API Documentation is sufficient only for well-known Domains. For new Users or very detailed Designs a conceptual Documentation is needed. Its Purposes are, among others: 
* Description above Class-Level 
* Introduction into Domain 
* Reasoning about Design-Decisions 

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
The Reader has to (mentally) parse the Code to understand it. This starts at the highest (Folder)-Level and  goes down to Files, Methods and Lines. 
Instructions that need to be executed together are formed into Blocks. This is done in one of the following Ways, depending on the Programming Language: 
* Fortran, Basic etc use `BEGIN type` and `END type` Statements to delimit a Block  
* C-like Languages use { Braces } to indicate the Block which is briefer
* F#, Python and modern Scheme use Indentation which enforces proper Formatting. 
It is common to indent Lines into Blocks, according to Coding Structure in nearly any Programming Language anyway. 
Part of Pythons appeal is its clean Layout, making Syntactical Noise like {;} obsolete. 
