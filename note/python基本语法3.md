# python基本语法3
### 面向对象
#### 定义类
```
 class 类名：
      类属性
      类方法
```
* 类方法特点(在对象没有创建的时候已经加载了，所以可以不需要创建对象就能使用，使用方法 类名.方法名())
    1. 定义需要依赖装饰器@classmethod
    2. 类方法中参数不是一个对象，而是类
    3. 类方法只能使用类属性
    4. 类方法不能使用普通方法
* 类方法的作用
    因为只能访问类属性和类方法，所以可以在对象创建之前，如果需要完成一些动作(功能)
 ```   
class Phone:
    #属性(当然属性也可以不赋值，比如是None或者0)
     brand = '华为'
     color = '黑色'
     type = 'Mate30'
     price = 3999
    #方法(只要在类中定义方法，里面的self是默认的，是要依赖self)
    def call(self):
           print('可以打电话！')
    def send_message(self):
           print('可以发消息！')
 ```
**类方法(没有对象也可以使用，因为是依靠类来存在的,里面传入的cls是类本身)**
```  
@classmethod #使用装饰器
def test(cls): #cls是class的简写    //类方法
    print(cls)
```
**静态方法**
```
@staticmethod
def test():    //里面所能用的东西和类方法一样
```
**创建对象**
```
p = Phone()
p.brand = '小米' #修改phone中的属性
```
**魔法方法,只要创建对象的时候就会默认执行的方法**
```
class Phone:
   魔法方法1 __init__(self)初始化魔术方法
   在初始化对象的时候触发
   def __init__(self,brand,price):&emsp;//加上了后面的参数之后在定义对象的时候就必须传入这两个参数
   self.brand = brand
   self.price = price
```
* 魔法方法2 __new__(cls)实例化魔术方法
 在实例化时进行触发
 ```
def __new__(cls):
      print('---->new')
```
* 在方法中也可以使用属性
```
def call(self):
   print('可以使用'+self.brand+'打电话！')
p = Phone('华为',1999)
print(p.brand)
p.call()
```
### 类方法的调用
一个类中可以定义多个方法，而且方法之间是可以互相调用的。而且方法中还可以使用属性。
```
class Person：
    def __init__(slef,name,age):
       self.name = name
       self.age = age
    #对象方法
    def eat(self,food): 
       print(self.name + '喜欢吃:')&emsp;//可以调用类的属性
       for i in food:
            print(i)
    def sleep(self,hours):
        print('{}睡觉啦，一下子睡了{}小时'.format(self.name,hours))
    def paly(self,gname):
        self.sleep(1)
        print('{}喜欢玩{}'.format(self.name,gname))
dong = Person('xindong',18)
dong.eat('士力架')
dong.sleep(10)
qiang = Person('aqiang',20)
qiang.sleep(2)
foods = ['麦当劳','鱼非鱼','大鸭梨烤鸭']
qiang.eat(foods)
qiang.sleep(8)
qiang.play('足球')
```
### 私有化
私有化的好处在于不让外界随便修改属性,并且访问范围也仅限于这个类中
封装：
1.私有化属性
2.定义共有set和get方法
```
class Student:
    def __init__(self,name,age):
        self.name = name
        self.age = age
        self.__score = 59&emsp;//私有变量
   #定义公有的set和get方法
   #set为了赋值
   def setScore(self,score):&emsp;&emsp;//定义成函数的好处在于可以进行判断
        self.__score = score
   def getScore(self):&emsp;//get获取值
        return self.__score     
   def __str__(self):
        return '姓名：{},年龄：{},考试分数{}'.format(self.name,self.age,self.__score)
lisi = Student('lisi',18)
print(lisi)
lisi.age = 21  #可以修改
//lisi.__score = 95  #不能直接修改私有变量，必须得使用set函数修改
lisi.setScore(95)&emsp;//私有变量必须要使用set,get修改获取
lisi.getScore()
```
>**我们可以使用property装饰器,简化私有变量修改的步骤**
```
class Student:
    def __init__(self,name,age):
         self.__name = name
         self.__age = age
    @property   //一定要先定义get的age，然后才能利用其来绑定下面的setter
    def age(self):
       return self.__age
    @age.setter &emsp;//因为set依赖于get
    def age(self,age):
       self.__age = age
    def \__str\__(self):
        return '姓名:{},年龄:{}'.format(self.__name,self.__age)
s = Student('lisi',20)
 print(s.age)    //只要加了装饰，就可以像参数一样用，不用加括号，就可以这样取值
 print(s.\__str\__())   //可以打印出里面的变量参数
```
**例题：**
```
公路(Road):
    属性：公路名称，公路长度
车(Car):
    属性：车名，时速
```
方法：
1. 求车名在那条公路上以多少的时速行驶了多长
        get_time(self,road)
