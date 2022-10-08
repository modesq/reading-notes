# class 02

## In Tests We Trust - TDD with Python

Software developers tend to be very opinionated about testing. Because of this, they have differing opinions about how important testing is and ideas on how to go about doing it. That said, let's look at three guidelines that (hopefully) most developers will agree with that will help you write valuable tests:

1. Tests should tell you the expected behavior of the unit under test. Therefore, it's advisable to keep them short and to the point. The GIVEN, WHEN, THEN structure can help with this:

    - GIVEN - what are the initial conditions for the test?
    - WHEN - what is occurring that needs to be tested?  
    - THEN - what is the expected response?

    So you should prepare your environment for testing, execute the behavior, and, at the end, check that output meets expectations.

2. Each piece of behavior should be tested once -- and only once. Testing the same behavior more than once does not mean that your software is more likely to work. Tests need to be maintained too. If you make a small change to your code base and then twenty tests break, how do you know which functionality is broken? When only a single test fails, it's much easier to find the bug.

3. Each test must be independent from other tests. Otherwise, you'll have hard time maintaining and running the test suite.

---

## If name equals main

Before executing code, Python interpreter reads source file and define few special variables/global variables.
If the python interpreter is running that module (the source file) as the main program, it sets the special __name__ variable to have a value “__main__”. If this file is being imported from another module, __name__ will be set to the module’s name. Module’s name is available as value to __name__ global variable.

A module is a file containing Python definitions and statements. The file name is the module name with the suffix .py appended.

When we execute file as command to the python interpreter,

- All of the code that is at indentation level 0 [Block 1] gets executed. Functions and classes that are defined are, well, defined, but none of their code runs.
- Here, as we executed script.py directly __name__ variable will be __main__. So, code in this if block[Block 2] will only run if that module is the entry point to your program. 
- Thus, you can test whether your script is being run directly or being imported by something else by testing __name__ variable.
- If script is getting imported by some other module at that time __name__ will be module name.

---

## Recursion

The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called a recursive function. Using a recursive algorithm, certain problems can be solved quite easily

Recursion is an amazing technique with the help of which we can reduce the length of our code and make it easier to read and write. It has certain advantages over the iteration technique which will be discussed later. A task that can be defined with its similar subtask, recursion is one of the best solutions for it. For example; The Factorial of a number.

Properties of Recursion:

- Performing the same operations multiple times with different inputs.
- In every step, we try smaller inputs to make the problem smaller.
- Base condition is needed to stop the recursion otherwise infinite loop will occur.

---