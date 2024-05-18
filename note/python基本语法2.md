# python基本语法2
### 函数
###### 1.定义函数的格式如下：
&emsp;&emsp;def 函数名():
&emsp;&emsp;&emsp;代码逻辑

def sum(a,b):
&emsp;print(a+b)
#位置传参
sum(1,2)
#关键字传参(不推荐)
sum(b=200,a=100)
**形参**：定义时小括号中的参数，用来接收参数用的
**实参**：调用时小括号中的参数，用来传递给函数用的
>import random
def generate_random(n,m): 
&emsp;for i in range(n):
&emsp;&emsp;&emsp;ran = random.randint(1,10) #随机生成1-10以内的整数
&emsp;&emsp;&emsp;if ran == m:
&emsp;&emsp;&emsp;&emsp;print('我被中断了！')
&emsp;&emsp;&emsp;&emsp;break
&emsp;&emsp;&emsp;print(ran)
generate_random(8,5)

默认参数
>def generate_random(n=6,m=3)
此时我们不想修改n，而是想修改m，那么我们可以如下传参
 generate_random(m=5) 这就表示n依旧使用默认值，而m使用5
 
可变参数：*args 可以接收独立的变量 **kwargs 关键字参数，在函数调用的时候必须传递关键字参数
>例： 要求数值相加，如果求两个数则需要定义两个参数，如果要求多个数的话我们可以利用可变参数
>def get_sum(*args):
&emsp;print(args)
get_sum(1,2) #(1,2)
get_sum(1,2,3,4,5) #(1,2,3,4,5)
***所以可变参数相当于一个容器，形成一个元组***
def get_sum(*args):
&emsp;&emsp;s = 0
&emsp;&emsp;for i in args:
&emsp;&emsp;&emsp;s += i
&emsp;&emsp;print(s)

 拆包和装包
>*a,b,c=1,2,3,4,5
      print(a) #(1,2,3)
    print(b) # 4
    print(c) # 5
>a,b,c = (1,2,3)
    print(a) #1
    print(b) #2
    print(c) #3

>def get_sum(*args):
&emsp;&emsp;s = 0
&emsp;&emsp;for i in args:
&emsp;&emsp;&emsp;s += i
&emsp;&emsp;print(s)    
>如果此时有一个列表，而我们要使用get_sum求值时
    ren_list = [23,4,53,45,77]
    get_sum(*ren_list)
    
关键字参数：**kwargs 
>def show_book(\*\*kwargs)
&emsp;print(kwargs) #{}
**注意\*\*kwargs必须传入的是关键字参数**
show_book(bookname='西游记') #{'bookname':'西游记'}
book = {'bookname':'红楼梦'}
show_book(**bookname)

###### 2.函数返回值
想要在函数中把结果返回给调用者，需要在函数中使用return
>* def add2num(a,b):
    return a+b
>* def buyIceCream()
    return '冰淇淋'
#使用一个变量来接受函数的返回值
food = buyIceCream()

>5个随机数相加
>import random
def get_total(n=5):
&emsp;&emsp;total = 0
&emsp;&emsp;for i in range(n):
&emsp;&emsp;&emsp;ran = random.randint(1,20)
&emsp;&emsp;&emsp;total += ran
 return total
result = get_total()
print(result)

**注意：return可以传多个参数**
>import random
def get_list_total(n=5):
&emsp;total = 0
&emsp;ran_list = []
&emsp;for i in range(n):
&emsp;&emsp;ran = random.randint(1,20)
&emsp;&emsp;ran_list.append(ran)
&emsp;&emsp;total += ran
&emsp;return total,ran_list
result = get_list_total()
print(result)

**3.函数调用**
>在1-20内取5个随机数，求和
>import random
def get_list():
&emsp;ran_list = []
&emsp;for i in range(5):
&emsp;&emsp;&emsp;ran = random.randint(1,20)
&emsp;&emsp;&emsp;ran_list.append(ran) 
&emsp;return ran_list
def get_total():
&emsp;r_list = get_list()
&emsp;if r_list:
&emsp;&emsp;total = 0
&emsp;&emsp;for i in r_list:
&emsp;&emsp;&emsp;total += i
&emsp;return total
res = get_total()
print(res)

