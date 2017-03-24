Martin, Robert C. Clean code : a handbook of agile software craftsmanship. Upper Saddle River, NJ: Prentice Hall, 2009.

## Chapter 5 - Formatting

Agreeing on sipmle set of formatting rules and all members should apply.

Your style and discipline survives, even though your code does not.

Some code metrics to smell: (loc)
  * average file size
  * smallest file size
  * largest file size
  * horizontal line width

Small files are usually easier to understand than large files.

**(?)** Protected variables should be avoided. **Why?** Vertical distance. Closely related concepts should be kept vertically close to each  other. (in the same source file)

The code itself makes the best coding standard document.

## Chapter 6 - Objects and Data Structures

The methods enforce an access policy. Think about atomic operations.

**Law of Demeter:** A module should not know about the internals of the objects it manipulates. A method *f* of a class *C* should only call the methods of these:
  * *C*
  * an object created by *f*
  * an object passed as an argument to *f*
  * an object held in an instance variable of *C*

In short; talk to friends, not to strangers.

Avoid *train wrecks*. Also splitting train wrecks does not give any benefit according to *Law of Demeter*. It's still violation. Still that's a lot of knowledge for one function to know.

**Data Transfer Objects:** Data structures with public variables and no functions. Also known as, *bean* forms.

## Chapter 7 - Error Handling

Use exceptions rather than return codes. In the past there were languages that didn't have exceptions. In those languages error flags or return codes used. Caller could check that.

*Try* blocks are like transactions. Your *catch* has to leave your program in a consistent state.

Java's checked exceptions causes violation of *Open/Closed Principle*. Also it breaks encapsulation. Because all functions in the path of a throw must know about details of that low level exception. It generates dependency costs.

Exceptions you throw should be informative about context.

(Try to) Don't return nulls. Prefer special case objects. For example; empty array, empty string.

## Chapter 8 - Boundaries

We should try to encapsulate 3rd party API's objects that future changes won't affect entire codebase. We should keep impact at wrapper layer.

Third-party code helps us get more functionality delivered in less time.

Using code that does not exist -> Adapter Pattern

You design your interface. When the 3rd party not suitable, you bring adapter class which implements your interface and encapsulates other API.

Good software design, accommodate change without huge investments and rework. We should take care of and protect our investment by making sure future change is not too costly.

*Why wrapper to API?* It's better to depend on something you control than on something you don't control, which ends up controlling you.

## Chapter 9 - Unit Tests

Having dirty, throw-away like, tests is equivalent to having no tests. The problem is that tests must change as the production code evolves. The dirtier the tests, the harder they are to change. In the end, you will discard test suite.

Test code is just as important as production code.

Tests make refactoring eligible. If you have tests, you do not fear making changes to the code. Without tests  every change is a possible bug.

Usually the structure of a test is something like *build-operate-check* pattern.

Single concept in each test function.

Clean tests follows *FIRST* acronym:
  * **F**ast
  * **I**ndependent   (<- Is this violation of reusability of tests **?**)
  * **R**epeatable
  * **S**elf-validating
  * **T**imely
