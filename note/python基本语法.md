# python基本语法
### 注释
* 单行注释以#开头
* 多行注释以'''开始'''结束
### 变量的类型
* int(有符号整型) long(长整数[也可以代表八进制和十六进制]) (老版本) float(浮点型) complex(复数)
* boolean
* string(字符串)
* list(列表)
* Tuple(元组)
* Dictionary(字典)
* 查看数据类型 type(变量的名字)
### 类型转换
>1. int(x) 将x转换为一个整数 
    >>如果将float转int返回的是小数点前的数
    如果将Boolean转int返回的是 true->1 false->0

>2. float(x) 将x转换为一个浮点数
    >如果将int转float返回的是 int的值后面加.0

>3. str(x) 将对象x转换为字符串

>4. bool(x) 将对象x转换成布尔值
    >>如果对非0的整数(包含正数和复数)进行bool、类型的转换 那么就全都是True，在整数的范围内0强制转换为bool类型的结果为false

>**注意**
>>1. 如果对非0的整数(包含正数和复数)进行bool、类型的转换 那么就全都是True，在整数的范围内0强制转换为bool类型的结果为false
>>2.  将浮点数转换为bool类型的数据的时候，正的浮点数和负的浮点数的结果是true，如果是0.0那么结果是false
>>3. 只要字符串中有内容(不管是啥哪怕是空格) 那么在强制类型转换为bool的时候返回true，反之为false
>>4. 只要列表中有数据 那么强制类型转换为bool的时候 就返回true，反之为false
>>5. 只要元组中有数据 那么强制类型转换为bool的时候 就返回true，反之为false
>>6. 只要字典中有数据 那么强制类型转换为bool的时候 就返回true，反之为false

### 运算符
>算数运算符 例 a=3 b=2
'+' 加 a+b = 5
'-' 减 a-b = 1
'*' 乘 a*b = 6
'/' 除 a/b = 1.5
'//'取整除 整除为取整数没有浮点数 a//b=1
'%' 取余 a%b = 1
'**'指数 幂运算
'()'小括号 提升优先级

>**扩展**
>>* a = '123'
b = '456'
a+b = '123456'

>>* a = '123'
b = 456
a+b会报错 在python中只有两边都是字符串才会进行拼接

>>* a = '下雨了'
a * 3 字符串的乘法是将字符串重复多少次

### 赋值运算符
>* b = c =20
print(b)//20
print(c)//20

>* d,e,f = 1,2,3
print(d)//1
print(e)//2
print(f)//3

### 复合赋值运算符
>+=       c+=a 等效于 c=c+a
-=       c-=a 等效于 c=c-a
*=       c*=a 等效于 c=c*a
/=       c/=a 等效于 c=c/a
//=       c//=a 等效于 c=c//a
%=       c%=a 等效于 c=c%a

### 逻辑运算符
**and 必须全为true才会返回true**
>* a = 1
b = 3
print(a and b) #输出结果为3 当两个值都是非零数字的情况下输出的是后面的值，只要有一边为0结果为0

**or  有一个true就会返回true**
>* a = 1
b = 3
print(a and b) #输出结果为1 当第一个值为非零数的时候就输出前面的值

**not 非 取反 not true --> false**

**注意**
>1. a = 36 
a > 10 and print('成功打印')  // 会打印
a < 10 and print('成功打印')  // 不会打印
当and前面的结果为false的情况下 那么后面的代码就不再执行

>2. a > 37 or print('成功打印')  // 会打印
a < 37 or print('成功打印')  // 不会打印
只要一方为true了那么结果就是true，下面的代码前半部已经为true了所有后面的代码就不会执行

### 位运算符
1. & 按位"与"运算符：参与运算的两个值，如果两个相应位都为1，则结果为1，否则为0

2. | 按位"或"运算符：只要对应的两个二进制位有一个为1时，结果为1

3. ^ 按位"异或"运算符：当两对应的二进制位相异时，结果为1

