# How does **JavaScript** handle **objects**?

**Objects** form the majority of **JavaScript's** interface, alongside _functions_ and _arrays_. Any **object** data structure by default refers to the global **object prototype** unless otherwise specified.

## What are **constructors** and **methods**?

**Methods** are an **object's** _property_, but instead of storing a static value, they compute the **object's** value dynamically with the use of a _function_. **Methods** are like regular _properties_ in that they're accessed using the `.` notation and also the `[]` notation, which instead of directly accessing a _property_, evaluates the expression within the `[]` first. Furthermore, **constructors** are an easier way to create **objects** from a specific _prototype_, a _function_ call with the keyword `new` before it treats the _function_ as a **constructor**, adding two invisible or implied lines of code in the **constructor** _function_ body. Those lines assign `this` to the `new` **object** created by the **constructor** at the start of the _function_, while the other at the end of the **constructor** _function_ is a `return this;` statement that returns the **object**, which unless a `return` statement precedes it, executes automatically.

### What is an **object prototype**?

A _prototype_ is an **object** that acts as a fallback in case a _property_ or **method** lookup fails. All **objects** by default refer to the global **JavaScript object** for default **methods** like `.toString()`, `.length`, etc...Similarly, _arrays_ and _functions_ refer to global **prototypes** of their own. You can specify a **prototype** using the `Object.create(obj)` notation. In short, a **prototype** stores _properties_ (static or dynamic values) for a set of **objects** that share _properties_. Moreover, _properties_ are overwritten by assigning said _property_ a value even if its _prototype_ had a different value. When using a `for/in` _loop_ to check an **object's** _properties_, an **object's** global _prototype_ interferes. You can avert this by using `.hasOwnProperty` instead, which looks up the _property_ in question on the **object** itself and not its tree of _prototypes_. Thus `.hasOwnProperty` would return `false` for `obj.hasOwnProperty('toString');`. An **object** can be **prototype-less** when specified, with the same notation used to specify a _prototype_ for an **object**: `Object.create(null);`

#### What is the `this` keyword and how can you define it in **JavaScript**?

The `this` keyword refers to the **object** in question. You could assign custom values for `this` using different techniques. Using the `new` to call a **constructor** _function_ creates a fresh `this` for each `new` **object** created by the **constructor**. Moreover, using the `.call` **method** found on a _function_ default **prototype** you can specify the _arguments_ taken by the _function_ (when it's called within another _function_): `func.call(this, x, y)`, as well as specify what the `this` keyword means in the **constructor** _function's_ body with the following notation: `func.call(i)`, where `i` is a variable or value passed as `this` to `func` when it's called.

##### What is the `instanceof` **operator** and how does it work?

The `instanceof` **operator** is binary and returns either `true` or `false`. It checks if an **object** is a product of a certain **constructor**. It's also used to check _arrays_, and almost everything returns `true` when checked against `Object`.

###### What are the concepts of **inheritance**, **getters**, **encapsulation**, _setters_ and _polymorphism_?

_Polymorphism_ is when a piece of code is able to work with values of different shapes given that the interface allows it. An example is `.toString` **method** found on the global **JavaScript object** that when called, works as expected on values it can process like _arrays_, _numbers_, **strings** and **objects**. **Getters** and _setters_ are a helpful construct of **JavaScript** used with the keywords `get` and `set` respectively. They both allow a _function_ to run either when you read or write the _property_. Lastly, **inheritance** makes use of ability of _prototypes_ to have other _prototypes_ in that it enables the new **prototype** to inherit the old **prototype's** _properties_. **Encapsulation** is an concept of **Object-oriented programming** that emphasizes the differentiation between internal complexity and the external interface. Along with **inheritance** and _polymorphism_, **encapsulation** is a fundamental aspect of **object-oriented programming**, but while _polymorphism_ and **encapsulation** abstract a program or an interface away from the external interface, **inheritance** complicates the external interface itself making the code more tangled.