## [Single responsibility principle][3]

SRP is very easy to understand but very hard to follow during a project rush.
Classes get fat, each developers add their own methods and objects become
freaky monsters.

Because I don't want to copy-paste 3200 lines of code here, I'll give you an example
of bad pratices in the Doctrine2 ORM project : [UnifOfWork][4]. More than 3k of
switches and ifs hell.

This class does everything, even coffee and sandwiches.

![srp](./srp.jpg)

To be clear : 
 * One class/interface must only have one reason to change


[3]: http://en.wikipedia.org/wiki/Single_responsibility_principle
[4]: https://github.com/doctrine/doctrine2/blob/master/lib/Doctrine/ORM/UnitOfWork.php