# Pythonisms

## Dunder Methods

What Are Dunder Methods?

In Python, special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores, for example `__init__` or `__str__`.

As it quickly became tiresome to say under-under-method-under-under Pythonistas adopted the term “dunder methods”, a short form of “double under.”

These “dunders” or “special methods” in Python are also sometimes called “magic methods.” But using this terminology can make them seem more complicated than they really are—at the end of the day there’s nothing “magical” about them.

Dunder methods let you emulate the behavior of built-in types. For example, to get the length of a string you can call len('string'). But an empty class definition doesn’t support this behavior out of the box:

```
class NoLenSupport:
    pass

>>> obj = NoLenSupport()
>>> len(obj)
TypeError: "object of type 'NoLenSupport' has no len()"
```

To fix this, you can add a ** len ** dunder method to your class:

```
class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42
```

Another example is slicing. You can implement a ** getitem ** method which allows you to use Python’s list slicing syntax: obj[start:stop].

**Special Methods and the Python Data Model**

This elegant design is known as the Python data model and lets developers tap into rich language features like sequences, iteration, operator overloading, attribute access, etc.

**Enriching a Simple Account Class**

Throughout this article I will enrich a simple Python class with various dunder methods to unlock the following language features:

- Initialization of new objects
- Object representation
- Enable iteration
- Operator overloading (comparison)
- Operator overloading (addition)
- Method invocation
- Context manager support (with statement)

**Object Initialization: `init`**

Right upon starting my class I already need a special method. To construct account objects from the Account class I need a constructor which in Python is the `init` dunder:

```
class Account:
    """A simple account class"""

    def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []

```

The constructor takes care of setting up the object. In this case it receives the owner name, an optional start amount and defines an internal transactions list to keep track of deposits and withdrawals.

This allows us to create new accounts like this:

```
>>> acc = Account('bob')  # default amount = 0
>>> acc = Account('bob', 10)
```

**Object Representation: `str`, `repr`**

1. `repr`: The “official” string representation of an object. This is how you would make an object of the class. The goal of `repr` is to be unambiguous.

2. `str`: The “informal” or nicely printable string representation of an object. This is for the enduser.

Let’s implement these two methods on the Account class:

```
class Account:
    # ... (see above)

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)

```

```
>>> str(acc)
'Account of bob with starting amount: 10'

>>> print(acc)
"Account of bob with starting amount: 10"

>>> repr(acc)
"Account('bob', 10)"

```

**Iteration: `len`, `getitem`, `reversed`**

In order to iterate over our account object I need to add some transactions. So first, I’ll define a simple method to add transactions. I’ll keep it simple because this is just setup code to explain dunder methods, and not a production-ready accounting system:

```
def add_transaction(self, amount):
    if not isinstance(amount, int):
        raise ValueError('please use int for amount')
    self._transactions.append(amount)
```

I also defined a property to calculate the balance on the account so I can conveniently access it with account.balance. This method takes the start amount and adds a sum of all the transactions:

```
@property
def balance(self):
    return self.amount + sum(self._transactions)
```

Let’s do some deposits and withdrawals on the account:

```
>>> acc = Account('bob', 10)

>>> acc.add_transaction(20)
>>> acc.add_transaction(-10)
>>> acc.add_transaction(50)
>>> acc.add_transaction(-20)
>>> acc.add_transaction(30)

>>> acc.balance
80
```

Now I have some data and I want to know:

1. How many transactions were there?

2. Index the account object to get transaction number …

3. Loop over the transactions

With the class definition I have this is currently not possible. All of the following statements raise TypeError exceptions:

```
>>> len(acc)
TypeError

>>> for t in acc:
...    print(t)
TypeError

>>> acc[1]
TypeError
```

## Iterators

Understanding iterators is a milestone for any serious Pythonista.

Let’s take the humble for-in loop, for example. It speaks for Python’s beauty that you can read a Pythonic loop like this as if it was an English sentence:

```
numbers = [1, 2, 3]
for n in numbers:
    print(n)
```

But how do Python’s elegant loop constructs work behind the scenes? How does the loop fetch individual elements from the object it is looping over? And how can you support the same programming style in your own Python objects?

Objects that support the `iter` and `next` dunder methods automatically work with for-in loops.

But let’s take things step by step. Just like decorators, iterators and their related techniques can appear quite arcane and complicated on first glance.

RepeaterIterator looks like a straightforward Python class, but you might want to take note of the following two things:

1. In the `init` method we link each RepeaterIterator instance to the Repeater object that created it. That way we can hold on to the “source” object that’s being iterated over.

2. In RepeaterIterator.`next`, we reach back into the “source” Repeater instance and return the value associated with it.

- Iterators provide a sequence interface to Python objects that’s memory efficient and considered Pythonic. Behold the beauty of the for-in loop!
- To support iteration an object needs to implement the iterator protocol by providing the `iter` and `next` dunder methods.
- Class-based iterators are only one way to write iterable objects in Python. Also consider generators and generator expressions.

## Generators

- Generator functions are syntactic sugar for writing objects that support the iterator protocol. Generators abstract away much of the boilerplate code needed when writing class-based iterators.
- The yield statement allows you to temporarily suspend execution of a generator function and to pass back values from it.
- Generators start raising StopIteration exceptions after control flow leaves the generator function by any means other than a yield statement.
