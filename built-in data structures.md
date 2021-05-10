# Built-in Data Structures Notes

## Strings




## Lists
- Mutable data structure that can store multiple values under one name, accessible via indeces.  
- Very versatile: can store any type of data  

Creation  
1. Square brackets  
2. Built-in list function
3. List comprehension: creating a list from an existing list 
```
myList = []

myList = list() 

myList = [2**x for x in range(10)]   
myList =  [x+y for x in ['Python ','C '] for y in ['Language','Programming']]   
```
Insertion/ Update  
1. Assignment operator = to change a specific element or a range of elements  
2. Add one element to the end of the list using the append() method
3. Add several items (another list) to the end of the list using the extend() method  
4. Insert one item at a particular position using the insert() method   
5. Insert multiple items starting at a particular position by assigning the list of items to an empty slice of the list
```
>>> odd = [2, 4, 6, 8]
>>> odd[1]=2
>>> odd
[2, 2, 6, 8]
>>> odd.append(5)
>>> odd
[2, 2, 6, 8, 5]
>>> odd.insert(3, 5)
>>> odd
[2, 2, 6, 5, 8, 5]
>>> odd.extend([2,3,4])
>>> odd
[2, 2, 6, 5, 8, 5, 2, 3, 4]
```
Deletion
1. pop method (removes and returns the last item in the list if no argument is provided. This helps us implement lists as stacks (lifo data structure)). argument it takes is index 
2. del keyword (can remove 1 single item by passing its index or a range of items)
3. remove method (removes first occurrence of the value given in the argument. ValueError if value is not in the list)
4. clear method (returns an empty list object)
```
>>> odd
[2, 2, 6, 5, 8, 5, 2, 3, 4]
>>> odd.pop()
4
>>> odd
[2, 2, 6, 5, 8, 5, 2, 3]
>>> odd.remove(2)
>>> odd
[2, 6, 5, 8, 5, 2, 3]
>>> del odd[1]
>>> odd
[2, 5, 8, 5, 2, 3]
>>> del odd[:2]
>>> odd
[8, 5, 2, 3]
```

Operations  
1. `+` operator joins two lists into a single list  
2. `in` operator checks if an item is in a list  
3. can iterate over items in the list using for loop:
```
for item in mylist:
    print(i)
```
4. check how many items are in the list using `len()` function
5. Slicing: mylist[start_included:end_excluded:interval]

Methods  
mylist.append(item)  note: item can be another list
mylist.extend(iterable)  
mylist.insert(index, element)  
mylist.remove(element)  
mylist.pop(index)  
mylist.clear()  
mylist.index(element, start, end)  
mylist.count(element)  
mylist.reverse()  
newlist= mylist.copy()  Returns a shallow copy of mylist. The copy needs to be assigned to a variable to be accessed. The benefit of using the copy() method is that if newlist gets modified mylist will remain unchanged.  
mylist.sort(key=...., reverse=...)  Sorts the list in place  

```
#sorting a list of tuples by their second element
>>> #define a function that will take second element from a tuple
>>> def takeSecond(elem):
	return elem[1]

>>> tuplelist = [(2, 2), (3, 4), (4, 1), (1, 3)]
>>> tuplelist.sort(key=takeSecond)
>>> tuplelist
[(4, 1), (2, 2), (1, 3), (3, 4)]


>>> mylist
['a', 'b', 'Windows', 'macOS', 'Linux']
>>> mylist.sort(key=len)
>>> mylist
['a', 'b', 'macOS', 'Linux', 'Windows']

To not change original list:
new_list = sorted(mylist)

```
<hr>

## Tuples
-A tuple is an immutable data structure that stores multiple values, separated by a comma, gathered under one variable name and accessed via indexing  
-Tuples are very useful if we want a function to return multiple values  
-Because they are immutable, tuples can be used as dictionary keys  
-Working with tuples can be more efficient than working with lists (for same items, a list will take up more bytes of memory and take longer to create)  

Creation  
1. Comma separated items in round brackets
2. tuple() function
```
mytuple = ('a', 'b')
```

Insertion/Update/ Deletion  
-Tuples are immutable, so its elements cant be changed once they have been declared. However, if the element is a mutable data type like a string, its individual items (the nested items of the tuple) can be changed  
-We can also change a tuple by reassigning it a different value  
-We cannot delete or remove items from a tuple (if you try it will result in a TypeError)  
-It is possible to delete the entire tuple using the del keyword: del mytuple  

Operations    
1. Unpacking tuple elements by assigning them to a specific variable
2. The + operator can be used to join two two tuples to form a new larger tuple
3. The * operator can be used to create a new tuple where the elements in a tuple are repeated a given number of times
4. The in operator can be used to check membership
5. The ==, > and < operatirs can be used to compare tuples in the same way that we compare other sequences
6. We can iterate through items in a tuple using a for loop
```
#unpacking
>>> n_tuple = ("mouse", [8, 4, 6], (1, 2, 3))
>>> a,b,c= n_tuple
>>> print(a)
mouse
>>> print(b)
[8, 4, 6]
>>> print(c)
(1, 2, 3)

#concatenation
>>> print((1, 2, 3) + (4, 5, 6))
(1, 2, 3, 4, 5, 6)

#repetition
>>> print(("Repeat", "hi") * 3)
('Repeat', 'hi', 'Repeat', 'hi', 'Repeat', 'hi')

#set membership
>>> mytuple= ((1, 2, 3),(4, 5, 6))
>>> print( 2 in mytuple)
False
>>> print( (4,5,6) in mytuple)
True

#iterating using a for loop
>>> names= ("John", "Kate", "Ellie")
>>> for name in names:
	print("Hi,", name)
Hi, John
Hi, Kate
Hi, Ellie
```

