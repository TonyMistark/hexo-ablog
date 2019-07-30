---
layout: post
title:  "python attrs"
date:   2019-01-12 22:32:40 +0800
categories: Python
---


```python
In [1]: import attr                                                                                                                                                                                                                           

In [2]: @attr.s 
   ...: class SomeClass(object): 
   ...:     a_number = attr.ib(default=42) 
   ...:     list_of_numbers = attr.ib(factory=list) 
   ...:     def hard_math(self, another_number): 
   ...:         return self.a_number + sum(self.list_of_numbers) * another_number 
   ...:                                                                                                                                                                                                                                       

In [3]: sc = SomeClass(1, [1, 2, 3])                                                                                                                                                                                                          

In [4]: sc                                                                                                                                                                                                                                    
Out[4]: SomeClass(a_number=1, list_of_numbers=[1, 2, 3])

In [5]: sc.hard_math(3)                                                                                                                                                                                                                       
Out[5]: 19

In [6]: sc == SomeClass(1, [1, 2, 3])                                                                                                                                                                                                         
Out[6]: True

In [7]: sc == SomeClass(1, [3, 2, 1])                                                                                                                                                                                                         
Out[7]: False

In [8]: attr.asdict(sc)                                                                                                                                                                                                                       
Out[8]: {'a_number': 1, 'list_of_numbers': [1, 2, 3]}

In [9]: SomeClass()                                                                                                                                                                                                                           
Out[9]: SomeClass(a_number=42, list_of_numbers=[])

In [10]: C = attr.make_class("C", ['a', 'b'])                                                                                                                                                                                                 

In [11]: C("foo", "bar")                                                                                                                                                                                                                      
Out[11]: C(a='foo', b='bar')
```