**4.全局和局部变量**
>#全局变量
a = 100
def test1():
&emsp;#局部变量
&emsp;a = 0
&emsp;print('a =',a)
test1() # a = 0 #此处打印为函数内部打印，函数在输出的时候会先找自身的值，局部变量的作用范围仅限函数的内部
print('a =',a) # a = 100 #此处打印的任然为全局变量的100

**如果要改变全局a的值的话需要加上global关键字**
>def test2():
&emsp;global a
&emsp;a = 11
test2()
print('a =',a) # a = 11 此时全局的a已经被改变

**global关键字的添加： 只有不可变的类型才需要添加(int str float bool tuple) 
不可变：当改变变量的值时，地址发生了改变 
可变的类型不需要添加(list dict set) 
可变：里面的内容发生了改变，但是地址没有发生改变 python会创建一片小正数空间0-256**
> a = 100
    print(id(a))
    a = 90
    print(id(a))
    二者的地址不一样，因为这属于小整数空间里的值

**引用**
>a = 10
    b = a
    print(b) #10
    a = 5
    print(b) #10
    这里的b的值没有改变，因为b所指向的a的地址，而a重新赋值之后地址发生了变化，而b指向的地址并没有发生变化所以b依然是等于10，这里所用的到特性跟上面的可变不可变类型是一样的
    
**5. 闭包**
函数还可以嵌套定义，即在一个函数内部可以定义另一个函数，有了嵌套函数这种结构，便会产生闭包问题

**局部变量和全局变量**
* 局部变量：在函数的内部定义的变量 我们称之为局部变量
特点：其作用域范围是函数内部，而函数的外部是不可以使用
* 全局变量：定义在函数外部的变量 我们称之为全局变量
特点：可以再函数的外部使用，也可以在函数的内部使用
>def outr():
&emsp;a = 100
def inner():
&emsp;b = 200
&emsp;#内部函数不能修改外部函数的变量
&emsp;#如果我们在inner里面想要修改a的值我们可以使用nonlocal 
&emsp;nonlocal a
&emsp;a = 200
&emsp;print("我是内部函数",a)

闭包的定义 1.嵌套函数 2.内部函数引用了外部函数的变量 3.返回值是内部函数 4.内部函数引用了外部函数的变量
>格式：
    def 外部函数():
    &emsp;def 内部函数():
    &emsp;return 内部函数
def outer(n):
 &emsp;a = 10
 &emsp;def inner():
 &emsp; &emsp;b = a+n
 &emsp; &emsp;print('内部函数',b)
 &emsp;return inner  &emsp;// 返回值是内部函数 
r = outer(5)
print(r) #打印的是return出来的inner函数的地址
r() #内部函数 15

**闭包的总结**
1.闭包优化了变量，原来需要类对象完成的工作，闭包也可以完成
2.由于闭包引用了外部函数的局部变量，则外部函数的局部变量没有及时释放，消耗内存
3.闭包的好处，使代码变得简洁，便于阅读
4.闭包是装饰器的基础

**6. 装饰器**
相当于给一个函数添加功能，比如说一个函数多处项目引用，但并不需要全部更改的时候我们就可以添加装饰器
特点：
**1. 函数作为参数传递给另一个函数
2. 要有闭包的特点**
>定义一个装饰器
def decorate(func):
&emsp;print('wrapper测试')
&emsp;a = 100
&emsp;def wrapper():
&emsp;&emsp;print('111')
&emsp;&emsp;func()
&emsp;&emsp;print(a)
&emsp;print('wrapper加载完成')
&emsp;return wrapper

**使用装饰器: @装饰器名**
>@decorate #如果调用下面的函数的话，在这里wrapper测试和加载完成还是会打印，此时会把下面的参数函数传入到装饰器里面
def house():
&emsp;print('房子')
house() #111 房子 100

