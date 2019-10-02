### 1.面向过程 vs面向对象

	  ####  	1.1. 面向过程
	
	-  优点：极大的降低了写程序的复杂度，只需要顺着要执行的步骤，堆叠代码即可

-  缺点：一套流水线或者流程就是用来解决一个问题，代码牵一发而动全身

  #### 1.2.面向对象

- 优点：优点是：解决了程序的扩展性。对某一个对象单独修改，会立刻反映到整个体系中，如对游戏中一个人物参数的特征和技能修改都很容易

- 缺点： 可控性差，无法向面向过程的程序设计流水线式的可以很精准的预测问题的处理流程与结果，面向对象的程序一旦开始就由对象之间的交互解决问题**，即便是上帝也无法预测最终结果。于是我们经常看到一个游戏人某一参数的修改极有可能导致阴霸的技能出现，一刀砍死3个人，这个游戏就失去平衡

### 2 .类，对象的初始

python中一切皆对象

#### 	2.1. 类的初始

	    ##### 			2.1.1声明类			

```
'''
class 类名:
    '类的文档字符串'
    类体
'''
#我们创建一个类
class Data:
    pass
```

```python
class Person:   #定义一个人类
    role = 'person'  #人的角色属性都是人
    def walk(self):  #人都可以走路，也就是有一个走路方法，也叫动态属性
        print("person is walking...")
```

类的两种作用：

- 属性的引用

  ```python
  class Person:   #定义一个人类
      role = 'person'  #人的角色属性都是人
      def walk(self):  #人都可以走路，也就是有一个走路方法
          print("person is walking...")
  
  
  print(Person.role)  #查看人的role属性
  print(Person.walk)  #引用人的走路方法，注意，这里不是在调用
  ```

- 实例化

  ​    类名加括号就是实例化，会自动触发`__init__`函数的运行，可以用它来为每个实例定制自己的特征

  ```python
  class Person:   #定义一个人类
      role = 'person'  #人的角色属性都是人
      def __init__(self,name):
          self.name = name  # 每一个角色都有自己的昵称;
          
      def walk(self):  #人都可以走路，也就是有一个走路方法
          print("person is walking...")
  
  
  alex = Person(alex) # 类的实例化就等于在执行Person.__init__()方法
  ```

  

  #### 2.1.2.  查看类的属性和调用方法

  ```python
  print(egg.name)     #查看属性直接 对象名.属性名
  print(egg.walk())   #调用方法，对象名.方法名()
  print(Person__dict__)# 查看类中的所有内容：类名.__dict__方式。
  ```

  #### 2.2 类名操作动态的方法

  ```python
  class Human:
      """
      此类主要是构建人类
      """
      mind = '有思想'  # 第一部分：静态属性 属性 静态变量 静态字段
      dic = {}
      l1 = []
      def work(self): # 第二部分：方法 函数 动态属性
          # print(self)
          print('人类会工作')
      def tools(self):
          print('人类会使用工具')
  
  Human.work(111)
  Human.tools(111)
  下面可以做，但不用。
  Human.__dict__['work'](111)
  ```

### 3 对象

#### 3.1 实例化对象

```python

class Human:
    mind = '有思想'
    def __init__(self):
        print(666)
        print(self)  # <__main__.Human object at 0x00000191508AA828>

    def work(self): 
        print('人类会工作')

    def tools(self):
        print('人类会使用工具')
obj = Human() # 只要实例化对象，它会自动执行__init__方法
print(obj)  # <__main__.Human object at 0x00000191508AA828>
# 并且obj的地址与self的地址相同
```

实例化对象的过程

- 在内存中开辟了一个对象空间。
- 自动执行类中的`__init__`方法，并将这个对象空间（内存地址）传给了`__init__`方法的第一个位置参数self。
- 在`__init__ `方法中通过self给对象空间添加属性。

#### 3.2 对象操作对象的空间属相

##### 3.2.1  对象查询对象中所有属性。 对象.`_dict__`

```
class Human:

    mind = '有思想'
    language = '实用语言'
    def __init__(self,name,sex,age,hobby):
        # self 和 obj 指向的是同一个内存地址同一个空间，下面就是通过self给这个对象空间封装四个属性。
        self.n = name
        self.s = sex
        self.a = age
        self.h = hobby

obj = Human('barry','男',18,'运动')
print(obj.__dict__)  # {'n': 'barry', 'h': '运动', 's': '男', 'a': 18}
```

##### 3.2.2 对象操作对象中的单个属性。 万能的点 .

```python
class Human:

    mind = '有思想'
    language = '实用语言'
    def __init__(self,name,sex,age,hobby):
        # self 和 obj 指向的是同一个内存地址同一个空间，下面就是通过self给这个对象空间封装四个属性。
        self.n = name
        self.s = sex
        self.a = age
        self.h = hobby

obj = Human('barry','男',18,'运动')
obj.job = 'IT'  # 增
del obj.n  # 删
obj.s = '女' # 改
print(obj.s)  # 查
print(obj.__dict__)
```

#### 3.3对象查看类中的属性

```python
class Human:

    mind = '有思想'
    language = '实用语言'
    def __init__(self,name,sex,age,hobby):
        self.n = name
        self.s = sex
        self.a = age
        self.h = hobby

obj = Human('barry','男',18,'运动')
print(obj.mind)
print(obj.language)
obj.a = 666
print(obj.a)
```

