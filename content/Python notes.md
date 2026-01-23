---
draft: true
---
# notes
参考[Python100Days](https://github.com/jackfrued/Python-100-Days/tree/master)
1. 整型（`int`）：Python 中可以处理任意大小的整数
	1. 二进制（如`0b100`，换算成十进制是4）
	2. 八进制（如`0o100`，换算成十进制是64）
	3. 十进制（`100`）
	4. 十六进制（`0x100`，换算成十进制是256）
2. 赋值运算符`:=`
	1. 我们称之为海象运算符，大家可以猜一猜它为什么叫这个名字。海象运算符也是将运算符右侧的值赋值给左边的变量，与赋值运算符不同的是，运算符右侧的值也是整个表达式的值
	2. 逻辑运算符有三个，分别是`and`、`or`和`not` ; 比较运算符的优先级高于赋值运算符
	3. ** 为幂运算
3. 分支结构： if elif else
	1. match-case：
		1. ```
		   match x:
			   case 0:
			   case 1:
			   case _:
		   ```
		2. 带有`_`的`case`语句在代码中起到通配符的作用，如果前面的分支都没有匹配上，代码就会来到`case _`。`case _`的是可选的，并非每种分支结构都要给出通配符选项。如果分支中出现了`case _`，它只能放在分支结构的最后面，如果它的后面还有其他的分支，那么这些分支将是不可达的。
		3. 可合并，如：`case 401 | 403 | 404: description = 'Not Allowed'`
4. 循环结构
	1. `time.sleep(1)`表示程序休眠 1 秒
	2. for-in loop ;
		1. use _ if the loop variable  not used in loop
		2. 3 ways : range(100) ;range(1,101); range(1,101,2)左闭右开
	3. while loop ：可以用break跳出/用continue进入下一轮循环
5. 列表
	1. 创建：`items=[1,2,34]` ,`items2 = ['Python', 'Java', 'Go', 'Kotlin']` 
	2. `list`函数可以将其他序列变成列表，如：`items4 = list(range(1, 10))
		`items5 = list('hello')` 
	3. `+`运算符实现两个列表的拼接;`*`运算符实现列表的重复,`*`运算符会将列表元素重复指定的次数; `in`或`not in`运算符判断一个元素在不在列表中, 
	4. `print(29 in items6)  # True ; print(99 in items6)  # False  `
	5. 索引：`[]`的元素位置可以是`0`到`N - 1`的整数，也可以是`-1`到`-N`的整数，分别称为正向索引和反向索引，其中`N`代表列表元素的个数。对于正向索引，`[0]`可以访问列表中的第一个元素，`[N - 1]`可以访问最后一个元素；对于反向索引，`[-1]`可以访问列表中的最后一个元素，`[-N]`可以访问第一个元素
	6. 切片运算是形如`[start:end:stride]`的运算符
		1. `start`代表访问列表元素的起始位置
		2. `end`代表访问列表元素的终止位置（终止位置的元素无法访问）
		3. `stride`则代表了跨度，简单的说就是位置的增量，比如我们访问的第一个元素在`start`位置，那么第二个元素就在`start + stride`位置，当然`start + stride`要小于`end`
		4. 如果`start`值等于`0`，那么在使用切片运算符时可以将其省略；如果`end`值等于`N`，`N`代表列表元素的个数，那么在使用切片运算符时可以将其省略；如果`stride`值等于`1`，那么在使用切片运算符时也可以将其省略
		5. `print(items8[-2:-6:-1]) `反向遍历
		6. 可以通过切片操作修改列表中的元素, 如`items8[1:3] = ['x', 'o']` 
	7. `append` 在尾部添加元素；`insert` ：插入到某个位置
		1.  ```Python
		languages = ['Python', 'Java', 'C++']
		languages.append('JavaScript')
		print(languages)  # ['Python', 'Java', 'C++', 'JavaScript']
		languages.insert(1, 'SQL')
		print(languages)  # ['Python', 'SQL', 'Java', 'C++', 'JavaScript']
		languages = ['Python', 'SQL', 'Java', 'C++', 'JavaScript']
		if 'Java' in languages:
		    languages.remove('Java')
		if 'Swift' in languages:
		    languages.remove('Swift')
		print(languages)  # ['Python', 'SQL', C++', 'JavaScript']
		languages.pop()
		temp = languages.pop(1)
		print(temp)       # SQL
		languages.append(temp)
		print(languages)  # ['Python', C++', 'SQL']
		languages.clear()
		print(languages)  # []
		```
		2. 使用 Python 中的`del` 关键字后面跟要删除的元素, 如`del items[1]
	8. index函数用于查找索引，count函数用于统计元素出现次数；如：`print(items.index('Python'))` 
		`# 从索引位置3开始查找'Java' print(items.index('Java', 3))`
	9. `sort()` 实现排序；`reverse()` 实现列表反转
	10. 列表生成式
		1. `items = [i for i in range(1, 100) if i % 3 == 0 or i % 5 == 0]`
		2. ` nums2 = [num ** 2 for num in nums1]`
6. 元组（tuple）
	1. **元组是不可变类型**
	2. `()`表示空元组，但是如果元组中只有一个元素，需要加上一个逗号，否则`()`就不是代表元组的字面量语法，而是改变运算优先级的圆括号
	3. 打包和解包操作：多个用逗号分隔的值赋给一个变量时，多个值会打包成一个元组类型；当我们把一个元组赋值给多个变量时，元组会解包成多个值然后分别赋给对应的变量
	4. 星号表达式：可以让一个变量接收多个值；用星号表达式修饰的变量会**变成一个列表**，列表中有0个或多个元素；其次，在解包语法中，星号表达式**只能出现一次**。
	5. 解包语法对所有的序列都成立，这就意味着我们之前讲的列表、`range`函数构造的范围序列甚至字符串都可以使用解包语法。
	6. 交换变量的值：直接`a, b, c = b, c, a` 
	7. 可以和列表互换，如`list(infos)` or `tuple(frts)` 
7. 字符串