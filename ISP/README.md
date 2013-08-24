## [Interface segregation principle][1]

To me, this principle is the second important because it is a **very effective
way to design loose coupled system**. Plus, it doesn't have performance issues.

Unlike LSP, ISP can be resumed in one phrase as "OOP is not facebook".
But there is a big prerequisite : you must have interfaces everywhere.

![ISP](./everywhere.jpg)

**Objects are socially awkward**, they don't want attachment to many people 
and they don't want to deeply know their friends. Just the bare minimum to
follow the contract they need, everything else does not concern them.

### A bad practice

```php
public function getTotal(\SplFixedArray $listing)
{
    $sum = 0;
    foreach($listing as $row) {
        $sum += $row->getPrice();
    }

    return $sum;
}
```

Why using a **SplFixedArray** if we just need to traverse the array ?

### A good practice

```php
public function getTotal(\Iterator $listing)
{
    $sum = 0;
    foreach($listing as $row) {
        $sum += $row->getPrice();
    }

    return $sum;
}
```

Since SplFixedArray inherits from Iterator, we "segregate" its type-hint to the 
minimum interface.

If you have big interface, you know there is something wrong
with your design.

If you can't break your interface, then you might have some problem with SRP.

[1]: http://en.wikipedia.org/wiki/Interface_segregation_principle