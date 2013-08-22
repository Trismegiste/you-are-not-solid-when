## [Open/closed principle][1]

Difficult to follow, because you have to be prescient. It's hard to know
what will change or won't, even with good experience.

Design patterns are welcome here, they solve many problems for you.

```php
class Service {
    public function doSomething() {
        // ... some code ...
    }
}
```

The most common case is the [template method design pattern][2].

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

[1]: http://en.wikipedia.org/wiki/Open/closed_principle
[2]: http://en.wikipedia.org/wiki/Template_method