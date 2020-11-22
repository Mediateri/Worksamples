Hello brother ...
##### This is in regard to the answer you asked about "Self" method

**Self is defined as**
> a reserved keyword in Ruby that always refers to an object, but the object self refers to frequently changes based on the context. When methods are called without an explicit receiver, Ruby sends the message to the object assigned to the self keyword. Calling methods without an explicit receiver is common, so understanding the object assigned to the keyword self at any time is essential.

###### where and how is it used?

self is initially set to main, an instance of the Object class that is automatically created whenever a Ruby program is interpreted. The main object is the ‘top-level’ namespace of the program.
> ```ruby 
> p self # the main object
> ```