2. 初始化车属性信息__init__方法
3. 打印对象显示车的属性信息
```
class Road:
    def __init__(self,name,len):
        self.name = name
        self.len = len
class Car:
    def __init__(self,brand,speed):
        self.brand = brand
        self.speed = speed
    def get_time(self,road):
        ran_time = random.randint(1,10)
        msg = '{}品牌的车在{}上以{}速度行驶了{}小时'.format(self.brand,road.name,self.speed,ran_time)
    def __str__(self):
        return '{}品牌的,速度:{}'.format(self.brand,self.speed)
#创建实例
r = Road('青藏高速',5000)
audi = Car('奥迪',120)
audi.get_time(r)
```
#### 继承
特点：
1. 如果子类中不定义__init__ ，调用父类super 就会调用父类的init
2. 如果类继承了父类，并且也需要定义自己的init的时候，就需要在当前类的init中调用下父类的init
3. 调用父类的两种方式 super().__init__(参数)  super(类名,self).__init__(参数)
4. 如果父类和子类都有相同的方法名，那默认的搜索原则是先找当前类，再去找父类。如果在该方法中还是需要父类的操作的话，只需要在方法中加super().方法名()即可  override：重写，覆盖
```
class Person: &emsp;//基类
    def __init__(self,name,age):
         self.name = name
         self.age = age
class Student(Person): #子类继承父类
    pass
class Employee(Person): #子类
    pass
class Doctor(Person): #子类
    pass
s = Student('lisi',18)
```
**子类里面调用父类方法**
```
class Person: #基类
   def __init__(self):
       self.name = '匿名'
       self.age = 18
class Student(Person): #子类
   def __init__(self):
       print('----->student的init')
       super().__init__()&emsp;//调用父类的init //super()表示找到父类
s = Student()
```
**如果需要传参的话**
```
class Person: &emsp;//基类
    def __init__(self,name):
        self.name = name
        self.age = 18
    def eat(self):
        print(self.name + '正在吃饭(父类)')
class Student(Person): &emsp;//子类
    def __init__(self,name,class):
        self.class = class
        print('----->student的init,{}'.format(self.class))
        super().__init__(name) //调用父类的init super()表示找到父类
    def eat(self):
        print(self.name + '正在吃饭')
s = Student('李四','大数据')
s.eat() //子类和父类有相同的方法,会调用子类自己的方法
```
**多继承**
```
class A:
   def test(self):
       print('AAAAAAAAAA')
class B:
   def test1(self):
       print('BBBBBBBBBB')
class C(A,B):   //#C继承A和B
   def test2(self):
       print('CCCCCCC')
c = C()
c.test()
c.test1()
c.test2()
```
**搜索原则**
```
class Base:
    def test(self):
        print('----Base----')
class A(Base):
    def test(self):
        print('AAAAAAAAAA')
class B(Base):
    def test1(self):
        print('BBBBBBBBBB')
class C(Base):#C继承A和B
    def test2(self):
        print('CCCCCCC')
class D(A,B,C):
   pass
d = D()
d.test() #结果打印的是AAAAAA
执行步骤:1.查找D()内发现没有test()函数，2.查找A()函数发现有test()函数执行，如果没有则顺序查找B,C,Base
```
**多态**
```
class Person:
   role = 'Pet'
   def __init__(self,name):
      self.name = name
   def feed_pet(self,pet):
      if isinstance(pet,Pet): #判断传过来的参数是什么类型的，这里加上判断是因为上层并不会判断pet的类型，也就是说不管是不是pet类型都能传进来，所以在这里做了限制
        print('{}喜欢养宠物:{}'.format(self.name,pet.nickname))
     else:
        print('不是宠物类型的')
class Pet:
    def __init__(self,nickname,age):
        self.nickname = nickname
        self.age = age
    def show(self):
        print('昵称:{},年龄:{}'.format(self.nickname,self.age))
class Cat(Pet):   //猫继承宠物类
    role = '猫'
    def catch_mouse(self):
          print('抓老鼠...')
class Dog(Pet): //狗继承宠物类
    role = '狗'
    def watch_house(self):
         print('看家高手')
cat = Cat('花花',2)&emsp;//创建对象
dog = Dog('大黄',4)
person = Person('李四') 
person.feed_pet(cat)
```
#### 模块
在python中一个脚本(.py)文件就是一个模块，创建模块实际上就是创建一个.py文件，可以被其他模块导入并使用
```
import 文件名
    然后下面就可以使用文件中的函数及属性了
    使用方法： 文件名.属性名  文件名.函数  文件名.类
```    
#### 包的导入
包的导入类似模块的导入
```
    import 包名
    from 包名.模块名 import *
    例如：在user的包里面有一个models模块，models模块里面有一个show方法，我们可以 from user.models import show
```
#### 文件
* 文件的打开与关闭
```
打开文件/创建文件
在python，使用open函数，可以打开一个已经存在的文件，或者创建一个新文件
open(文件路径,访问模式)
f = open('test.txt','w')&emsp;//当当前文件夹没有这个文件的时候使用open是在当前文件夹中创建了这个文件
fp = open('a.txt','w')
fp.write('hello')
fp.write('hello world' * 5) //如果要写入多条相同的内容的话可以在后面写乘号加遍数
fp.close()
```
**如果再次运行上方代码 文件中的内容还是5遍
意味着如果文件存在 会先清空原来的数据然后再写**

