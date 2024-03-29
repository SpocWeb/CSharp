# CSharp
This Repo is intended to publish small to medium-sized C# Samples and Gists. Code should be more than just a way to get a specific Problem solved. Instead it should model and explain both Problem and Solution to the Reader. The Fact that also a Computer can execute this to solve the Problem in an automated way is just a Side-Effect.

These Samples typically demonstrate a particular Coding- and Architecture Style that has evolved and is still changing according to the availability of new Languages and Idioms. One Example is the Java practice of writing Methods in small and Classes in capital Letters. 
This aligns with the german Habit of capitalizing Nouns, which takes slightly more time to type, but as we know by now (although very late), Code and Text are much more often read than written. Unfortunately the universally endorsed Microsoft C# Conventions force writing Methods with Capital Letters.

## Knowledge Capture
Programs is Knowledge captured in a Form that is applicable by Machines. By breaking it up into small, well-defined Instructions it becomes not only executable, but simultaneously (hopefully) better comprehensible for Humans. It is the purest Form of Knowledge: automated, but we aspire it to be also readable in the best possible way. Therefore the following Requirements are made: 

### Good Naming 
The Names of Classes and Methods should succinctly describe their Purpose using well-known Analogons. Method Names should be Verbs, otherwise they may rather describe querying Properties. in will take the Form `VerbObject(object arg)` so the full Invocation yields `Subject.VerbObject(arg)`

### API Documentation
Unless a Method is completely trivial and self-describing, at least a `<summary>Documentation</summary>` should be given; this is mandatory for public Methods. The Summary should fit on a single Line (up to 130 Characters). Everything else should be written into a separate multi-line `<remarks>Section</remarks>`. 

Parameter Documentation is often more tedious than helpful, especially if completeness is required by the Environment as soon as the first Parameter is described. Rather use the `<paramref name='...'>` in the Summary or Remarks to document their Role and possible considerations. 
  
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
* Functional Code is readily testable given all Parameters. 
Choosing a functional Language like F# would be the most consequent choice, but that asks for a different Repository.
In C# this often results in static Methods with multiple (often defaulted) Parameters. Sometimes multiple Overloads are necessary to provide Call-Convenience. 

* Object-Orientation provides Abstraction and Safety 
Small Classes and Structures that form a closed (mathematical) Group are excellent examples of so-called Abstract Data Types. 
Larger Classes or Hierarchies often become Monoliths AKA Blobs. 

## Coding Style:
C# is a very complex, Math-affine language with many Operators. It has a long history reaching back to 1969 when C was created at AT&T Bell Labs and lately it has been re-invigorated by Roslyn, which allows the C# Language to evolve further. 
This results in the situation that the same Logic can often be written in many different ways. 
Styles have evolved, not only for formatting the Code but also for solving small Programming Tasks, so that at least within a certain Region the same Patterns and Idioms are used. 

We acknowledge the fact that a foreign Style makes the Code harder to read, in Fact as McConnel describes, Code Language and Formatting have a major Impact on Productivity. But the Code in this Repository also serves to demonstrate alternative Solutions and hopefully inspires some Tolerance for new Idioms to support expressing Design Intent until suitable Language Features are available. 
One example is using optional Parameters (in addition to ReSharper [CanBeNullAttribute]) to express the Fact that a Parameter can be Null:
`void Method([CanBeNull] Typ value = null) { ... }`
As of C# 8 this can be expressed by declaring nullable Reference Type:
`void Method(Typ? value = null) { ... }`
This Feature adds Nullability Code Analysis similar to ReSharper but with a much more succinct Syntax.

### Brevity rules 
This corresponds to Occams Razor: explain a Phenomenon with the smallest possible Model. 

The human Brain can only handle a few 'items' concurrently, between 3 and 7. It is therefore necessary to break up Code with many Instructions and Data into manageable Pieces to be able to 'handle' it. 

* Simple procedural Code-Style caters for that, but often leads to long, unstructured Lists of Instructions. 
* Functional Style on the other hand tends to grow ever-larger Expressions that are extremely dense and hard to debug (Expressions are typically evaluated in one Step). 
Briefer Code does not necessarily mean shorter Code. The Number of Characters is very much dependent of the Naming of Objects and Methods, which should not be artificially abbreviated. Mathematicians did that for centuries, because writing and transforming Expressions with longer Names is tedious and Paper was not cheap. This tradition can still be found in naming Loop Variables `i, j` and `k`, Dimensions `x, y` and `z` and many C-Programs from the 70s and 80s. 
* OO-Style has liberated Naming so that full and combined_Names are common nowadays, beware though of `unwieldyAndUnnecessarilyLongVariableNamesThatDontAddToTheirMeaning`. 

This results in very readable Code where medium-sized Variable and Method Names are separated by Operators and/or Spaces. That makes it easy for the Reader to parse it (mentally) and understand it. 
When e.g. Operators cannot be easily distinguished from Letters, they should be surrounded by additional Spaces, even if the Compiler does not need it.  
* Brief Methods: 
Methods should fit on a single Screen. You should not need to scroll or use a tiny Font to see it at a single glance. The best Methods are single Expressions, because they are usually also `[Pure]`
* `[Pure]` Functions have no 'Side-Effects' (except e.g. temporary Memory Allocation and CPU Consumption). 
  * These Functions are stateless and can be carelessly shared and easily tested 
  