#### 3.4 对象操作类中的方法

```python
class Human:

    mind = '有思想'
    language = '实用语言'
    def __init__(self,name,sex,age,hobby):
        self.n = name
        self.s = sex
        self.a = age
        self.h = hobby

    def work(self):
        print(self)
        print('人类会工作')

    def tools(self):
        print('人类会使用工具')

obj = Human('barry','男',18,'运动')
obj.work()
obj.tools()
```

类中的方法一般都是通过对象执行的（出去类方法，静态方法外），并且对象执行这些方法都会自动将对象空间传给方法中的第一个参数self.

**self 是什么？**

```
self其实就是类中方法（函数）的第一个位置参数，只不过解释器会自动将调用这个函数的对象传给self。所以咱们把类中的方法的第一个参数约定俗成设置成self, 代表这个就是对象。
```

### 4 类的空间问题

#### 4.1 添加对象，类的属性

```python
class A:
    def __init__(self,name):
        self.name = name

    def func(self,sex):
        self.sex = sex

# 类外面可以：
obj = A('barry')
obj.age = 18
print(obj.__dict__)  # {'name': 'barry', 'age': 18}

# 类内部也可以：
obj = A('barry') # __init__方法可以。
obj.func('男')  # func 方法也可以。        
```

```python
class A:
    def __init__(self,name):
        self.name = name

    def func(self,sex):
        self.sex = sex
    
    def func1(self):
        A.bbb = 'ccc'
A.aaa = 'taibai'
print(A.__dict__)

# 类的内部也可以添加。

A.func1(111)
print(A.__dict__)
```

**总结：**

在类的内部，外部，都可以添加类的属性，对象的属性

- 对象查找属性的顺序：先从对象空间找  ------> 类空间找 ------> 父类空间找 ------->.....

- 类名查找属性的顺序：先从本类空间找 -------> 父类空间找--------> ........

上面的顺序都是单向不可逆，类名不可能找到对象的属性。

#### 4.2 类和类的关系

1. 依赖关系： 将一个类的对象或者类名传到另一个类的方法使用
2. 关联关系：两种事物必须是互相关联的. 但是在某些特殊情况下是可以更改和更换的.
3. 组合关系：将一个类的对象封装到另一个类的对象的属性中，就叫组合。
4. 聚合关系：属于关联关系中的⼀种特例. 写法上差不多. 组合关系比聚合还要紧密. 比如⼈的⼤脑, ⼼脏, 各个器官. 这些器官组合成⼀个⼈. 这时. ⼈如果挂了. 其他的东⻄也跟着挂了
5. 实现关系
6. 继承关系(类的三大特性之一：继承。)

##### 4.2.1 依赖关系

设计⼀个场景. 还是最初的那个例⼦. 要把⼤象装冰箱. 注意. 在这个场景中, 其实是存在了两种事物的. ⼀个是⼤象, ⼤象负责整个事件的掌控者, 还有⼀个是冰箱, 冰箱负责被⼤象操纵. 

⾸先, 写出两个类, ⼀个是⼤象类, ⼀个是冰箱类

```python
class Elphant:
    def __init__(self, name):
        self.name = name

    def open(self):
        '''
        开⻔
        '''
        pass
    
    def close(self):
        '''
        关⻔
        '''
        pass


class Refrigerator:
    
    def open_door(self):
        print("冰箱⻔被打开了")
    
    def close_door(self):
        print("冰箱⻔被关上了")
```

冰箱的功能非常简单, 只要会开⻔, 关⻔就⾏了. 但是⼤象就没那么简单了. 想想. ⼤象开⻔和关⻔的时候是不是要先找个冰箱啊. 然后呢? 打开冰箱⻔. 是不是打开刚才找到的那个冰箱⻔. 然后装⾃⼰. 最后呢? 关冰箱⻔, 注意, 关的是刚才那个冰箱吧. 也就是说. 开⻔和关⻔⽤的是同⼀个冰箱. 并且. ⼤象有更换冰箱的权利, 想进那个冰箱就进那个冰箱. 这时, ⼤象类和冰箱类的关系并没有那么的紧密. 因为⼤象可以指定任何⼀个冰箱. 接下来. 我们把代码完善⼀下.

```python
class Elphant:
    def __init__(self, name):
        self.name = name

    def open(self,obj1):
        # obj是冰箱实例化的对象
        '''
        开⻔

        '''
        print('大象要开门了，默念三声，开')
        obj1.open_door()

    def close(self):
        '''
        关⻔
        '''
        print('大象要关门了，默念三声，关')


class Refrigerator:

    def open_door(self):
        print("冰箱⻔被打开了")

    def close_door(self):
        print("冰箱⻔被关上了")


elphant1 = Elphant('大象')# 实例大象类
haier = Refrigerator() # 实例冰箱类
elphant1.open(haier) # 将大象放在冰箱中
```

 ##### 4.2.2 关联关系

```python
class Boy:
    def__init__(self,name,girlFriend=None):
        self.name = name
        self.girlFriend = girlFriend

    def have_a_diner(self):
        if self.girlFriend:
            print('%s 和 %s 一起晚饭'%(self.name,self.girlFriend.name))
        else:
            print('单身狗，吃什么饭')


class Girl:
    def __init__(self,name):
        self.name = name
class Girl:
    def __init__(self,name):
        self.name = name
b = Boy('日天')
b.have_a_diner() # 此时是单身狗

# 突然有一天，日天牛逼了
b.girlFriend = Girl("如花")
b.have_a_diner()  #共进晚餐        
```