`fp = open('test.txt','a')&emsp;//如果想每次执行之后都要追加数据，则需要把模式改为'a'`

* 读数据
```
fp = open('test.txt','r')
content = fp.read()&emsp;//默认情况下,read是一字节一字节的读,效率比较低
content = fp.readline() //一行一行的读取,但是只能读取一行
readlines可以按照行来读取 但是会将所有的数据都读取到 并且以一个列表的形式返回
#而列表中的元素是一行一行的元素
content = fp.readlines()&emsp; //将所有的数据都读取到并且以一个列表的形式返回
```
#### 文件的序列化和反序列化
通过文件操作，我们可以将字符串写入到一个本地文件。但是，如果是一个对象(例如列表、字典、元组等)，就无法直接写入到一个文件里，需要对这个对象进行序列化，然后才能写入到文件里。
* 对象 --> 字节序列 === 序列化
* 字节序列 --> 对象 === 反序列化

**使用JSON实现序列化**
```
#序列化的两种方式
#dumps()
fp = open('test.txt','w')   //1.创建一个文件
name_list = ['张三','李四','王五']   //2.定义一个列表
import json   //3.引入json模块
names = json.dumps(name_list)   //4.序列化 将python对象 变成json字符串
fp.write(names)   //5.将names写入到文件中
fp.close()
//写入到文件中的为 ['张三','李四','王五']
//我们在使用scrapy框架的时候 该框架会返回一个对象 我们要将对象写入到文件中 就要使用json.dumps

#dump
#在将对象转换为字符串的同时 指定一个文件的对象 然后把转换后的字符串写入到这个文件里
fp = open('test.txt','w')   //1.创建一个文件
name_list = ['张三','李四','王五']   //2.定义一个列表
import json
json.dump(name_list,fp)   //4.使用dump写入，相当于names = json.dumps(name_list)和fp.write(names)
fp.close()
```
**反序列化**
将json的字符串变成一个python对象
```
fp = open('test.txt','r')
content=fp.readlines()
import json
json.load(content)  //将json字符串变成python对象
fp.close()

```






