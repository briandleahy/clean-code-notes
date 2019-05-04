General
-------
1.  *Leave the codebase cleaner than you found it.*
2.  *Clarity is king.*
3.  *Iteratively improve your code, just you would iteratively improve a paper draft.*


Names
-----
0.  *It's hard to overestimate the value of good names.*
    So use good names. A long, descriptive name is better than a short, enigmatic one.
1.  *Use intention-revealing names.*
    Single-character names do not reveal intention.
2.  *Avoid disinformation.*
    Don't use an abbreviation or variable name that implies the variable is something else.

3.  *Make meaningful distinctions in variable names.*
    * Don't do number-series naming (e.g. `x1` and `x2`); they are not intention-revealing.
    * Eliminate "noise words" that don't explain what the variable is (e.g. use `Name` rather than `NameString`).

4.  *Use pronounceable names.*
    If you can't pronouce the variable name, it's probably not a clear, meaningful, intention-revealing variable name.
5.  *Use searchable names.*
    It's much easier to grep for `MAX_CLASSES_PER_STUDENT` than for `7`.
6.  *Avoid encodings.*
    No Hungarian notation plz.
7.  *Class names should be nouns or noun phrases.*
8.  *Method names should be verbs or verb phrases.*
    Accessors, mutators, and predicates should be named for the value and prefixed with `get`, `set`, and `is`.
9. *For functions which take arguments, the function name and argument should make a verb-object pair.*
10.  *Pick one word per concept.*
    "For instance, it's confusing to have `fetch`, `retrieve`, and `get` as equivalent methods of different classes.`
11. *Don't pun.*
    Don't use the same word to mean two different things in different names.

Functions
----------
1. *Functions should be small; shoot for <20 lines.*
2. *Functions should do 1 thing and 1 thing only.*
    Corrolary to points 1 and 2: `if`, `else`, `while`, `for`, etc blocks should be 1 line long, calling an additional sub-method.
3.  *There should be 1 level of abstraction per function.*
    Functions which are about big-picture things should not have low-level
    details in them.
4.  *The fewer arguments to a function, the better.*
    The ideal number of arguments to a function is 0, followed by 1 and 2. Three arguments should be avoided wherever possible. Four or more arguments is a code smell. Why? It's hard to remember which argument is which -- is it `copy(src, dest)` or `copy(dst, src)`? Worse, when you test, you need to have a combinatoric number of tests to capture all the possible behavior. When a function needs multiple arguments, it is likely that some of those arguments should be wrapped in a class as their own. For example, `make_circle(x, y, radius)` could be `make_circle(center, radius)` where `center` is a `Point` object.
5.  *Avoid output arguments.*
6.  *Avoid boolean flag arguments.*
    This is a code smell that the function does more than one thing (it does something when `flag=True`, and something else when `flag=False`). It also doubles the amount of unit tests requires.
7.  *Functions should have no side effects.*
8.  *Don't repeat yourself.*
    Duplicated code should be split out into a separate function.


Exceptions & Errors
--------------------
1.  *It's better to raise an exception than return an error code.*
    Exceptions force the caller to deal with them immediately, but an error code can easily get ignored, leading to problems down the line.
2.  *Extract try-except blocks.*
    Error processing should be distinct from regular processing (cf. "Functions should do one thing"; error handling is a thing). Plus, the fewer lines in the `try-except` block, the less the possibilities of additional exceptions slipping through.

Comments
--------
1.  *Comments are a necessary evil.*
    Comments compensate for our failure to express ourself in code. It's better to write clean, expressive code than to have abstruse code with clarifying comments.
2.  *Be careful with comments; comments lie.*
    Comments are not code, so they can lie about what the code is actually doing. Be careful with comments as the code can change and the comments can stay the same.
3.  *Comments do not make up for bad code.*
4.  *It's better to change the name of the method, variable, etc to describe the code than to write the same thing in a comment.*
5.  *Comments that explain design choices, warn of consequences, or that emphasize aspects of the code are good.*
6.  *TODO, FIXME, etc comments are OK.*
7.  *Comments which mumble, repeat what the code says, are misleading or imprecise, or which can be eliminated in favor of more descriptive variable names are probably not necessary.*
    But do use a more descriptive variable name :).
8.  *Commented out code is a code smell.*
    We have git. Use it. Delete the commented out code. The rest of code will keep changing and soon the commented code will be outdated.
9.  *Comments should be near the code they describe.*

Formatting
----------
1.  *Follow the standard.*
    In Python we have pep8. Use it.
2.  *Play as a team.*
    If the team agrees on a formatting standard, stick to it!
3.  *Place vertical space between concepts.*
    Separate groups of related statements with an empty line, just like you would separate groups of related sentences with a paragraph break. The converse of this is to
4.  *Remove vertical space between associated concepts.*
5.  *Code should be readable from top to bottom.*
    The methods at highest level of abstraction should be at the top of the file, and the level of abstraction should decrease towards the bottom of the file.
6.  *Related concepts and methods should appear nearby in the file.*



Files
-----
1.  *Small files are good.*
    It's easier to understand what goes on in a small file than in a large one. Uncle Bob's examples are files usually less than 200 lines.

