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
1.  *Use exceptions rather than error codes.*
    Exceptions force the caller to deal with them immediately, but an error code can easily get ignored, leading to problems down the line.
2.  *Extract try-except blocks.*
    Error processing should be distinct from regular processing (cf. "Functions should do one thing"; error handling is a thing). Plus, the fewer lines in the `try-except` block, the less the possibilities of additional exceptions slipping through.
3.  *Provide context when you raise an exception.*
    Use informative error messages, that describe the intent of the operation that failed.


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


Objects vs Data Structures
--------------------------
1.  *Distinguish between objects, which hide their data behind abstractions and expose functions that operate on that data, and data structures, which expose their data and have no meaningful functions.*
2.  *Law of Demeter: A module should not know about the innards of the objects it manipulates.*.
    For instance, a method `f` of class `C` should only call the methods of `C`, an object created by `f`, an object passed as argument to `f`, or an instance variable of `C`.


Third-Party Code & UndevelopedCode
----------------------------------
1.  *Constrain the behavior of the outside code with tests.*
    Use "learning tests," where you write tests as you figure out the API of the code. Then, when you understand the outside code, you have a series of unit tests that will quickly tell you if the outside code has changed due to an update in an important way.
2.  *Define a "dream api" for yet-unwritten code.*
    This lets you continue working on outside areas, and allows the unwritted code to be modular with respect to the rest of the code base.


Tests & Test-Driven Development
-------------------------------
1.  *Follow TDD.*
    The three laws of TDD are:
    1.  You may not write production code until you have written a failing unit test.
    2.  You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
    3.  You may not write more production code than is sufficient to pass the currenlty failing test.

    Following these laws will give you hundreds of tests, covering all of your code base.
2.  *Keep the tests clean and readable.*
    The tests need to follow the same high standards for cleanliness as the rest of the code. Otherwise, when the code changes, it will be difficult to chnage the tests to keep up.
3.  *There should be one assert per test, which should test one concept.*
    This makes it much easier to see what aspect of the code is failing. If this leads to duplication, split the duplication out into test-suite-specific objects or functions. And no cheating with `and` in the assert statement.
4.  *Tests should be fast.*
    They should run quickly enough where you can run them all the time. A few seconds for the entire test suite is the upper limit on speed.
5.  *Tests should be independent.*
    One test should not set up the conditions for the next test. Each tests should produce the same result independent of the ordering in which the tests were run.
6.  *Tests should be repeatable.*
    They should test the same thing in any environment. Repeatability also means that if you're using randomness, you must set the seed to a specific value.
7.  *Tests sould be self-validating.*
    The test should give a boolean output of pass or fail. You should not have to process the test results to see if it fails.
8.  *Tests should be timely.*
    Write the tests *before* you write the production code, or, worse case, right after. Don't do it 6 months later.
9.  *Writing tests is liberating. It allows you to change the code freely -- if it doesn't break a test, then go ahead and change the code.*
    This is Brian's experience as well :)



Classes
-------
1.  *Classes should be small.*
    As a ballpark, classes should be < 100 lines. Since we said before functions should be <20 lines, a code smell is if the class has more than 5-ish methods.
2.  *Classes should have a single responsibility.*
    As a code smell, look at the class name. The class name should describe one responsibility of the class. If you can't write a concise name, then perhaps the class is too large. A class names that includes `Processor`, `Manager`, or `Super` is a hint that the class has multiple responsibilities. Since a class has a single responsibility, its code should have only one reason to change.
3.  *Classes should have a small number of instance variables.*
4.  *Classes should be cohesive.*
    Measure cohesion by how many methods use what fraction of the instance variables. In a maximally cohesive class, all the methods use all the instance variables. If you can split the methods and instance variables into two non-intersecting groups, that's a good sign your class is too big.
5.  *Maintaining cohesion results in many small classes.*


Files
-----
1.  *Small files are good.*
    It's easier to understand what goes on in a small file than in a large one. Uncle Bob's examples are files usually less than 200 lines.


