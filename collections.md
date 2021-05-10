# Container

-Collections is a module implements special container data types that provide alternatives to the built-in containers (dict, list, set, tuple) with some additional functionalities  
-Counter (dict subclass), namedtuple (factory function for tuple subclasses), OrderedDict (dict subclass), defaultDict (dict subclass), deque (list-like container)  

## Counter
-Dict subclass for counting occurence of elements in an interable  
-Given an iterable, it will store the elements of the iterable as dictionary keys and their counts as dictionary values  
-Counts are allowed to be any integer value including zero or negative counts.  
-Counter objects have a dictionary interface except that they return a zero count for keys that arent in the dict instead of raising a KeyError  

```
>>> from collections import Counter
>>> mystring = "aaaaabbbccdddddee"
>>> mycounter = Counter(mystring)
>>> mycounter
Counter({'a': 5, 'd': 5, 'b': 3, 'c': 2, 'e': 2})
>>> mycounter.keys()
dict_keys(['a', 'b', 'c', 'd', 'e'])
>>> mycounter.values()
dict_values([5, 3, 2, 5, 2])
>>> mycounter.items()
dict_items([('a', 5), ('b', 3), ('c', 2), ('d', 5), ('e', 2)])
>>> mycounter.most_common(1)
[('a', 5)]
>>> mycounter.most_common(3)
[('a', 5), ('d', 5), ('b', 3)]
>>> list(mycounter.elements())
['a', 'a', 'a', 'a', 'a', 'b', 'b', 'b', 'c', 'c', 'd', 'd', 'd', 'd', 'd', 'e', 'e']

>>> c = Counter({'red': 4, 'blue': 2})
>>> c
Counter({'red': 4, 'blue': 2})
>>> c.most_common(1)
[('red', 4)]
>>> 
```

Methods  
mycounter.most_common(n)   returns a list of tuples. First item in the tuple is the key, second item is the count  
mycounter.elements()

Examples  
```
>>> # Tally occurrences of words in a list
>>> cnt = Counter()
>>> for word in ['red', 'blue', 'red', 'green', 'blue', 'blue']:
...     cnt[word] += 1
>>> cnt
Counter({'blue': 3, 'red': 2, 'green': 1})

>>> # Find the ten most common words in Hamlet
>>> import re
>>> words = re.findall(r'\w+', open('hamlet.txt').read().lower())
>>> Counter(words).most_common(10)
[('the', 1143), ('and', 966), ('to', 762), ('of', 669), ('i', 631),
 ('you', 554),  ('a', 546), ('my', 514), ('hamlet', 471), ('in', 451)]
```

## NamedTuple
-NamedTuple is a factory function for creating tuples with named fields (ie each position in a tuple is assigned a name or meaning which allows for more readable code)  
-They can be used wherever regular tuples are used, and they add the ability to access fields by name instead of position index  
-Creating a namedtuple object is basically like defining a class. Once it is created you use it to create actual namedtuples by passing it the desired values for the fields.  

Creation  
```
from collections import namedtuple

className = namedtuple(className, fieldNames)
-The field_names are a sequence of strings such as ['x', 'y'].
-Alternatively, field_names can be a single string with each fieldname separated by whitespace and/or commas, for example 'x y' or 'x, y'.
```

Methods and operations  
1. `_make(iterable)`  makes a new namedtuple instance from an existing sequence or iterable.  
2. `_asdict()` Return a new dict which maps field names to their corresponding values  
3. `_replace(**kwargs)` Return a new instance of the named tuple replacing specified fields with new values 
4. `_fields` returns tuple of strings representing the field names  
5. To convert a dictionary to a named tuple, use the double-star-operator  
```
>>> t = [11, 22]
>>> Point._make(t)
Point(x=11, y=22)

>>> p = Point(x=11, y=22)
>>> p._asdict()
{'x': 11, 'y': 22}

>>> p = Point(x=11, y=22)
>>> p._replace(x=33)
Point(x=33, y=22)

d = {'x': 11, 'y': 22}
Point(**d)
Point(x=11, y=22)

```


## OrderdDict
-remembers the order in which dictionary items were added  

## DefaultDict
-You specify the default data type.  
-When you try to access an undefined key it returns the default value of the default data type instead of a keyValue error  
int: 0  
str: empty string  
list: empty list  
float: 0.0  

```
>>> from collections import defaultdict
>>> d = defaultdict(int)
>>> d['a'] =1
>>> d['b'] = 2
>>> d['a']
1
>>> d['b']
2
>>> d['c']
0
>>> 
```

## Deque ('deck')
-Deques are a generalization of stacks and queues (the name is pronounced “deck” and is short for “double-ended queue”).   
-Deques support thread-safe, memory efficient appends and pops from either side of the deque with approximately the same O(1) performance in either direction.  
-Arguments: iterable (defines the number of items in the deque), maxlength of the deque  
-If maxlen is not specified or is None, deques may grow to an arbitrary length. Otherwise, the deque is bounded to the specified maximum length.  
-Once a bounded length deque is full, when new items are added, a corresponding number of items are discarded from the opposite end.   

```
>>> from collections import deque
>>> d = deque('ghi')                 # make a new deque with three items
>>> for elem in d:                   # iterate over the deque's elements
...     print(elem.upper())
G
H
I

>>> d.append('j')                    # add a new entry to the right side
>>> d.appendleft('f')                # add a new entry to the left side
>>> d                                # show the representation of the deque
deque(['f', 'g', 'h', 'i', 'j'])

>>> d.pop()                          # return and remove the rightmost item
'j'
>>> d.popleft()                      # return and remove the leftmost item
'f'
>>> list(d)                          # list the contents of the deque
['g', 'h', 'i']
>>> d[0]                             # peek at leftmost item
'g'
>>> d[-1]                            # peek at rightmost item
'i'

>>> list(reversed(d))                # list the contents of a deque in reverse
['i', 'h', 'g']
>>> 'h' in d                         # search the deque
True
>>> d.extend('jkl')                  # add multiple elements at once
>>> d
deque(['g', 'h', 'i', 'j', 'k', 'l'])
>>> d.rotate(1)                      # right rotation
>>> d
deque(['l', 'g', 'h', 'i', 'j', 'k'])
>>> d.rotate(-1)                     # left rotation
>>> d
deque(['g', 'h', 'i', 'j', 'k', 'l'])

>>> deque(reversed(d))               # make a new deque in reverse order
deque(['l', 'k', 'j', 'i', 'h', 'g'])
>>> d.clear()                        # empty the deque
>>> d.pop()                          # cannot pop from an empty deque
Traceback (most recent call last):
    File "<pyshell#6>", line 1, in -toplevel-
        d.pop()
IndexError: pop from an empty deque

>>> d.extendleft('abc')              # extendleft() reverses the input order
>>> d
deque(['c', 'b', 'a'])
```

Working with deques:  
1. Return last n lines of a file
```
def tail(filename, n=10):
    'Return the last n lines of a file'
    with open(filename) as f:
        return deque(f, n)
```

2. maintain a sequence of recently added elements by appending to the right and popping to the left:  
```
def moving_average(iterable, n=3):
    # moving_average([40, 30, 50, 46, 39, 44]) --> 40.0 42.0 45.0 43.0
    # http://en.wikipedia.org/wiki/Moving_average
    it = iter(iterable)
    d = deque(itertools.islice(it, n-1))
    d.appendleft(0)
    s = sum(d)
    for elem in it:
        s += elem - d.popleft()
        d.append(elem)
        yield s / n
```
