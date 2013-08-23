## [Single responsibility principle][3]

SRP is very easy to understand but very hard to follow during a project rush.
Classes get fat, each developer adds their own methods and eventually objects become
freaky monsters.

### A bad practice

Because I don't want to copy-paste 3200 lines of code here, I'll give you an example
of bad pratices in the Doctrine2 ORM project : [UnifOfWork][4]. More than 3k of
switches' and ifs' hell.

This class makes everything, from cup of coffee to sandwiches, it also cures 
cancer and calls NSA if you are a terrorist.

![srp](./srp.jpg)

### A good practice

To be clear : 
 * One class/interface must only have one reason to change

Make simple objects. My personal guidances are :
(from the most important to the less, there are always exceptions)

 0) Strong type-hinting : it helps to define strict responsibilities
 1) **No class longer than 100 NCLOC** (non comment line of code)
 2) No method longer than 20 NCLOC
 3) No more than 5 public methods per class
 4) No more than 5 methods per class
 5) No "switch" because it is hidden inheritance
 6) No more "if(is_null($obj))" => Null Object Pattern
 7) No "if" for 2 behaviors => subclasses or State Pattern
 8) No "new" except in Creational Patterns (factories, builders etc...)
 9) No more "return null" for error => throw an exception
 10) Constructor with mandatory parameters for the class
 
It means for example I can tolerate a class with 15 methods if only five are public, 
or I could have a 50 NCLOC method if there is only one in this class 
but I don't tolerate class with 200+ NCLOC. Above 100 NCLOC, I put a "@todo need refactor".
200 NCLOC is my threshold for refactoring.
 
With small objects, documentation is easy, unit tests are easy, debug is easy
and refactoring is easier. Bonus, you could re-use some classes inside your project.

The drawback : choose carefully namespaces and naming conventions and use a good
IDE with effective autocomplete/link to.

[3]: http://en.wikipedia.org/wiki/Single_responsibility_principle
[4]: https://github.com/doctrine/doctrine2/blob/master/lib/Doctrine/ORM/UnitOfWork.php