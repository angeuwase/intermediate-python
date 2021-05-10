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
5. 
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
1. + operator joins two lists into a single list  
2. in operator checks if an item is in a list  

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
mylist.sort(key=...., reverse=...)  

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

```









## Dictionaries





## Tuples




## Sets