学校和老师的关系

```python
class School:

    def __init__(self,name,address):
        self.name = name
        self.address = address
        self.teacher_list = []

    def append_teacher(self,teacher):
        self.teacher_list.append(teacher)
        
class Teacher:

    def __init__(self,name,school):
        self.name = name
        self.school = school

s1 = School('北京校区','美丽的沙河')
s2 = School('上海校区','上海迪士尼旁边')
s3 = School('深圳校区','南山区')

t1 = Teacher('武大',s1)
t2 = Teacher('海峰',s2)
t3 = Teacher('日天',s3)

s1.append_teacher(t1)
s1.append_teacher(t2)
s1.append_teacher(t3)

# print(s1.teacher_list)
# for teacher in s1.teacher_list:
#     print(teacher.name)
```

##### 4.2.3 组合关系

**将一个类的对象封装到另一个类的对象的属性中，就叫组合。**

几个游戏人物实现互殴

```
class Gamerole:
    def __init__(self,name,ad,hp):
        self.name = name
        self.ad = ad
        self.hp = hp
    def attack(self,p1):
        p1.hp -= self.ad
        print('%s攻击%s,%s掉了%s血,还剩%s血'%(self.name,p1.name,p1.name,self.ad,p1.hp))
        
    def equip_weapon(self,wea):
        self.wea = wea  # 组合：给一个对象封装一个属性改属性是另一个类的对象
class Weapon:
    def __init__(self,name,ad):
        self.name = name
        self.ad = ad
    def weapon_attack(self,p1,p2):
        p2.hp = p2.hp - self.ad - p1.ad
        print('%s 利用 %s 攻击了%s,%s还剩%s血'
              %(p1.name,self.name,p2.name,p2.name,p2.hp))


# 实例化三个人物对象：
barry = Gamerole('太白',10,200)
panky = Gamerole('金莲',20,50)
pillow = Weapon('绣花枕头',2)

# 给人物装备武器对象。
barry.equip_weapon(pillow)

# 开始攻击
barry.wea.weapon_attack(barry,panky)
```

##### 4.2.4 继承关系

继承（英语：inheritance）是面向对象软件技术当中的一个概念。如果一个类别A“继承自”另一个类别B，就把这个A称为“B的子类别”，而把B称为“A的父类别”也可以称“B是A的超类”。继承可以使得子类别具有父类别的各种属性和方法，而不需要再次编写相同的代码。在令子类别继承父类别的同时，可以重新定义某些属性，并重写某些方法，即覆盖父类别的原有属性和方法，使其获得与父类别不同的功能。另外，为子类别追加新的属性和方法也是常见的做法。 一般静态的面向对象编程语言，继承属于静态的，意即在子类别的行为在编译期就已经决定，无法在执行期扩充。

字面意思就是：子承父业，合法继承家产，就是如果你是独生子，而且你也很孝顺，不出意外，你会继承你父母所有家产，他们的所有财产都会由你使用（败家子儿除外）。

```python
# 3 个类，具有相同的属性
class Person:
    def __init__(self,name,sex,age):
        self.name = name
        self.age = age
        self.sex = sex

class Cat:
    def __init__(self,name,sex,age):
        self.name = name
        self.age = age
        self.sex = sex

class Dog:
    def __init__(self,name,sex,age):
        self.name = name
        self.age = age
        self.sex = sex

# 继承的用法：创建一个父类
class Aniaml(object):
    def __init__(self,name,sex,age):
            self.name = name
            self.age = age
            self.sex = sex

### 这些类继承父类，就有了父类的属性
class Person(Aniaml):
    pass

class Cat(Aniaml):
    pass

class Dog(Aniaml):
    pass
```

**继承的优点**

- 增加了类的耦合性（耦合性不宜多，易精）
- 减少了重复的代码
- 使得代码更加规范，合理化

### 5 继承

#### 5.1 单继承

##### 5.1.1 类名，对象执行父类方法

```python
class Aniaml(object):
    type_name = '动物类'

    def __init__(self,name,sex,age):
            self.name = name
            self.age = age
            self.sex = sex

    def eat(self):
        print(self)
        print('吃东西')


class Person(Aniaml):
    pass


class Cat(Aniaml):
    pass


class Dog(Aniaml):
    pass

# 类名：
print(Person.type_name)  # 可以调用父类的属性，方法。
Person.eat(111)
print(Person.type_name)

# 对象：
# 实例化对象
p1 = Person('春哥','男',18)
print(p1.__dict__)
# 对象执行类的父类的属性，方法。
print(p1.type_name)
p1.type_name = '666'
print(p1)
p1.eat()
```

##### 5.5.2 执行顺序

```python
class Aniaml(object):
    type_name = '动物类'
    def __init__(self,name,sex,age):
            self.name = name
            self.age = age
            self.sex = sex

    def eat(self):
        print(self)
        print('吃东西')

class Person(Aniaml):
    
    def eat(self):
        print('%s 吃饭'%self.name)
        
class Cat(Aniaml):
    pass

class Dog(Aniaml):
    pass

p1 = Person('barry','男',18)
# 实例化对象时必须执行__init__方法,类中没有，从父类找，父类没有，从object类中找。
p1.eat()
# 先要执行自己类中的eat方法，自己类没有才能执行父类中的方法。
```