Methods  
mytuple.count(item)  
mytuple.index(item)  
len(mytuple)  
min(mytuple)/ max(mytuple)  The functions only work if the items in the tuple are of the same data type otherwise you get a TypeError  

<hr>

## Dictionaries
-An unordered collection of items composed of key-value pairs where a key is entered to access a value.   
-There is a one-to-one mapping between keys in the dictionary and values. Dictionaries are the only built-in data type that provides this mapping feature  
-Dictionaries are optimized for storing data that occurs in key-value pairs. They eliminate the need for indexing to access a value.  

Creation  
1. Curly braces, with key-value pairs separated by a colon  
2. Built-in `dict` function, with keys given as arguments and values given as their arguments
```
>>> myDict = {'name':'Ange', 'age':27}
>>> myDict2 = dict(name='Ange', age=27)
>>> myDict
{'name': 'Ange', 'age': 27}
>>> myDict2
{'name': 'Ange', 'age': 27}
>>> 
```
Access  
-Values in the dictionary are accessed using keys instead of indices.Keys can be used with square brackets [ ] or the get() method
-KeyError will occur if we try to access a key that doesn’t exist using the square bracket method. Get method will return None if no key is found  
-Values are mutable, so once it is accessed it can be changed (added to, subtracted from, etc)  
```
mydict= {“name”: “Jack”, “age”: 26}

#using square brackets
personsname= mydict[“name”]
mydict[“age”]+=1
print(“Jack is”,mydict[“age”], “years old”)

#using get() method
personsname= mydict.get(“name”)
print(“Jack is”, mydict.get(“age”), “years old”)
```

Insertion/ Update  
-Dictionaries are mutable, meaning we can change existing items or add new ones   
-We add a new key-value pair by defining it like it already exists.  
-If the key is already present in the dictionary, its value will be overwritten, otherwise a new key-value pair will be added to the dictionary.  
-We can also update a key’s value using the update() method  
-We can add items from one dictionary to another using the update() method  
```
vowels.update(a=5) #update key a’s value to 5

mydict.update(my2nddic)
```

Deletion  
-We can use the del keyword to remove a key and its associated value from the dictionary to delete the entire dictionary itself  
-We can delete a particular key and its associated value using the pop() method. The pop() method will delete the key that calls it and return its value.  
-The popitem() method will delete a random key-value pair from the dictionary and return the key+value as a tuple  
-The clear() method can be used to remove all the items in the dictionary at once.   
-You cant/shouldnt delete items from a dictionary while looping through it  
```
squares = {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

#delete the dictionary
del squares

#delete a key and its associated value
del squares[“2”]

#pop a specific item or a random item
>>> print(squares.pop(4))
16
>>> print(squares.popitem())
(5, 25)

#clear the dictionary
squares.clear()
```

Operations  
-The in operator only checks the membership of keys, not values.  
-Methods useful for traversing every item in the dictionary: .values(), .items() and .keys()  
-sorted() function can be used to do a simple sort on either the dictionary keys or dictionary values. It returns a new list of the sorted values. It doesnt change the dictionary. It has an optional reverse parameter whose default value is False. If set to True it will return items sorted in reverse order  
```
>>> person =  {'name': 'Phill', 'salary': None, 'age': 22}
>>> sorted(person)
['age', 'name', 'salary']
>>> sorted(person, reverse= True)
['salary', 'name', 'age']

>>> d={"one":1, "two":2, "three":3}
>>> sorted(list(d))
['one', 'three', 'two']
>>> sorted(list(d.values()))
[1, 2, 3]
>>> sorted(d)
['one', 'three', 'two']

#sorting by values
>>> employees = [
    {'Name': 'Alan Turing', 'age': 25, 'salary': 10000},
    {'Name': 'Sharon Lin', 'age': 30, 'salary': 8000},
    {'Name': 'John Hopkins', 'age': 18, 'salary': 1000},
    {'Name': 'Mikhail Tal', 'age': 40, 'salary': 15000},
]
>>> def get_name(employee):
    return employee.get('Name')
>>> employees.sort(key=get_name)
>>> print(employees, end='\n\n')
[{'Name': 'Alan Turing', 'age': 25, 'salary': 10000}, {'Name': 'John Hopkins', 'age': 18, 'salary': 1000}, {'Name': 'Mikhail Tal', 'age': 40, 'salary': 15000}, {'Name': 'Sharon Lin', 'age': 30, 'salary': 8000}]

```

Methods  
len(mydictionary)  
mydictionary.clear()  
mydictionary.copy()  
mydictionary.fromkeys(sequence, value) Returns a new dictionary with keys from the given sequence of elements and values set to value. value is optional  
mydictionary.get(key,d) Returns the value of the key. If the key doesn't exist it returns d. d is optional  
mydictionary.items()  
mydictionary.values()  
mydictionary.keys()  
mydictionary.update(dictionary2)  
mydictionary.update(a=5)  
mydictionary.popitem()  
mydictionary.pop(key,default) Removes element with key value given by key and returns its value. If the key isnt found it returns value given by default.  
mydictionary.setdefault(key,value) Returns the value of the key if its in the dictionary, otherwise it inserts a key with value set to value and returns that value. Value is optional, if its not specified default value is None and the method will return None  

## Sets

