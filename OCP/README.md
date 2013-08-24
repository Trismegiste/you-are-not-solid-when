## [Open/closed principle][1]

Difficult to follow it, because you have to be prescient. It's hard to know
what will change in a future release and what won't, even with good experience.

**Design patterns** are welcome here, they solve many problems for you.

### A bad practice

Imagine you have a service :

```php
class Service {
    public function doSomething() {
        // ... some code ...
    }
}
```

And imagine not all the code inside could evolve, only a small part. 

### A good practice

The most common solution is the [template method design pattern][2].

```php
abstract class Service {

    final public function doSomething() {
        // ... some immutable code ...
        $this->specialBehavior();
        // ... some immutable code ...
    }

    abstract protected function specialBehavior();
}
```

With this pattern, you follow the Hollywood principle and it's easy to unit test
the abstract template without customer concerns. Business logic for customer
(the part that varies a lot) is in a separate class. The same for unit tests.

You could also use Strategy, Bridge, Adapter, Decorator, all Behavioral patterns.

A simple principle is : if there is something that frequently evolves or changes, 
do it in a subclass or with delegation (most of the GoF patterns are following this guideline)

[1]: http://en.wikipedia.org/wiki/Open/closed_principle
[2]: http://en.wikipedia.org/wiki/Template_method