##### 5.5.3 同时执行类以及父类方法

方式一

```python
class Aniaml(object):
    type_name = '动物类'
    def __init__(self,name,sex,age):
            self.name = name
            self.age = age
            self.sex = sex

    def eat(self):
        print('吃东西')

class Person(Aniaml):
    def __init__(self,name,sex,age,mind):
        '''
        self = p1
        name = '春哥'
        sex = 'laddboy'
        age = 18
        mind = '有思想'
        '''
        # Aniaml.__init__(self,name,sex,age)  # 方法一
        self.mind = mind

    def eat(self):
        # 方式一
        #Aniaml.eat()
        # 方式二
        super().eat()
        print('%s 吃饭'%self.name)
class Cat(Aniaml):
    pass

class Dog(Aniaml):
    pass

# 方法一： Aniaml.__init__(self,name,sex,age)
# p1 = Person('春哥','laddboy',18,'有思想')
# print(p1.__dict__)
```

#### 5.2 多继承

```
class ShenXian: # 神仙
    def fei(self):
        print("神仙都会⻜")
class Monkey: # 猴
    def chitao(self):
        print("猴⼦喜欢吃桃⼦")
class SunWukong(ShenXian, Monkey): # 孙悟空是神仙, 同时也是⼀只猴
    pass
sxz = SunWukong() # 孙悟空
sxz.chitao() # 会吃桃⼦
sxz.fei() # 会⻜
```

在python2x版本中存在两种类.：
　　⼀个叫**经典类**. 在python2.2之前. ⼀直使⽤的是经典类. 经典类在基类的根如果什么都不写.深度优先遍历
　　⼀个叫**新式类**. 在python2.2之后出现了新式类. 新式类的特点是基类的根是object类。
python3x版本中只有一种类：
python3中使⽤的都是**新式类**. 如果基类谁都不继承. 那这个类会默认继承 object `**mro**` c3算法

### 6 面向对向的三大特性

#### 6.1 封装

把很多数据封装到⼀个对象中. 把固定功能的代码封装到⼀个代码块, 函数, 对象, 打包成模块. 这都属于封装的思想. 具体的情况具体分析. 比如. 你写了⼀个很⽜B的函数. 那这个也可以被称为封装. 在⾯向对象思想中. 是把⼀些看似⽆关紧要的内容组合到⼀起统⼀进⾏存储和使⽤. 这就是封装. 	

#### 6.2 继承

⼦类可以⾃动拥有⽗类中除了私有属性外的其他所有内容. 说⽩了, ⼉⼦可以随便⽤爹的东⻄. 但是朋友们, ⼀定要认清楚⼀个事情. 必须先有爹, 后有⼉⼦. 顺序不能乱, 在python中实现继承非常简单. 在声明类的时候, 在类名后⾯添加⼀个⼩括号,就可以完成继承关系. 那么什么情况可以使⽤继承呢? 单纯的从代码层⾯上来看. 两个类具有相同的功能或者特征的时候. 可以采⽤继承的形式. 提取⼀个⽗类, 这个⽗类中编写着两个类相同的部分. 然后两个类分别取继承这个类就可以了. 这样写的好处是我们可以避免写很多重复的功能和代码. 如果从语义中去分析的话. 会简单很多. 如果语境中出现了x是⼀种y. 这时, y是⼀种泛化的概念. x比y更加具体. 那这时x就是y的⼦类. 比如. 猫是⼀种动物. 猫继承动物. 动物能动. 猫也能动. 这时猫在创建的时候就有了动物的"动"这个属性. 再比如, ⽩骨精是⼀个妖怪. 妖怪天⽣就有⼀个比较不好的功能叫"吃⼈", ⽩骨精⼀出⽣就知道如何"吃⼈". 此时 ⽩骨精继承妖精.

#### 6.3 多态

同⼀个对象, 多种形态. 这个在python中其实是很不容易说明⽩的. 因为我们⼀直在⽤. 只是没有具体的说. 比如. 我们创建⼀个变量a = 10 , 我们知道此时a是整数类型. 但是我们可以通过程序让a = `"alex"`, 这时, a⼜变成了字符串类型. 这是我们都知道的. 但是, 我要告诉你的是. 这个就是多态性. 同⼀个变量a可以是多种形态。

#####  6.3.1 鸭子类型

```
class Duck():
  def walk(self):
    print('I walk like a duck')
  def swim(self):
    print('i swim like a duck')

class Person():
  def walk(self):
    print('this one walk like a duck') 
  def swim(self):
    print('this man swim like a duck')

```

可以很明显的看出，Person类拥有跟Duck类一样的方法，当有一个函数调用Duck类，并利用到了两个方法walk()和swim()。我们传入Person类也一样可以运行，函数并不会检查对象的类型是不是Duck，只要他拥有walk()和swim()方法，就可以正确的被调用。 
再举例，如果一个对象实现了__getitem__方法，那python的解释器就会把它当做一个collection，就可以在这个对象上使用切片，获取子项等方法；如果一个对象实现了__iter__和next方法，python就会认为它是一个iterator，就可以在这个对象上通过循环来获取各个子项。

### 7 类的组成成员

#### 7.1细分类的组成成员

