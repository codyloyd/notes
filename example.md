# example...

say we have a class that uses a variable in a couple different methods...
```ruby
class SomeClass
  def initialize(var)
    @var = var
  end

  def method1
    #do something with @var
  end

  def method2
    #do something else with @var
  end
end
```

so.. if for some reason we decide that `@var` needs some extra processing.. (maybe we change the way that var generated in another method.. in your example.. what happens if you change how `@board` works?) the only way to do that is to go through and edit all the methods that reference it.

IF however you had set it up like this:

```ruby
class SomeClass
  attr_accessor :var
  def initialize(var)
    @var = var
  end

  def method1
    #do something with var
  end

  def method2
    #do something else with var
  end
end
```


you can just manually make the methods that the `attr_accessor` method does for you:
```ruby
class SomeClass
  attr_accessor :var
  def initialize(var)
    @var = var
  end

  def var
    #do stuff to @var here.. and return it.. so that the other methods still work
  end

  def method1
    #do something with var
  end

  def method2
    #do something else with var
  end
end
```