### Redundancy is bad
* SPoC (Single Point of Change)
Removing Redundancy increases Brevity (see above) and reduces the risk of inconsistencies. One goal in this Repository is to avoid implementing the same Algorithm twice. This often requires restructuring and may introduce Regression Bugs, because existing Algoritms need to be extended by new Features or hardened for new Situations. We still go to great lengths in doing this, because the resulting Algorithms will be very robust and reusable. 

### Align Code Formatting and Structure
The Reader has to (mentally) parse the Code to understand it. This starts at the highest (Folder)-Level and  goes down to Files, Methods and Lines. 
Instructions that need to be executed together are formed into Blocks. This is done in one of the following Ways, depending on the Programming Language: 
* Fortran, Basic etc use `BEGIN type` and `END type` Statements to delimit a Block  
* C-like Languages use { Braces } to indicate the Block which is briefer and more easily distinguishable from Identifiers 
* F#, Python and modern Scheme use Indentation which both enforces proper Formatting and reduces 'Noise'. 
It is common to indent Lines into Blocks, according to Coding Structure in nearly any Programming Language anyway. 
Part of Pythons appeal is its clean Layout, making Syntactical Noise like `{ ; }` obsolete. They are only needed in case you want/need to break the Style of placing one Statement into one Line. 
* Long Lines can appear due to long Identifier Names and/or complex Expressions. The latter should be avoided not only for Readability but also for Debuggability, since Expressions are evaluated atomically. Rather introduce well-named local Variables, unless in performance-critical Expressions. 
* Modern Editors can automatically wrap long Lines and if they are good, they also indent the wrapped Content. 
* Alternatively long Lines can be broken manually somewhere between 80 and 130 Characters, so the Appearance stays the same. Breaks should be placed BEFORE Operators according to [best Practices of Programmers and Mathematicians](https://legacy.python.org/dev/peps/pep-0008/#should-a-line-break-before-or-after-a-binary-operator). 

### Specific Idioms used
The following list describes a few Idioms common in this code and the Reasons behind them. Sometimes it is just remainders of best Practices in C or Java Programming. 
* `--i` instead of `i--`: Although the Compiler should optimize this to yield the same, C-Compilers may create a temporary Copy of Objects 
* `for(;;)` instead of `while(true)` Loops: In addition to being briefer, it also stands out with its Operator Syntax (instead of Keywords which can easily be confused with Identifiers) and saves you to look if there is a Variable used like in while(blue). 
* `for(int i = Count; --i >= 0;)` downward Loops: Whenever the Order is irrelevant, we use backward Loops, because: 
  * the Check for 0 is faster (although you realize it only in tight loops with few Instructions)
  * When removing or adding to a List, this saves you from worrying about the Index. 
* Enums: Although Enums are righteously frowned upon by OO purists, their Support in Visual Studio and ReSharper is excellent. They save creating a Class Hierarchy but should be used only if they are stable 
* Use Properties when applicable. Properties have many Benefits: 
  * they are displayed in the Debugger (although that may lead to unwanted Side-Effects) 
  * they save the Declaration of get-/set-Method-Pairs 
  * But they must only be used when their (repeated) Evaluation is fast, otherwise write a Get()-Method. This is actually a good Side-Channel Communication to the API-User. 
* Use Events when applicable. Like Properties, they have many Benefits: 
  * `-=` and `+=` Operators for (Un-)Subscription 
  * they should NOT propagate, but catch and Log their Exception (unlike Callbacks!)
  * Unlike Callbacks they should have an anonymous Relation with their Clients 
  * Events should ideally be processed async in a separate Thread.
* `Purposeful&lt;T>` Typing: It is helpful to use e.g. `Int&lt;T>` and `String&lt;T>` instead of simple int and string to avoid Confusion. 
  * giving the right Methods for IntelliSense 
  * avoiding accidental wrong use of Parameters (happens often with int IDs)
* `=>` Expression Syntax: This saves the `{ return ... }` Noise, especially on Properties. 
* `switch` instead of `if ... else ...`:
  * especially as of C#8 a new switch Syntax is available without fall-through or break; - Noise. 
  * Combined with `=>` Expression Syntax it becomes extremely legible.
* Using plain Names also for protected and private Fields and Methods: 
  * Visibility is often volatile and it creates only Code Churn to update all Usages
  * Using _ Prefix for private Backing Fields and Backing Methods only: These are often not needed, but when they are, it is a good Convention to name them just like the actual Properties and Methods only with a leading _ Underscore. Otherwise don't use the Underscore Prefix, even for private Members, because all-too-often Visibility changes and changing the Naming creates unnecessary Code Churn. 
* Using PASCAL_CASE for static and const Members in non-static Classes: 
  * Since the Decision for a static Member is usually not volatile, it pays of to advertise them in non-static Classes by this Convention, so they can be easily identified. 
* Use Extension Methods as much as possible: 
* Mixin: Use minimal Base-Interfaces and derived Interfaces with Default Implementations: 
  * This C# 8 Feature allows to re-use Default Implementations across Inheritance Hierarchies. 
  * It is more flexible than abstract Base Classes 
  * Unlike Extension Methods these Implementations can be overridden by more specific ones.
  