```python
class A:

    company_name = '嘻哈教育'  # 静态变量(静态字段)
    __iphone = '1353333xxxx'  # 私有静态变量(私有静态字段)


    def __init__(self,name,age): #特殊方法

        self.name = name  #对象属性(普通字段)
        self.__age = age  # 私有对象属性(私有普通字段)

    def func1(self):  # 普通方法
        pass

    def __func(self): #私有方法
        print(666)


    @classmethod  # 类方法
    def class_func(cls):
        """ 定义类方法，至少有一个cls参数 """
        print('类方法')

    @staticmethod  #静态方法
    def static_func():
        """ 定义静态方法 ，无默认参数"""
        print('静态方法')

    @property  # 属性
    def prop(self):
        pass
```

#### 7.2 类的私有成员

类成员

- 公有成员 在任何地方都能访问

- 私有成员 只有在类的类的内才能使用

  

静态字段

- 公有静态字段：类可以访问，类内部可以访问，派生类中可以访问

  ```python
  class C:
  
      name = "公有静态字段"
  
      def func(self):
          print C.name
  
  class D(C):
  
      def show(self):
          print C.name
  
  
  C.name         # 类访问
  
  obj = C()
  obj.func()     # 类内部可以访问
  
  obj_son = D()
  obj_son.show() # 派生类中可以访问
  
  公有静态字段
  ```

  

- 私有静态字段： 仅类内部可以昂文

  ```python
  class C:
  
      __name = "私有静态字段"
  
      def func(self):
          print C.__name
  
  class D(C):
  
      def show(self):
          print C.__name
  
  
  C.__name       # 不可在外部访问
  
  obj = C()
  obj.__name  # 不可在外部访问
  obj.func()     # 类内部可以访问   
  
  obj_son = D()
  obj_son.show() #不可在派生类中可以访问  
  
  私有静态字段
  ```

  

普通字段

- 公有普通字段：对象可以访问；类内部可以访问；派生类中可以访问

  ```python
  class C:
      
      def __init__(self):
          self.foo = "公有字段"
  
      def func(self):
          print self.foo 　#　类内部访问
  
  class D(C):
      
      def show(self):
          print self.foo　＃　派生类中访问
  
  obj = C()
  
  obj.foo     # 通过对象访问
  obj.func()  # 类内部访问
  
  obj_son = D();
  obj_son.show()  # 派生类中访问
  ```

  

- 私有普通字段：仅类内部可以访问；

  

```python
class C:
    
    def __init__(self):
        self.__foo = "私有字段"

    def func(self):
        print self.foo 　#　类内部访问

class D(C):
    
    def show(self):
        print self.foo　＃　派生类中访问

obj = C()

obj.__foo     # 通过对象访问    ==> 错误
obj.func()  # 类内部访问        ==> 正确

obj_son = D();
obj_son.show()  # 派生类中访问  ==> 错误

私有普通字段
```



方法：

- 公有方法:对象可以访问；类内部可以访问；派生类中可以访问

  ```python
  class C:
  
      def __init__(self):
          pass
      
      def add(self):
          print('in C')
  
  class D(C):
  
      def show(self):
          print('in D')
          
      def func(self):
          self.show()
  obj = D()
  obj.show()  # 通过对象访问   
  obj.func()  # 类内部访问    
  obj.add()  # 派生类中访问 
  ```

  

- 私有方法:仅类内部可以访问

  ```python
  class C:
  
      def __init__(self):
          pass
  
      def __add(self):
          print('in C')
  
  class D(C):
  
      def __show(self):
          print('in D')
  
      def func(self):
          self.__show()
  obj = D()
  obj.__show()  # 通过不能对象访问
  obj.func()  # 类内部可以访问
  obj.__add()  # 派生类中不能访问
  ```

  

**总结**

对于这些私有成员来说,他们只能在类的内部使用,不能再类的外部以及派生类中使用.

*ps：非要访问私有成员的话，可以通过 对象._类__属性名,但是绝对不允许!!!*

*为什么可以通过._类__私有成员名访问呢?因为类在创建时,如果遇到了私有成员(包括私有静态字段,私有普通字段,私有方法)它会将其保存在内存时自动在前面加上_类名.*

#### 7.3类的其他成员

这里的其他成员主要就是类方法：

方法包括：普通方法、静态方法和类方法，三种方法在**内存中都归属于类**，区别在于调用方式不同。

- **实例方法**

​    定义：第一个参数必须是实例对象，该参数名一般约定为“self”，通过它来传递实例的属性和方法（也可以传类的属性和方法）；

​    调用：只能由实例对象调用。

- **类方法**

​    定义：使用装饰器@classmethod。第一个参数必须是当前类对象，该参数名一般约定为“cls”，通过它来传递类的属性和方法（不能传实例的属性和方法）；

​    调用：实例对象和类对象都可以调用。

获得班级总人数

```python
class Student:
    
    __num = 0
    def __init__(self,name,age):
        self.name = name
        self.age= age
        Student.addNum() 
        
    @classmethod
    def addNum(cls):
        cls.__num += 1

    @classmethod
    def getNum(cls):
        return cls.__num
```



- **静态方法**

​    定义：使用装饰器@staticmethod。参数随意，没有“self”和“cls”参数，但是方法体中不能使用类或实例的任何属性和方法；

​    调用：实例对象和类对象都可以调用。

定义一个关于时间操作的类，其中有一个获取当前时间的函数

