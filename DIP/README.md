## [Dependency inversion principle][1]

Some developers would say this is tthe most important principle to design
loose coupled system. That's right. But you can't achieve it if you are not
ISP and LSP in the first place.

Example of the most common *bad practice* :

```php
public function __construct()
{
    $this->delegation = new Strategy();
}
```

With DIP, you will have :

```php
public function __construct(StrategyInterface $strat)
{
    $this->delegation = $strat;
}
```

A note about using a singleton instead of "new" : it is a bad pratice too.

You should use design patterns like factory method, abstract factory and/or
Dependency injection container like [Pimple][2].

[1]: http://en.wikipedia.org/wiki/Dependency_inversion_principle
[2]: http://pimple.sensiolabs.org/