>**若需要传参**
def decorate(func):
&emsp;def wrapper(x):
&emsp;&emsp;print('111')
&emsp;&emsp;func(x)
&emsp;return wrapper
@decorate
#此时的f1是需要传参的，而我们f1调用的时候实际上是调用的wrapper所以我们要在内层的wrapper上给上参数，然后传给里面的func
def f1(n):
&emsp;print(n)
f1(5)

>**如果需要传递的参数不确定的话，在wrapper传参的时候传入的是\*args可变参数，如果后面还会传入指定关键字的话我们还可以加上\*\*kwargs，这样任何函数都可以使用**
 def decorate(func):
 &emsp;def wrapper(*args,**kwargs):
&emsp;&emsp;print('111')
 &emsp;&emsp;func(*args,**kwargs)
&emsp;return wrapper
**可以使用多个装饰器，并且执行顺序是从下往上，所以先执行装饰器1再执行装饰器2**
@decorate2
@decorate1
def func():
func()

>**带参数的装饰器**
def outer(a):
&emsp;def decorate(func):&emsp;//此时的func即为house()函数
&emsp;&emsp;def wrapper(*args,**kwargs):
&emsp;&emsp;&emsp;&emsp;func()
&emsp;&emsp;&emsp;&emsp;print('111',a)
&emsp;&emsp;return wrapper
&emsp;return decorate
@outer(a=10) &emsp;//调用装饰器
def house(): &emsp;//因为house()上方调用装饰器outer，即将house作为参数传递
&emsp;print('222')
house()
结果：222
&emsp;&emsp;111 10


### 匿名函数
作用：简化函数定义
>格式:
   **lambda 参数1,参数2...:运算**

>s = lambda a,b:a+b     &emsp; //定义匿名函数
result = s(1,2)
print(result)

>匿名函数作为参数
def fun(a,b,func):
&emsp;&emsp;s = func(a,b)  &emsp;//func()为匿名函数
&emsp;&emsp;print(s)
fun(1,2,lambda a,b:a+b)

**匿名函数与内置函数的结合使用**
>list = [{'a':10,'b':20},{'a':13,'b':20},{'a':9,'b':20}]
m = max(list,key=lambda x:x['a'])  &emsp; &emsp;//变量x为键值对，在list列表中查找key为a的键值对
print(m) #{a:'13',b:'20'}

### 异常
1. 异常处理：
try:
&emsp;把可能出现异常的代码放在try里面
except:
&emsp;如果有异常执行的代码
finally:(可要可不要，一般用在文件处理和数据库操作中，因为无论是否异常都要关闭)
&emsp;无论是否存在异常都会被执行的代码

>def func():
&emsp;stream = None
&emsp;try:
&emsp;&emsp;stream = open(r'文件路径')
&emsp;&emsp;container = steam.read()
&emsp;&emsp;print(container)
&emsp;except Exception as err:
&emsp;&emsp;print(err)
&emsp;finally:
&emsp;&emsp;if stream:
&emsp;&emsp;&emsp;stream.close()

2. 如果有多种错误需要判断的话可以在except后面加错误类型，因为所有的错误类型都是从Exception里面衍生出来的，所以错误类型直接使用Exception的话会接纳所有的错误，所以一般Exception放在最后面，最大的放在最下面
>except ZeroDivisionError:
&emsp;print('被除数不能为0')
except ValueError:
&emsp;print('必须输入(需要输入的类型)')
except Exception:
&emsp;print('出错了')
如果要打印出错的原因的话
except Exception as err:
&emsp;print('出错了',err)

   
**抛出异常 raise 可以自己定义报错**
>#注册 用户名必须6位
def register():
&emsp;username = input('输入用户名')
&emsp;if len(username)<6:
&emsp;&emsp;raise Exception('用户长度必须6位以上')
&emsp;else:
&emsp;&emsp;print('输入的用户名是：',username)

>try:
&emsp;register()
except Exception as err:
&emsp;print(err)
&emsp;print('注册失败')
else:
&emsp;print('注册成功')