```python
import time

class TimeTest(object):
    def __init__(self, hour, minute, second):
        self.hour = hour
        self.minute = minute
        self.second = second

    @staticmethod
    def showTime():
        return time.strftime("%H:%M:%S", time.localtime())


print(TimeTest.showTime())
t = TimeTest(2, 10, 10)
nowTime = t.showTime()
print(nowTime)
```

#### 7.4 属性**property**

```python
class People:
    def __init__(self,name,weight,height):
        self.name=name
        self.weight=weight
        self.height=height
    @property
    def bmi(self):
        return self.weight / (self.height**2)

p1=People('egon',75,1.85)
print(p1.bmi)
```

**为什么要用property**

将一个类的函数定义成特性以后，对象再去使用的时候obj.name,根本无法察觉自己的name是执行了一个函数然后计算出来的，这种特性的使用方式**遵循了统一访问的原则**

由于新式类中具有三种访问方式，我们可以根据他们几个属性的访问特点，分别将三个方法定义为对同一个属性：获取、修改、删除

```PYTHON
class Foo:
    @property
    def AAA(self):
        print('get的时候运行我啊')

    @AAA.setter
    def AAA(self,value):
        print('set的时候运行我啊')

    @AAA.deleter
    def AAA(self):
        print('delete的时候运行我啊')

#只有在属性AAA定义property后才能定义AAA.setter,AAA.deleter
f1=Foo()
f1.AAA
f1.AAA='aaa'
del f1.AAA

或者：
class Foo:
    def get_AAA(self):
        print('get的时候运行我啊')

    def set_AAA(self,value):
        print('set的时候运行我啊')

    def delete_AAA(self):
        print('delete的时候运行我啊')
    AAA=property(get_AAA,set_AAA,delete_AAA) #内置property三个参数与get,set,delete一一对应

f1=Foo()
f1.AAA
f1.AAA='aaa'
del f1.AAA
```

商品实例

```python
class Goods(object):

    def __init__(self):
        # 原价
        self.original_price = 100
        # 折扣
        self.discount = 0.8

    @property
    def price(self):
        # 实际价格 = 原价 * 折扣
        new_price = self.original_price * self.discount
        return new_price

    @price.setter
    def price(self, value):
        self.original_price = value

    @price.deltter
    def price(self, value):
        del self.original_price

obj = Goods()
obj.price         # 获取商品价格
obj.price = 200   # 修改商品原价
del obj.price     # 删除商品原价
```

#### 7.5 `isinstace` 与` issubclass`

`isinstance(a,b)`：判断a是否是b类（或者b类的派生类）实例化的对象

```python
class A:
    pass

class B(A):
    pass

obj = B()


print(isinstance(obj,B))
print(isinstance(obj,A))
```

`issubclass(a,b)`： 判断a类是否是b类（或者b的派生类）的派生类

```python
class A:
    pass

class B(A):
    pass

class C(B):
    pass

print(issubclass(B,A))
print(issubclass(C,A))
```

 list `str` tuple `dict`等这些类与` Iterble`类 的关系是什么？

```python
from collections import Iterable

print(isinstance([1,2,3], list))  # True
print(isinstance([1,2,3], Iterable))  # True
print(issubclass(list,Iterable))  # True

# 由上面的例子可得，这些可迭代的数据类型，list str tuple dict等 都是 Iterable的子类
```

#### 7.6元类 type

```
print(type('abc'))
print(type(True))
print(type(100))
print(type([1, 2, 3]))
print(type({'name': '太白金星'}))
print(type((1,2,3)))
print(type(object))

class A:
    pass

print(isinstance(object,type))
print(isinstance(A, type)
```

type元类是获取该对象从属于的类,而type类比较特殊，Python原则是：一切皆对象，其实类也可以理解为'对象',而type元类又称作构建类，python中大多数内置的类（包括object）以及自己定义的类，都是由type元类创造的。

\* 而type类与object类之间的关系比较独特：object是type类的实例，而type类是object类的子类，这种关系比较神奇无法使用python的代码表述，因为定义其中一个之前另一个必须存在。所以这个只作为了解。

### 8 面向对象 反射 双下划线

#### 8.1 反射

python面向对象中的反射：通过字符串的形式操作对象相关的属性。python中的一切事物都是对象（都可以使用反射）

四个可以实现自省的函数

```python
class Foo:
    f = '类的静态变量'
    def __init__(self,name,age):
        self.name=name
        self.age=age

    def say_hi(self):
        print('hi,%s'%self.name)

obj=Foo('egon',73)

#检测是否含有某属性
print(hasattr(obj,'name'))
print(hasattr(obj,'say_hi'))

#获取属性
n=getattr(obj,'name')
print(n)
func=getattr(obj,'say_hi')
func()

print(getattr(obj,'aaaaaaaa','不存在啊')) #报错

#设置属性
setattr(obj,'sb',True)
setattr(obj,'show_name',lambda self:self.name+'sb')
print(obj.__dict__)
print(obj.show_name(obj))

#删除属性
delattr(obj,'age')
delattr(obj,'show_name')
delattr(obj,'show_name111')#不存在,则报错

print(obj.__dict__)

```

当前模块的反射

```python
import sys
def s1():
    print 's1'
def s2():
    print 's2'
this_module = sys.modules[__name__]

hasattr(this_module, 's1')
getattr(this_module, 's2')
```

其他模块的反射

```python
#一个模块中的代码
def test():
    print('from the test')
"""
程序目录：
    module_test.py
    index.py 
当前文件：
    index.py
"""
# 另一个模块中的代码
import module_test as obj
#obj.test()
print(hasattr(obj,'test'))
getattr(obj,'test')()
```

