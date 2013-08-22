## [Single responsibility principle][3]

SRP is very easy to understand but very hard to follow during a project rush.
Classes get fat, each developers add their own methods and object become
freaky monsters.

Because I don't want to copy-paste 3200 lines of code here, I'll give you an example
of bad pratices in Doctrine2 ORM : [UnifOfWork][4]

This classes does everything, even coffee and sandwiches.

![srp](./srp.jpg)

To be clear : 
 * The stronger principle : One class/interface must only have one responsibility
 * The softer principle : One class/interface must only add one responsibility
 * The better formulation : One class/interface must only have one reason to change

I think the last quote is simple to remember. 


[3]: http://en.wikipedia.org/wiki/Single_responsibility_principle
[4]: https://github.com/doctrine/doctrine2/blob/master/lib/Doctrine/ORM/UnitOfWork.php