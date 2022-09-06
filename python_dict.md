# python的Dictionary

## 引言
在做leecode题目的时候，解题思路中很巧妙的运用的dict这种数据类，或者成为结构体，达到了非常好的效果。我们来学习这种数据类型，然后来再现下leecode的题目的解题过程

## dict
字典（dict）类型是一种可变容器类型，可存储任意类型对象，关键词dict。  

*example*：d={ key1 : value1 , key2 : value2 }
'''py
>>>tinydict = {'a':1,'b':2,'b':'3'}
>>>tinydict['b']
'3'
>>>tinydict
{'a':1,'b':'3'}
'''
在字典中健是唯一的，重复后后面会替代前面，值不需要唯一。且值可以取任何数据类型，但是键必须是不可变的，如字符串，数字或元组。

### 访问字典
'''py
>>>tinydict = {'name':'zara','age':7,'class':'first'}
>>>print("tinydict['name']:",tinydict['name']) 
tinydict['name']:zara
'''
如果访问的键不存在则会报错。

### 修改字典
'''py
>>>tinydict = {'name':'zara','age':7,'class':'first'}
>>>tinydict['age'] = 8 #更新
>>>tinydict['school'] = "RUN00B" #添加
>>>print(tinydict['age'])
>>>print(tinydict['school'])
8
RUN00B
'''

### 删除字典元素
可删除单一元素，也可清空
'''py
>>>tinydict = {'name':'zara','age':7,'class':'first'}
>>>del tinydict['name'] # 删除键是‘name’的条目
>>>tinydict.clear()     # 清空所有条目
>>>del tinydict         # 删除字典
>>>
>>>print (tinydict['age'])
>>>print (tinydict['school'])
Error
'''
这是由于删除字典后，字典不存在，所以有异常抛出

### 字典键的特性
字典值可以取任何python中的对象，甚至可以是用户自定义的。但是键不行。有两点需要记住：

1) 不允许同一个键出现两次。创建时出现两次后一个会被记住。
'''py
>>>tinydict = {'name':'runoob','age':7,'name':'manni'}
>>>print(tinydict['name'])
manni
'''
2) 键必须不可变，所以可以用数字，字符串或者元组充当，用列表不行
'''py
>>>tinydict = {['name']:'zara','age':7}
>>>print(tinydict['name'])
Traceback (most recent call last):
  File "test.py", line 3, in <module>
    tinydict = {['Name']: 'Zara', 'Age': 7} 
TypeError: unhashable type: 'list'
'''

### 内置函数和方法
|序号 |函数及描述|
|:----|:----|
|1    |**cmp(dict1,dict2)**  比较两个字典元组|
|2    |**len(dict)**计算字典元素个数|
|3    |**str(dict)**输出字典可以打印的字符串表示|
|4    |**type(variable)**返回类型，比如是一个字典就返回字典类型|

|序号 |函数及描述|
|:----|:----|
|1    |**dict.clear()**删除字典内所有元素，或者指定的元素|
|2    |**dict.copy()**返回一个字典的浅复制（不懂什么是浅）|
|3    |**dict.fromkeys(seq,[val])**创建一个字典，seq中的元素作为字典的键，val作为键对应的初始值|
|4    |**dict.get(key,default=none)**返回指定键的值，如果值不在字典中，返回default的值|
|5    |**dict.has** _ **key(key)** 如果键在字典里返回true，否则返回false|
|6    |**dict.items()** 以列表返回可遍历的（键，值）元组数组|
|7    |**dict.keys()** 以列表返回一个字典所有的键|
|8    |**dict.setdefault(key,default=none)** 和get类似，但如果不存在字典中，将会添加并将值设置为default的值|
|9    |**dict.update(dict2)**把字典dict2的键值更新到dict中|
|10   |**dict.values()** 以列表返回字典中的所有值|
|11   |**pop(key,default=none)** 删除字典中给定键key的对应值，返回值为删除的值。key值必须给出。否则返回default值|
|12   |**popitem()**返回并删除字典中最后一对键和值|


## 关于dict在编写程序中的运用

### 题目描述
给定一个字符串s，找出其中不含重复字符的最长串的长度。
比如输入s="abcabcabc"输出3，因为无重复字符的最长串是"abc"，长度为3

### 解题思路
对于任意一个字符串s，则只需要从第一个字符开始找它的最大不重复串，记录串长，接着从第二个字符串开始找它的最大不重复串...一直遍历到最后一个，输出所有的串长最长的就好了。这是一种最笨的方法。但是实现起来较为简单方便。

'''python
class Solution:
	def lengthOfLongestSubstring(self,s: str) -> int:
		k,res,c_dict = -1,0,{}
		for i, c in enumerate(s):
			if c in c_dict and c_dict[c] > k:
				k=c_dict[c]
				c_dict[c]=i
			else:
				c_dict[c]=i
				res=max(res,i-k)
		return res
'''
我们来解释下这个程序的细节，首先创建了字典结构体c_dict，然后进入循环，重点是enumerate()函数，python中的这个函数



