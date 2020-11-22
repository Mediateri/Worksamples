Hello brother ...
#### This is in regard to the answer you asked about "Self" method in Ruby

**Self is defined as**
> a reserved keyword in Ruby that always refers to an object, but the object self refers to frequently changes based on the context. When methods are called without an explicit receiver, Ruby sends the message to the object assigned to the self keyword. Calling methods without an explicit receiver is common, so understanding the object assigned to the keyword self at any time is essential.

##### where and how is it used?

###### self is initially set to main, an instance of the Object class that is automatically created whenever a Ruby program is interpreted. The main object is the ‘top-level’ namespace of the program.
> ```ruby 
>p self # the main object
> ```

###### In a class definition (but not in an instance method), the self keyword refers to the class itself.
>```ruby 
> class Dog
>  p self # the Dog class
> end
> ```

###### In singleton methods, the self keyword also refers to the class itself.
> ```ruby
>class Dog
>  def self.about
>    self
>  end
>end 
>p Dog.about # Dog
>```
###### In instance methods, the self keyword refers to instances of the class.
>```ruby
>class Dog
>  def bark
>    self
>  end
>end 
>p Dog.new.bark # an instance of the Dog class
>```

###### In modules, self refers to the module itself.
>```ruby
>module Cab
>  p self # Cab
>end
>```

###### self refers to an instance of a class if it’s defined in a module that’s mixed in to the class.

>```ruby
>module Cab
>  def hi
>    self
>  end
>end
> 
>class Cat
>  include Cab
>end
> 
>p Cat.new.hi # instance of the Cat class
>```

###### When a method is called without an explicit self, the implicit self is used, which is the value of the self keyword. In the following example, the Person#full_name method uses the values from Person#first_name and Person#last_name, but does not explicitly use self and relies on the value of the implicit self.

>```ruby
>class Person
>  attr_reader :first_name, :last_name
> 
>  def initialize(first_name, last_name)
>    @first_name = first_name
>    @last_name = last_name
>  end
> 
>  def full_name
>    "#{first_name} #{last_name}"
>  end
>end
>```

###### Relying on the implicit self can save quite a bit of typing over time and is very common among Ruby programmers.

**I hope this will help if you still have issue on understanding it please feel free to ask again**