4. ~ 按位"取反"运算符：对数据的每个二进制位取反，即把1变为0，把0变为1

5. << "左移动"运算符：运算数的各二进制位全部左移若干位，由"<<"右边的数指定移动的位数，高位丢弃，低位补0  左移1位相当于乘2

6. '>>' "右移动"运算符：运算数的各二进制位全部右移若干位，由">>"右边的数指定移动的位数 右移1位相当于整除2

### 成员运算符
in ：当在指定的序列中找到值时返回True，否则返回False
not in：当在指定的序列中没有找到值时返回True，否则返回False
### 身份运算符
is ：判断两个标识符是否引用自同一个对象，若引用的是同一个对象返回True，否则返回False
is not ：判断两个标识符是否引用自不同对象，若引用的不是同一个对象返回True，否则返回False

### 输入与输出
1. 普通输出 
print()
2. 格式化输出(scrapy框架的时候用到，当把爬取到的数据要放到excel文件 mysql redis中的时候)
%% 代表的是输出%号
%s 代表的是字符串  
%d 代表的是有符号的十进制整数
%f 代表的是浮点数
%c 代表的是字符
%u 代表的是无符号十进制整数
%o 代表的是八进制整数
%x 代表的是十六进制整数(小写字母0x)
%X 代表的是十六进制整数(大写字母0X)
%e 代表的是科学计数法(小写'e')
%E 代表的是科学计数法(大写'E')
%g 代表的是%f和%e的简写
%G 代表的是%f和%E的简写
字符串后先写%然后接()，里面是要放进去的数据,如果只有一个数值的话就不用括号了

>* age = 18
name = '张三'
print('我的名字是%s,我的年龄是%d' % (name,age))
>* name = '李四'
age = 26 
money = 999.9
>* print('%d岁的%s一首歌赚了%f块钱' %(age,name,money)) # 26岁的李四一首歌赚了999.9000块钱
print('%s岁的%s一首歌赚了%s块钱' %(age,name,money)) # 26岁的李四一首歌赚了999.9块钱 
数据给的整型，而前面的占位符是字符型却依然打印出了正确的结果，是因为此处做了一个强转，把整型转换成了字符型，如果不能转成字符型的则会报错
>* print('%d岁的%s一首歌赚了%.1f块钱' %(age,name,money)) # 26岁的李四一首歌赚了999.9块钱 此处的浮点型设置了小数点的位数