反射的登录

```python
class User:
    def login(self):
        print('欢迎来到登录页面')    
    def register(self):
        print('欢迎来到注册页面')    
    def save(self):
        print('欢迎来到存储页面')
user = User()
while 1:
    choose = input('>>>').strip()
    if hasattr(user,choose):
        func = getattr(user,choose)
        func()
    else:
        print('输入错误。。。。')
```

#### 8.2 函数 vs 方法

###### 8.2.1验证函数和方法

- 通过打印函数（方法）

  ```python
  def func():
      pass
  print(func)  # <function func at 0x00000260A2E690D0>
  class A:
      def func(self):
          pass    
  print(A.func)  # <function A.func at 0x0000026E65AE9C80>
  obj = A()
  print(obj.func)  # <bound method A.func of <__main__.A object at 0x00000230BAD4C9E8>>
  ```

- #### 通过types模块验证

  ```python
  from types import FunctionType
  from types import MethodType
  
  def func():
      pass
  class A:
      def func(self):
          pass
  obj = A()
  print(isinstance(func,FunctionType))  # True
  print(isinstance(A.func,FunctionType))  # True
  print(isinstance(obj.func,FunctionType))  # False
  print(isinstance(obj.func,MethodType))  # True
  ```

  

静态方法是函数

```python
from types import FunctionType
from types import MethodType

class A:    
    def func(self):
        pass    
    @classmethod
    def func1(self):
        pass    
    @staticmethod
    def func2(self):
        pass
obj = A()
# 静态方法其实是函数
# print(isinstance(A.func2,FunctionType))  # True
# print(isinstance(obj.func2,FunctionType))  # True
```

**函数与方法的区别**

那么，函数和方法除了上述的不同之处，还总结了一下几点区别。

（1）函数的是显式传递数据的。如我们要指明为len()函数传递一些要处理数据。

（2）函数则跟对象无关。

（3）方法中的数据则是隐式传递的。

（4）方法可以操作类内部的数据。

（5）方法跟对象是关联的。如我们在用strip()方法是，是不是都是要通过str对象调用，比如我们有字符串s,然后s.strip()这样调用。是的，strip()方法属于str对象。

我们或许在日常中会口语化称呼函数和方法时不严谨，但是我们心中要知道二者之间的区别。

在其他语言中，如Java中只有方法，C中只有函数，C++么，则取决于是否在类中。

#### 8.3 双下方法

- `__len__`

  ```python
   # len 一个对象就会触发 __len__方法。
  class A:
      def __init__(self):
          self.a = 1
          self.b = 2
      def __len__(self):
          return len(self.__dict__)
  a = A()
  print(len(a))
  ```

  

- `__hash__`

  hash一个对象的时候会触发

  ```
  class A:
      def __init__(self):
          self.a = 1
          self.b = 2
  
      def __hash__(self):
          return hash(str(self.a)+str(self.b))
  a = A()
  print(hash(a))
  ```

- `__str__`

  如果一个类中定义了`__str__`方法，那么在打印 对象 时，默认输出该方法的返回值

  ```
  class A:
      def __init__(self):
          pass
      def __str__(self):
          return '太白'
  a = A()
  print(a)
  print('%s' % a)
  ```

- `__repr__`

  如果一个类中定义了`__str__`方法，那么在打印 对象 时，默认输出该方法的返回值

  ```python
  class A:
      def __init__(self):
          pass
      def __repr__(self):
          return '太白'
  a = A()
  print(repr(a))
  print('%r'%a)
  ```

- `__call__`

  对象后面加括号，触发执行。

  注：构造方法`__new__`的执行是由创建对象触发的，即：对象 = 类名() ；而对于 __call__ 方法的执行是由对象后加括号触发的，即：对象() 或者 类()()

  ```python
  class Foo:
  
      def __init__(self):
          pass    
      def __call__(self, *args, **kwargs):
          print('__call__')
  obj = Foo() # 执行 __init__
  obj()       # 执行 __call__
  ```

- `__eq__`

  判断相等？

  ```
  class A:
      def __init__(self):
          self.a = 1
          self.b = 2
  
      def __eq__(self,obj):
          if  self.a == obj.a and self.b == obj.b:
              return True
  a = A()
  b = A()
  print(a == b)
  ```

- ` __del__`

  析构方法，当对象在内存中被释放时，自动触发执行。

  注：此方法一般无须定义，因为Python是一门高级语言，程序员在使用时无需关心内存的分配和释放，因为此工作都是交给Python解释器来执行，所以，析构函数的调用是由解释器在进行垃圾回收时自动触发执行的

  可以实现资源的关闭

