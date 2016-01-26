# Test Driven Development

## Overview 
Yay testing! Testing is industry standard - by not testing, you will accumulate [technical debt](/concepts/technical-debt-1).

Writing tests reduces costs by:
- reducing bugs  
-  providing documentation
- improving your application design.

> It is common for programmers who are new to testing to find themselves in the unhappy state where the tests they write do cost more than the value those tests provide, and who therefore want to argue about the worth of tests.<br>
> These are programmers who believed themselves highly productive in their former test-not lives but who have crashed into the test-first wall and stumbled to a halt.<br>
> Their attempts at test-first programming result in less output, and their desire to regain productivity drives them to revert to old habits and forgo writing tests.<br>
> The solution to the problem of costly tests, however, is not to stop testing but instead to get better at it.<br>
> Getting good value from tests requires clarity of intention and knowing what, when, and how to test.<br>
> - Sandi Metz, Practical Object Oriented Design in Ruby

Furthermore, tests are crucial for maintainibility.
Having tests means that you can fearlessly refactor, because you have instant feedback if you've broken something. 
This leads to code you can work with and improve in the long term. 
When working with untested code, you are never completely sure that the changes you've made have not broken functionality. This leads to fear and stress when refactoring, extending and maintaining untested code bases. 

Well written tests tell a story of the behaviour and functionality of your app.
Tests and good naming of functions and variables make up the living documentation of your app.

Tests improve application design by forcing you to write code, where each function has a single testable responsibility. This is why it is important that **tests are written before the code** - hence "Test Driven Development".
Modular code written to pass tests is cleaner, more robust and easier to maintain.

## Prerequisites 
none

## Capabilities
You are comfortable using the command line tool to:

- Understand the benefits of testing

## Resources 
- [Sandi Metz - Rules for good testing](https://gist.github.com/Integralist/7944948)
