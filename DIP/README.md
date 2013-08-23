## [Dependency inversion principle][1]

Some developers would say this is the most important principle to design
loose coupled system. That's right. But you can't achieve it if you are not
ISP and LSP in the first place.

### A bad practice

This example is very common :

```php
public function __construct()
{
    $this->delegation = new Strategy();
}
```

The birth of a new object is a critical moment. Don't do it casually. When
you're typing "new", be sure it means your code cannot evolve.

About using a **singleton** or a **static factory** instead of "new" : it is a bad pratice too.
You can't extend this code without breaking it and you can't mockup the delegation
in unit tests. "Static" means "cannot evolve" by definition.

### A good practice

If you follow DIP, you would have :

```php
public function __construct(StrategyInterface $strat)
{
    $this->delegation = $strat;
}
```

Notice that we rely on interfaces.

You should use design patterns like **factory method**, abstract factory and/or
**Dependency injection container** like [Pimple][2].

And if your class needs to create objects on demand, inject a factory.

[1]: http://en.wikipedia.org/wiki/Dependency_inversion_principle
[2]: http://pimple.sensiolabs.org/