- `__new__`

  创建对象空间

  ```
  
  class A:
      def __init__(self):
          self.x = 1
          print('in init function')
      def __new__(cls, *args, **kwargs):
          print('in new function')
          return object.__new__(A, *args, **kwargs)
  
  a = A()
  print(a.x)
  ```

  单例模式

  ```
  class A:
      __instance = None
      def __new__(cls, *args, **kwargs):
          if cls.__instance is None:
              obj = object.__new__(cls)
              cls.__instance = obj
          return cls.__instance
  ```

  单例解析：

  ```
  单例模式是一种常用的软件设计模式。在它的核心结构中只包含一个被称为单例类的特殊类。通过单例模式可以保证系统中一个类只有一个实例而且该实例易于外界访问，从而方便对实例个数的控制并节约系统资源。如果希望在系统中某个类的对象只能存在一个，单例模式是最好的解决方案。
  【采用单例模式动机、原因】
  对于系统中的某些类来说，只有一个实例很重要，例如，一个系统中可以存在多个打印任务，但是只能有一个正在工作的任务；一个系统只能有一个窗口管理器或文件系统；一个系统只能有一个计时工具或ID(序号)生成器。如在Windows中就只能打开一个任务管理器。如果不使用机制对窗口对象进行唯一化，将弹出多个窗口，如果这些窗口显示的内容完全一致，则是重复对象，浪费内存资源；如果这些窗口显示的内容不一致，则意味着在某一瞬间系统有多个状态，与实际不符，也会给用户带来误解，不知道哪一个才是真实的状态。因此有时确保系统中某个对象的唯一性即一个类只能有一个实例非常重要。
  如何保证一个类只有一个实例并且这个实例易于被访问呢？定义一个全局变量可以确保对象随时都可以被访问，但不能防止我们实例化多个对象。一个更好的解决办法是让类自身负责保存它的唯一实例。这个类可以保证没有其他实例被创建，并且它可以提供一个访问该实例的方法。这就是单例模式的模式动机。
  【单例模式优缺点】
  【优点】
  一、实例控制
  单例模式会阻止其他对象实例化其自己的单例对象的副本，从而确保所有对象都访问唯一实例。
  二、灵活性
  因为类控制了实例化过程，所以类可以灵活更改实例化过程。
  【缺点】
  一、开销
  虽然数量很少，但如果每次对象请求引用时都要检查是否存在类的实例，将仍然需要一些开销。可以通过使用静态初始化解决此问题。
  二、可能的开发混淆
  使用单例对象（尤其在类库中定义的对象）时，开发人员必须记住自己不能使用new关键字实例化对象。因为可能无法访问库源代码，因此应用程序开发人员可能会意外发现自己无法直接实例化此类。
  三、对象生存期
  不能解决删除单个对象的问题。在提供内存管理的语言中（例如基于.NET Framework的语言），只有单例类能够导致实例被取消分配，因为它包含对该实例的私有引用。在某些语言中（如 C++），其他类可以删除对象实例，但这样会导致单例类中出现悬浮引用
  ```

- #### `__item__`

  ```
  class Foo:
      def __init__(self,name):
          self.name=name
  
      def __getitem__(self, item):
          print(self.__dict__[item])
      def __setitem__(self, key, value):
          self.__dict__[key]=value  # 可以索引取值
      def __delitem__(self, key):
          print('del obj[key]时,我执行')
          self.__dict__.pop(key)
      def __delattr__(self, item):
          print('del obj.key时,我执行')
          self.__dict__.pop(item)
  
  f1=Foo('sb')
  f1['age']=18
  f1['age1']=19
  del f1.age1
  del f1['age']
  f1['name']='alex'
  print(f1.__dict__)
  ```

- #### 上下文管理器相关

  `__enter__  __exit__`

  ```
  class A:
      
      def __init__(self, text):
          self.text = text
      
      def __enter__(self):  # 开启上下文管理器对象时触发此方法
          self.text = self.text + '您来啦'
          return self  # 将实例化的对象返回f1
      
      def __exit__(self, exc_type, exc_val, exc_tb):  # 执行完上下文管理器对象f1时触发此方法
          self.text = self.text + '这就走啦'
          
  with A('大爷') as f1:
      print(f1.text)
  print(f1.text)
  ```

  自定义文件管理器

  ```
  class Diycontextor:
      def __init__(self,name,mode):
          self.name = name
          self.mode = mode
   
      def __enter__(self):
          print "Hi enter here!!"
          self.filehander = open(self.name,self.mode)
          return self.filehander
   
      def __exit__(self,*para):
          print "Hi exit here"
          self.filehander.close()
   
   
  with Diycontextor('py_ana.py','r') as f:
      for i in f:
          print i
  ```

  

### 9 单例模式

第一种方式

```python
class A:
    __flag = None
    def __new__(cls, *args, **kwargs):
        if cls.__flag is None:
            cls.__flag = object.__new__(cls)
        return cls.__flag

    def __init__(self,name=None,age=None):
        self.name = name
        if age:
            self.age = age
```

第二种方式，利用导入模块的方式

**mysingleton.py**文件

```python
class Singleton(object):
    def foo(self):
        pass
singleton = Singleton()

```

将上面的代码保存在文件 `mysingleton.py` 中，要使用时，直接在其他文件中导入此文件中的对象，这个对象即是单例模式的对象

```python
from mysingleton import singleton
```

第三种方式：

```python
def Singleton(cls):
    _instance = {}

    def _singleton(*args, **kargs):
        if cls not in _instance:
            _instance[cls] = cls(*args, **kargs)
        return _instance[cls]

    return _singleton
@Singleton
class A(object):
    a = 1

    def __init__(self, x=0):
        self.x = x
a1 = A(2)
a2 = A(3)
```

第四种方式

```python
class Singleton(object):

    def __init__(self):
        pass
# 静态类方法
    @classmethod
    def instance(cls, *args, **kwargs):
        # 判断是否可以反射
        if not hasattr(Singleton, "_instance"):
            Singleton._instance = Singleton(*args, **kwargs)
        return Singleton._instance
```