3. 输入
input('请输入您的密码'）
password = input('请输入您的密码')
4. 进制转换
>1. n = 149
print(bin(n)) #bin()为十进制转二进制结果为 0b10010101 只要前面有0b就表示为二进制
print(oct(n)) #oct()为十进制转八进制 0o225 0o表示八进制
>2. n = 221
print(hex(n)) #hex()为十进制转十六进制 0xdd 0x表示十六进制
>3. n = 0x558
print(int(n)) #十六进制转十进制 1368
print(oct(n)) #十六进制转八进制
print(bin(n)) #十六进制转二进制 bin()函数无论什么进制的数，放里面都能转为二进制
>>0x  5    5    8
0b 0101 0101 1000
>>0x  a    c     3
0b 1010 1100  0011
### 位运算符 针对二进制进行的运算
**& | ^ ~ >> <<**

1. & 类似于and（俩个都为真才是真）
    * F and F -----> F
    * T & T -----> T
   * n1 = 0b0110 #6
     n2 = 0b0010 #2
     print(n1 & n2) #2 
计算过程：
上下相同则为相同的数，不同则为0
    0b 0110
    0b 0010
结果 0b 0010 所以结果为2

2. | 类似于 or（ 一个为真则为真）
    * n1 = 0b0110 #6
      n2 = 0b0010 #2
      print(n1 | n2) #2 
计算过程：
上下相同则为相同的数，不同则为1
    0b 0110
    0b 0010   
结果 0b 0110 所以结果为6
3. ^ 按位异或运算（当两个对应的二进制位相异时，结果为1）
    * n1 = 0b0110 #6
      n2 = 0b0010 #2
      print(n1 | n2) #2 
计算过程：
上下相同则为相同为假，不同则为真
    0b 0110
    0b 0010   
结果 0b 0100 所以结果为4

4. ~ 取反运算符
   * n1 = 0b0110 #6
     print(~n1)
整数为:0b 0110
结果:
   * 二进制的负数表示(二进制一个字符是8个比特位，前面的表示符号，最高位为1为负数，0为正数)
原码 0000 0110
反码 1111 1001
补码 反码+1  1111 1010 前面再加上表示
    * 负的二进制转十进制步骤
1.二进制(负的) 2.二进制减1 3.取反 4.原码 5.转十进制

>n = 12 # 0000 1100
>* print(n << 2) #左移两位 0011 0000 = 48
print(n << 3) #左移三位 0110 0000 = 96
所以相当于乘以2的移动位数的次方，也就是每移动一位表示乘以2
>* print(n >> 1) #右移一位 0000 0110 = 6
print(n >> 2) #右移两位 0000 0011 = 3
print(n >> 3) #右移三位 0000 0001 = 1
所以相当整除2，每移动一位表示除以2

### 流程控制语句
**1. if判断语句**
>age = 30 
if age >= 18:
    print('我已经成年了') 
结果为 输出打印

>**如果需要使用input输入参数的话，参数的类型为string类型**
>age = input('请输入你的年龄')
print(type(age)) //str
>**所以如果需要和int类型进行比较的话我们就要使用强制类型转换**
age = int(input('请输入你的年龄'))
if age >= 18:
    print('我已经成年了') 
    
**2. if else语句**
>* age = 19
if age > 18:
    print('可以去网吧了')
else:
    print('回家写作业')

>* elif的功能:
    if xxx1:
        事情1
    elif xxx2:
        事情2
    elif xxx3:
        事情3
>**如果if后面的表达式是：None、""(空字符串)、0、0.0、[]、()、{}等都认为是False**

>* 三元表达式
a = 1
b = 2 
c = a if a < b else b
相当于:
if a < b:
    c = a 
else:
    c = b

**3. while循环**
>**1. 猜数猜对位置，如果猜错给出提示，猜大了还是猜小了**
>>import random
ran = random.randint(1,50)
#循环猜多次
while True:
&emsp; guess = int(input('猜一个1-50之间的数'))
&emsp;#猜对就结束
&emsp;  if guess == ran:
&emsp; &emsp;print('恭喜猜对了！')
&emsp;&emsp; break
&emsp;elif guess> ran:
&emsp;&emsp;print('猜大了，小一点')
&emsp;elif guess< ran:
&emsp;&emsp;print('猜小了，大一点')

>**2. 猜拳三局两胜**
>>import random
n = 1
#计数
p_count = 0
m_count = 0
while n <= 3:
&emsp;&emsp;#猜拳
&emsp;&emsp;#机器产生数字0 1 2代表剪刀石头布
&emsp;&emsp;ran = random.randint(0,2)
&emsp;&emsp;#人猜数字
&emsp;&emsp;guess = int(input('请输入：剪刀(0) 石头(1) 布(2)'))
&emsp;&emsp;#比较判断
&emsp;&emsp;if guess== 0 and ran==2 or guess==1 and ran==0 or guess==2 and ran==1:
&emsp;&emsp;&emsp;print('我赢了')
&emsp;&emsp;&emsp;p_count += 1
&emsp;&emsp;elif ran ==0 and guess == 2 or ran== 1 and guess == 0 or ran == 2 and guess == 1:
&emsp;&emsp;&emsp;print('机器赢了')
&emsp;&emsp;&emsp;m_count += 1
&emsp;&emsp;else:
&emsp;&emsp;&emsp;print('本轮平局')
&emsp;&emsp;&emsp;n += 1
#比较胜负
if p_count > m_count:
&emsp;print('我赢了')
elif p_count < m_count:
&emsp;print('机器赢了')
else:
&emsp;print('平局')

**4. for循环**
s = 'china'
for i in s:
&emsp;print(i)
**range方法的结果是一个可以遍历的对象**
**range(5) 为 0~4 左闭右开区间**
>1. for i in range(5):
    print(i) // 结果为 0 1 2 3 4
>2. range(1,6)
for i in range(1,6):
    print(i) // 1 2 3 4 5
>3. range(1,10,3) // 第三个参数为步长
for i in range(1,10,3):
   print(i) // 1 4 7
>4. a_list = ['周杰伦','林俊杰','陶喆']
for i in a_list:
    print(i)
>5. 如果想要遍历列表的下标
for i in range(len(a_list)):
>6. i = 1
total = 0
while i <= 5:
&emsp;total += i
&emsp;i += 1
&emsp;if i == 3:
&emsp;&emsp;print('遇到3就跳出循环')
&emsp;&emsp;break    如果是continue的话就是跳过下面的代码执行下一次的循环
else:
&emsp;print('累加和是：', total)

### 数据类型高级
**1. 字符串高级**
  * 获取长度: len 可以获取字符串的长度 len()
  * 查找内容: find 查找指定内容在字符串中第一次出现的位置，找不到就是-1，默认是从左边开始查，如果想从右边开始查的话就用rfind，index的效果也是查找，但是index找不到不会返回-1而是直接报错
   * 判断: stratswith endswith (判断以什么开头，以什么结尾) isalpha isdigit isalnum isspace 返回值都是布尔值
   * 计算出现的次数: count 
   * 替换内容: replace 
   * 切割字符串: split
   * 修改大小写: upper,lower
   * 空格处理: strip
   * 字符串拼接: join
   * 切片：[start:end]  [start:end:step]
字符串的strip方法可以帮我们去除字符串两端的空格。strip方法还有Istrip和rstrip两个版本，格式化字符串：就是将字符串按照指定的格式输出，可以使用%，format或者字符串前加上'f'来格式化字符串
>* s = 'aaab'
s.count('a') // 3
>* s = 'cccddd'
s.replace('c','a') // 用a替换c aaaddd
>* s = '1#2#3'
s.split('#') // ['1','2','3']
>* s = 'china'
s.upper() // 将小写字母变成大写
>* s = 'CHINA'
s.lower() // 将大写变成小写
>* s = 'a'
s.join('hello') // haealalao
>* s = 'sdasdassa56sda54d54'
s.stratswith('sdsd') #false
s.endswith('sdsd') #false
>* s = 'sds'
s.isalpha() #是否是纯字母组成的
s.isdigit() #是否是数字组成的
s.isalnum() #是否是字母和数字组成的
s.isspace() #是否是空格
>* s = 'abc123456'
print(s[0:3]) //abc 包前不包后 意为从0到2 如果end不写的话就是从你设置的起始位到最后 如果start不传的话就是从起始一直到end值的前一位
print(s[0:6:2]) // ac2
print(s[:6:3]) //a1
print(s[:6:-1]) //65 如果step为负数的话就是从后往前取
print(s[:-7:-2]) //642

**2. 切片**
切片是指对操作的对象截取其中一部分的操作，字符串、列表、元组都支持切片操作
切片的语法:[起始:结束:步长]
**注意:选取的区间从'起始'位开始，到'结束'位的前一位结束(不包含结束位本身)，步长表示选取间隔**
>* s = 'Hello world'
s[4] // o
s[3:7] // lo w 从下标3到下标6
s[1:] // ello world  如果只有起始位没有终止位那么就到最后一位结束
s[:4] //hell 如果只有结束位没有起始位那就是从头到结束位的前一位位置
s[0:6:2] // hlo 步长为2的话表示隔一个截取一个
>* name = 'lj'
job = 'it'
print('%s是一位%s' % (name,job)) // lj是一位it
print('{}是一位{}'.format(name,job))  // lj是一位it {}里也可以使用索引，例如前一个括号填0后一个括号填1这样显示结果不变
print(f'{name}是一位{job}') // lj是一位it
>* s = 'abcd123'
for i in s:
&emsp;print(i) #可以遍历字符串
>**例：找出字符串中的数字相加**
&emsp;s = 0
&emsp;for i in '6dfdf989dfs3':
&emsp;&emsp;i.isdigit():
&emsp;&emsp;s += int(i)
>* str.format()方法
print('要借阅的书名是：{}，借阅的数量是：{}'.format(bookname,number))

**3.列表高级**
1. append 在末尾添加元素
2. insert 在指定位置插入元素,后面的元素往后挪
3. extend 合并两个列表
切片使用和字符串相同
4. sort 排序
5. clear 删除 清空列表里的所有元素
6. reverse 元素反转
7. count 获取元素个数
>* food_list = ['小炒肉','回锅肉']
  food_list.append('粉蒸肉') //['小炒肉','回锅肉','粉蒸肉']
>* char_list = ['a','c','d']
char_list.insert(1,'b') //['a','b','c','d']
>* num_list = ['1','2','3']
num1_list = ['4','5','6']
num_list.extend(num1_list) //['1','2','3','4','5','6']
8. 修改元素
>city_list = ['北京','上海','广州']
city_list[0] = '南昌' // ['南昌','上海','广州']
9. 查找元素
python中查找的常用方法:
   * in(存在),如果存在那么结果为true，否则为false
   * not in(不存在),如果不存在那么结果为true，否则为false
    food_list = ['小炒肉','回锅肉']
    food = input('请输入您想吃的食物')
    if food in food_list:
&emsp;print('在')
    else:
&emsp;print('不在')

使用count去进行判断
n = items.count('要查找的值')  如果为0则表示没有该值
10. 删除元素
* del:根据下标进行删除
* pop:删除最后一个元素 也可以传入下标去指定删除
* remove:根据元素的值进行删除，如果列表中存在多个同名元素只会删除第一个，后面的不会删除
>* a_list = [1,2,3,4]
  del a_list[2] //[1,2,4]
>* b_list = [1,2,3,4]
  b_list.pop() // [1,2,3]
>* c_list = [1,2,3,4]
  c_list.remove(3) //[1,2,4]
>* 如果里面有多个重复元素，都需要删除
>>list = [1,2,5,2,2,88,2]
     n = 0
    while n<len(list):
    &emsp;if list[n] == 2:
    &emsp;&emsp;list.remove(2)#此时为了控制连续相同元素挨着然后漏删的问题，在删除之后下标不操作，没删除的时候下标才加一
    &emsp;else:
     &emsp;&emsp;n += 1

11. 排序
    list = [1,3,5,89,7,56]
    list.sort() #1 3 5 7 56 89 直接使用的话就是正序
    list.sort(reverse=True) 这么使用的话就是逆序
12. 反转
    list.reverse()
>s = [1,3,5,89,7,56,99,102,85,41]
s[4] // 7
s[3:7] // [89,7,56,99] 从下标3到下标6
s[1:] // [3,5,89,7,56,99,102,85,41]  如果只有起始位没有终止位那么就到最后一位结束
s[:4] // [1,3,5,89]
s[0:6:2] // [1,5,7] 步长为2的话表示隔一个截取一个
s[::-3] #[41,99,89,1] 步长为负数的时候是从后往前


13. 列表推导式：最终得到一个列表
例：如果我们要拿到一个1-20的列表
list = []
for i in range(1,21):
    list.append(i)
列表推导式可以对其进行简化
格式：
    * [i(这个i是最终放在列表里的变量) for i in 可迭代的变量]
    * 如果需要加判断的话
    [i(这个i是最终放在列表里的变量) for i in 可迭代的变量 if 条件]
    * 如果既有if也有else
    [结果1 if 条件 else 结果2 for i in 可迭代的变量]
    * 多个循环嵌套
    [(x,y) for x in 可迭代的变量 for y in 可迭代的变量]

>* list = [ i for i in range(1,21)]
前面放在列表中的i可以进行一些运算
>* 例：1-100之间所有偶数 存放在列表中
list = [ i for i in range(0,101,2)]
list = [ i for i in range(0,101) if i%2==0]
>* 例：如果是h开头的则将首字母大写，不是h开头的全部转大写
title() 首字母大写
upper() 全部大写
list2 = ['62','hello','100','world']
lis3 = [word.title() if word.isalpha() and word.startswith('h') else word.upper()   for word in list2]
list4 = [(x,y) for x in range(1,3) for y in range(1,3)] #[(1,1),(1,2),(2,1),(2,2)]
>* 例 实现分组一个list里面的元素，比如[1,2,3,...100] 变成 [[1,2,3],[4,5,6]...]
    a = [x for x in range(1,101)]
    b = [a[i:i+3] for i in range(0,len(a),3)]
>* 找出里面名字含有两个'e'的放在新列表中
   names = [['Tom','Billy','Jefferson','Andrew','Wesley','Steven','Joe'],    
   ['Alice','Jill','Ana','Wendy','Jennifer','Sherry','Eva']]
new_names = [j for i in names for j in i if j.count('e')>=2]

 **4. 元组高级 python的元组与列表类似，不同之处在于元组的元素不能修改 元组使用小括号，列表使用方括号**
 a_tuple = (1,2,3,4)
a_tuple[0] // 1
a_tuple[3] = 5 //报错 tuple不支持该方式

**注意：定义只有一个元素的元组，需要在唯一的元素后写一个逗号**
* a = (11,) 如果不加逗号类型判断会是int
切片的使用相同
* count 用来计数，使用方法也相同
* list(tuple) ---> 元组转列表 
* tuple(list) ---> 列表转元组
  可以通过元组转列表之后进行修改，再把列表转元组
  
**5. 字典高级**
**字典也有和列表一样的推导式**
person = {'name':'小明','age':18}
如果出现相同的键的话，运行并不会报错，后面的键的值会替换掉前面键的值。如果值是相同的话则无所谓。

1. 访问person的属性：
print(person['name']) // 小明(注音要查询的属性名的写法是str的形式)
   * 使用[]的方式，获取字典中不存在的key的时候 会发生异常 keyerror
   * 不能使用person.name的方式来访问字典中的数据
   * 可以使用如下方式来访问
print(person.get('name')) // 小明 get后面还可以传第二个参数，意味如果找不到该key的value值的话，显示的就是第二个参数的值
   * 使用.的方式，获取字典中不存在的key的时候 不会报错会返回一个none
2. 字典的修改
person['name'] = '张三'
3. 字典的添加
#给字典添加一个新的key value 这个键如果在字典中不存在 那么就会变成新增元素
 person['sex'] = '男'
4. 字典的删除
pop
    删除字典中指定的某一个元素
popitem
    删除最后面的一个键值
del
    * 删除字典中指定的某一个元素
    * 删除整个字典  
    
 &emsp;&emsp;clear
&emsp;&emsp;清空字典 但是保留字典对象

>person = {'name':'小明','age':18}
person.pop('name')
del person['age']
del person // 整个删除
此时如果在下面打印person会出现报错 person is not defined
>person.clear()
此时如果在下面打印person会打印出 {}
5. 字典的遍历
person = {'name':'小明','age':18,'sex':'男'}
    * 遍历字典的key
字典.keys() 方法 获取字典中所有的key值
for key in person.keys():
    print(key)
    *  遍历字典的value
字典.values() 方法 获取字典中所有的values值
for value in person.values():
    print(value)
   * 遍历字典的key和value
for key,value in person.items():
    print(key,value)
    * 遍历字典的项/元素
for item in person.items():
    print(item)
    
**6. 集合set**
集合(set)是一个无序不重复的元素序列，可以使用大括号{}或者set()函数创建集合 **注意：创建一个空集合必须用set()而不是{},因为{}是用来创建一个空字典 集合也有和列表一样的推导式**

创建格式:
parame = {value01,value02,...}
或者
set(value)
set可用于快速删除多个重复元素

>list = [1,3,6,8,9,9,1,2,3,9]
set(list) # {1,2,3,6,8,9}

添加元素 add
>set.add(10)

合并 update
>set1.update(set2) #把2并进1

移除
>set.remove() #如果传入的值不存在的话会报错
set.discard() #传入的值不存在的话不会报错

>del set #整个删除
set.clear() # 清空
set.pop() #随机删除一个元素

集合
>union 并集 简写 &    set2 & set3
difference 差集 简写 -  set2 - set3
intersection 交集 简写 |  set2 | set3

>>set2 = {1,2,3,4,5}
set3 = {3,4,5,6,7}
print(set2.intersection(set3)) #{3,4,5}

***例 产生5组(不允许重复)，字母和数字组成4位验证码***
>import random
code_set = set()
s = 'ewqrrtuyyutifgsgsdfg012132254678731'
while True:
&emsp;code = ''
&emsp;for i in range(4):
&emsp;&emsp;&emsp;index = random.randint(0,len(s)-1) #从0到s的长度中间任取一个数字,当做下标位置
&emsp;&emsp;&emsp;code += s[index]
&emsp;code_set.add(code)
&emsp;if len(code_set) == 5:
&emsp;&emsp;break
print(code_set)

***练习 图书馆管理系统***
>library = [{'bookname':'xxx','author':'xxx,'price':100,'number':4},{},{},{}]

功能：借书 还书 查询(书名/作者) 查看所有 退出

>library = [
    {'bookname':'西游记','author':'吴承恩','price':100','number':40},
    {'bookname':'水浒传','author':'施耐庵','price':100','number':40},
    {'bookname':'红楼梦','author':'曹雪芹','price':100','number':40},
    {'bookname':'三国演义','author':'罗贯中','price':100','number':40},
    {'bookname':'三国演义','author':'罗贯东','price':100','number':40},
]

>while True:
&emsp;oper = input('\n1. 借书 \n2. 还书\n3. 查询\n4. 查看所有\n5. 退出\n请选择你需要的服务：')
&emsp;if oper == '1':
        #需求：输入书名，查询是否有书，然后再判断作者是否是想要的
&emsp;&emsp;print('1.借书模块')
&emsp;elif oper == '2':
        #需求：输入书名，输入作者判断是否存在有则还书，无则抛出异常
&emsp;&emsp;print('2.还书模块')
&emsp;elif oper == '3':
        #需求：输入书名或者输入作者判断是否存在书籍
&emsp;&emsp;print('3.查询模块')
&emsp;elif oper == '4':
&emsp;&emsp;print('4.查看所有')
&emsp;&emsp;for i in library:
&emsp;&emsp;&emsp;print(f'书名：{i['bookname']},作者：{i['author']}')
&emsp;elif oper == '5':
&emsp;&emsp;print('5.退出')
&emsp;&emsp;print('系统正常退出')
&emsp;&emsp;break
&emsp;else:
&emsp;&emsp;print('请重新选择')

**7. 公共方法**
* max()找出最大值
* list = [1,2,5,6,9]
print(max(list)) # 9
* min()找出最小值
* sum()求和
* abs()绝对值
* sorted()升序排序排序，但是返回的是列表 添加参数 reverse=True 变为降序排序
* chr() 输入ASSC码值返回对应的字母
* ord() 输入字母返回ASSC码值
* isinstance(a,int) 判断类型 第一个参数是变量，第二个参数是类型,如果是则返回True，反之是False
