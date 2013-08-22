## [Open/closed principle][1]

Difficult to follow, because you have to be prescient. It's hard to know
what will change in a future release and what won't, even with good experience.

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

With this pattern, you follow the Hollywood principe and it's easy to unit test
the abstract template without customer concerns and to code and test only customer concerns
in a separate clas.

[1]: http://en.wikipedia.org/wiki/Open/closed_principle
[2]: http://en.wikipedia.org/wiki/Template_method