### 生成器
得到生成器方式：
**1. 通过列表推导式得到生成器**
通过列表推导式生成的结果会占用内存，所以我们可以使用()替换[]来对代码进行包裹

>**#得到生成器**
>* g = (x*3 for x in range(20))
print(type(g)) # generator
如果直接打印g的话会得到一个内存地址

>* print(g.\__next__())#0
print(g.\__next__())#3
每调用一次__next__得到一个元素
print(next(g))#6 &emsp;//**系统内置的next方法里面放的是生成器对象，每次调用会产生一个元素**

>* 这里我们就可以使用循环来做操作
g = (x*3 for x in range(20))
while True:
&emsp;try:
&emsp;&emsp;e = next(g)
&emsp;&emsp;print(e)
&emsp;except:
&emsp;&emsp;print('没有更多元素啦')
&emsp;&emsp;break

**2. 借助函数**
**只要函数中出现了yield关键字，说明该函数是一个生成器**
步骤：
1.定义一个函数，函数中使用yield关键字
2.调用函数，接收调用的结果
3.得到的结果就是生成器
4.借助next()或者__next__()得到元素

>* def func(): &emsp;//func()为生成器
&emsp;n = 0
&emsp;while True:
&emsp;&emsp;n +=1
&emsp;&emsp;yield n &emsp;//相当于return + 暂停
g = func()
print(next(g))  &emsp;//1


>* def fib(length): &emsp;//斐波那契数列(后面数是前面俩个数相加)
&emsp;a,b = 0,1
&emsp;n = 0
&emsp;while n < length:
&emsp;&emsp;&emsp;yield b  &emsp;//每次返回数据b(1,1,2,3,5,8...)
&emsp;&emsp;&emsp;a,b = b,a+b
&emsp;&emsp;&emsp;n+=1
g = fib(8) &emsp;//g为生成器对象
print(next(g))  &emsp;//1&emsp;//进入fib()函数中，执行到yield b时，返回b=1并终止循环
print(g.__next__())&emsp;//1&emsp;//定位到上次yield b之后，a,b=...，在循环再次执行到yield时终止
print(g.__next__())&emsp;//2
print(g.__next__())&emsp;//3

**生成器方法：**
* \__next__():获取下一个元素
* send():向每次生成器调用中传值 注意：第一次电泳send(None)

>def gen():
&emsp;i = 0
&emsp;while i < 5:
&emsp;&emsp;temp = yield i  &emsp;//temp为3  &emsp;//当i为1时，返回结果1，并终止循环
&emsp;&emsp;print('temp',temp)
&emsp;&emsp;for x in range(temp):
&emsp;&emsp;&emsp;&emsp;print('---->',x)
&emsp;&emsp;&emsp;&emsp;print('****')
&emsp;&emsp;i+=1
&emsp;return '没有更多的数据'
g = gen()
g.send(None)&emsp;//第一次电泳send(None)
n1 = g.send(3) &emsp;//首先定位到yield那行
print('n1:',n1) &emsp;//n1=1


**生成器的应用：协程**
>如果让任务交替运行要改写为
def task1(n): &emsp;//生成器
&emsp;for i in range(n):
&emsp;&emsp;print('正在搬第{}块砖！'.format(i))
&emsp;&emsp;yield None
def task2(n):
&emsp;for i in range(n):
&emsp;&emsp;print('正在听第{}首歌！'.format(i))
&emsp;&emsp;yield None
g1 = task1(10)
g2 = task2(5)
while True:
&emsp;try:
&emsp;&emsp;g1.\__next__() &emsp;//每次调用next(),都是从上次结束位置之后开始执行
&emsp;&emsp;g2.\__next__()
&emsp;except:
&emsp;&emsp;pass
正在搬第0块砖！
正在听第0首歌！
正在搬第1块砖！
正在听第1首歌！
正在搬第2块砖！
正在听第2首歌！
正在搬第3块砖！
正在听第3首歌！
正在搬第4块砖！













