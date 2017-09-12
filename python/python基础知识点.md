* 以一个下划线开头的命名 ，如_getFile
    * 单下划线开头，这个被常用于模块中，在一个模块中以单下划线开头的变量和函数被默认当作内部函数，如果使用 from a_module import * 导入时，这部分变量和函数不会被导入。不过值得注意的是，如果使用 import a_module 这样导入模块，仍然可以用 a_module._some_var 这样的形式访问到这样的对象
* 以一个下划线结尾的命名，如class_
    * Python 的官方推荐的代码样式中，还有一种单下划线结尾的样式，这在解析时并没有特别的含义，但通常用于和 Python 关键词区分开来，比如如果我们需要一个变量叫做 class，但 class 是 Python 的关键词，就可以以单下划线结尾写作 class_。
* 以两个下划线开头的命名 ，如__filename
    * 双下划线开头的命名形式在 Python 的类成员中使用表示名字改编 (Name Mangling)，即如果有一 Test 类里有一成员 __x，那么 dir(Test) 时会看到 _Test__x 而非 __x。这是为了避免该成员的名称与子类中的名称冲突。但要注意这要求该名称末尾没有下划线。
* 以两个下划线开头和结尾的命名，如 __init__()
    * 双下划线开头双下划线结尾的是一些 Python 的“魔术”对象，如类成员的 __init__、__del__、__add__、__getitem__ 等，以及全局的 __file__、__name__ 等。 Python 官方推荐永远不要将这样的命名方式应用于自己的变量或函数，而是按照文档说明来使用。
***
* python中删除元素的方法：
li = [1,2,3,4,5,6]

    * # 1.使用del删除对应下标的元素
                         del li[2]
                          # li = [1,2,4,5,6]
    * # 2.使用.pop()删除最后一个元素
                         li.pop()
                         # li = [1,2,4,5]
    * # 3.删除指定值的元素
                       li.remove(4)
                       # li = [1,2,5]
    * # 4.使用切片来删除
                       li = li[:-1]
                       # li = [1,2]
                       # !!!切忌使用这个方法，如果li被作为参数传入函数，
                       # 那么在函数内使用这种删除方法，将不会改变原list
***
* 负数没有回文数
***
* 字符串取反：
           ss = “abxdks”
           ss = ss[::-1]
***
* *args的用法：函数参数列表
          **kwargs的用法：函数参数字典
***
* 生成器
    * 可迭代对象：能提供迭代器的任意对象
    * 迭代器：任意对象，只要定义了next方法
    * 迭代：从某个对象中取出元素的过程
    * 生成器：也是一种迭代器，但是只能对其迭代一次。这是因为它们并没有把所有的值存在于内存中，而是在运行时生成值。通过遍历来使用，使用yield生出一个值
      例子如下：
      ```
      def generator_function():
          for i in range(10):
              yield i
      for item in generator_function():
          print(item)
      ```
***
* Python内置函数next()
```
def generator_function():
    for i in range(3):
        yield i
gen = generator_function()
print(next(gen))
# Output: 0
print(next(gen))
# Output: 1
print(next(gen))
# Output: 2
print(next(gen))
# Output: Traceback (most recent call last):
#            File "<stdin>", line 1, in <module>
#         StopIteration
```
***
* lambda
    * 也被称为匿名函数
    * 他和不同函数的效果是一样的
    * 格式：lambda  参数：操作（参数）
    * map、lambda用法：Map会将一个函数映射到一个输入列表的所有元素上，规范map(function_to_apply, list_of_inputs)，大多数时候，我们要把列表中所有元素一个一个地传递给一个函数，并收集结果。不仅用于一列表的输入，我们甚至可以用于一列表的函数
    * Filter，lambda用法：filter过滤列表中的元素，并且返回一个由所有符合要求的元素所构成的列表，符合要求即函数映射到该元素时返回值为true。
    * Reduce，lambda用法：当需要对一个列表进行一些计算并返回结果时，reduce是一个非常有用的函数。
    * map（）的第二个参数为迭代器，使用yield的生成器也是可以的。
***
* set数据集合
    * -符号是得出差集
    * &符号得出交集
    * |符号得出并集
***
* 三元运算符：
    * condition_is_true   if   condition   else   condition_is_false
***
* 装饰器
    * 一切皆对象
    * 我们可以将一个函数赋值给一个变量
    * 我们可以在一个函数中定义另外一个函数，即可以创建嵌套函数，嵌套函数不能在函数外使用。
    * 可以从函数中返回函数
    * 可以将函数作为参数传给另一个函数
    * 函数对象有一个__name__属性，可以拿到函数的名字。
    * 高阶函数：编写高阶函数就是让函数的参数能够接收别的函数。即把函数作为参数传入，这样的函数称为高阶函数
***
* 虚拟环境：virtualenv
    * 能够帮我们创建一个独立（隔离）的python开发环境
    * 创建：virtualenv  myproject
    * 激活：source  bin/activate
    * 退出：deactivate
***
* 容器（collections）:
    * python附带的模块collections。
    * 例如，defaultdict，这个容器于dict不同，不需要检查key。from  collections  import  defaultdict
    * 例如，counter是一个计数器，它可以帮助我们针对某项数据进行统计。from  collections  import  counter
    * 例如，deque提供一个双端队列，可以从头\尾两端添加和删除元素。from  collections  import  deque
    * 例如，namedtuple命名元组，特性是可以像字典一样访问命名元组namedtuple
***
* 推导式：python的一种独有特性。
    * 列表（list）推导式：它的结构是一个中括号里包含一个表达式，然后是一个for循环，然后是0或者多个for或者if语句
    * 字典（dict）推导式：字典推导式和列表推导式的使用方法是类似的。字典推导式使用{ }
    * 集合（set）推导式：集合推导式和列表推导式的使用方法也是类似的。唯一的区别就是集合推导式使用{ }
***
* 异常：
    * 异常处理是一种艺术，一旦掌握，将被授予无穷的力量。
    * try/except语句：except可以同时处理多种异常
    * raise：忽略异常
    * else语句：在try内没有异常的情况下，执行该语句内的代码。
    * finally语句：不管try中的异常是否触发，都会执行该语句，该语句可以被用来用代码执行之后的清理工作。
***
* 上下文管理器：
    * 典型的，with语句
***
* open函数：
    * with  open(***,***)  as  f:
                         d = f.read()
    * open第一个参数是文件名，第二个参数是打开模式：r、r+、w、a
***
* 对象自省：
    * 是指在运行时来判断一个对象的类型的能力。
    * dir函数，返回一个列表，列出一个对象所拥有的属性和方法。
    * type函数，返回一个对象的类型。
    * id函数，返回任意不同种类对象的唯一ID
    * inspect模块，提供了很多有用的函数，来获取活跃对象的信息。
***
* for—else：
    * capitalize()方法，将字符串的第一个字母变成大写,其他字母变小写。
    * 当for循环是以正常方式退出for循环的（即不是以break、return、异常技术循环的），都会执行else语句内的代码。
***
* 使用C扩展：
    * CPython可以使python轻松调用C语言代码。
***
* global关键字&return关键字
    * 在实际编程中应尽量避免使用global关键字
    * return可以返回多个值
***
* 可变对象&不可变对象
    * 每当一个变量赋值给另外一个可变类型的变量时，对这个数据的任意改变会同时反应到两个变量上，新变量只是老变量的一个别名而已。这种情况只是针对可变数据类型。
    * 应该永远不要定义可变数据类型的默认参数（像这样这个函数中def add_to(num, target=[ ]):……的target参数），除非你自己知道在做什么。
***
* __slots__魔法：
    * 针对类中的对象属性：优化对象属性占用的内存
***
* 枚举：
    * 枚举是python的内置函数，允许我们遍历数据并自动计数。
***
* 知识点：
    1. //运算符：用于 floor division 而无论操作数是什么类型，例如，17//4结果是4，17//4.0结果是4.0
    2.  ** 运算符：进行幂运算，例如，5 ** 2结果是25
    3. 循环可以有一个 else 子句；它在循环迭代完整个列表 (对于 for) 后或执行条件为 false (对于 while) 时执行，但循环被 break 中止的情况下不会执行。
    4. 在函数调用中，关键字的参数必须跟随在位置参数的后面。*name 必须在 **name 之前出现。
    5. zip（）函数
    6. set（）集合，可用于对象元素的合并、交、差等数学运算。
    7. enumerate()是python的内置函数，可以同时遍历索引和遍历元素。例如列表的下标及对应的值。
    8. 遍历字典时，使用 iteritems() 方法可以同时得到键和对应的值。
    9. xrange 用法与 range 完全相同，所不同的是生成的不是一个list对象，而是一个生成器。
    10. 要生成很大的数字序列的时候，用xrange会比range性能优很多，因为不需要一上来就开辟一块很大的内存空间。
    11. json格式数据的应用，python中dict转换为json，使用json模块，import json，然后使用json中的dumps方法，json.dumps()。json.loads方法是将json格式转换为python数据格式。
    12.  python 列表list中内置了一个十分有用的排序函数sort,sorted。sorted()从小到大排序,不影响列表本身结构。sort()从小到大排序,影响列表本身结构。如果要从大到小排序，可以使用sorted(list,reverse=True)或者list.sort()
***
* CPU密集型    VS    IO密集型
    * CPU密集型代码：因为单个线程需要大量的运算，多线程之间的切换需要消耗资源，所以，如果是CPU密集型的代码不建议使用多线程，可以使用多进程。
    * IO密集型代码：（例如文件处理，网络爬虫），单线程下有IO操作会进行IO等待，造成不必要的时间浪费，而开启多线程等在线程A等待时，自动切换到线程B，可以不浪费CPU的资源，从而能提升程序执行效率。
    * python中的多线程并不是并行执行，而是交替执行。
    * GIL的全称是Global Interpreter Lock(全局解释器锁)，来源是python设计之初的考虑，为了数据安全所做的决定。
    * 在Python多线程下，每个线程的执行方式：
        1. 获取GIL
        2. 执行代码直到sleep或者是python虚拟机将其挂起。
        3. 释放GIL
    * 可见，某个线程想要执行，必须先拿到GIL，我们可以把GIL看作是“通行证”，并且在一个python进程中，GIL只有一个。拿不到通行证的线程，就不允许进入CPU执行。

***
* 同步、异步###阻塞、非阻塞
    * 同步、异步：同步和异步关注的是消息通信机制。所谓同步，就是在发出一个*调用*时，在没有得到结果之前，该*调用*就不返回。但是一旦调用返回，就得到返回值了。换句话说，就是由*调用者*主动等待这个*调用*的结果。而异步则是相反，*调用*在发出之后，这个调用就直接返回了，所以没有返回结果。换句话说，当一个异步过程调用发出后，调用者不会立刻得到结果。而是在*调用*发出后，*被调用者*通过状态、通知来通知调用者，或通过回调函数处理这个调用。
    * 阻塞、非阻塞：阻塞和非阻塞关注的是程序在等待调用结果（消息，返回值）时的状态。阻塞调用是指调用结果返回之前，当前线程会被挂起。调用线程只有在得到结果之后才会返回。非阻塞调用指在不能立刻得到结果之前，该调用不会阻塞当前线程。

***
* 多进程:
    * multiprocessing模块：from  multiprocessing  import  Process：Process类代表一个进程对象。例子如下：
```
from multiprocessing import Process
import os

 子进程要执行的代码
def run_proc(name):
    print 'Run child process %s (%s)...' % (name, os.getpid())

if __name__=='__main__':
    print 'Parent process %s.' % os.getpid()
    p = Process(target=run_proc, args=('test',))
    print 'Process will start.'
    p.start()
    p.join()
    print 'Process end.’
```
    * multiprocessing模块：from  multiprocessing  import  Pool：Pool类代表线程池。例子如下：
```
from multiprocessing import Pool
import os, time, random

def long_time_task(name):
    print 'Run task %s (%s)...' % (name, os.getpid())
    start = time.time()
    time.sleep(random.random() * 3)
    end = time.time()
    print 'Task %s runs %0.2f seconds.' % (name, (end - start))

if __name__=='__main__':
    print 'Parent process %s.' % os.getpid()
    p = Pool()
    for i in range(5):
        p.apply_async(long_time_task, args=(i,))
    print 'Waiting for all subprocesses done...'
    p.close()
    p.join()
    print 'All subprocesses done.’
```
    * Pool类包含的函数：
    1. apply_async()：非阻塞且支持结果返回进行回调。
    2. map()：内置的map函数用法行为基本一致，它会使进程阻塞直到返回结果。
    3. close()：关闭进程池（pool），使其不在接受新的任务。
    4. terminate()：结束工作进程，不在处理未处理的任务。
    5. join()：主进程阻塞等待子进程的退出，join方法必须在close或terminate之后使用。

    * Pool对象调用join（）方法会等待所有子进程执行完毕，调用join（）之前必须调用close（），调用close（）之后就不能继续添加新的Process了。
    * Pool的默认大小是宿主机上CPU的核数。
    * 进程间通信：multiprocessing模块提供了Queue、Pipes等多种方式进行交换数据。

* 多线程：可参考（http://codingpy.com/article/python-201-a-tutorial-on-threads/）
    * threading模块
    * 启动一个线程就是把一个函数传入并创建Thread实例，然后调用start（）开始执行。例子如下：
import time, threading
# 新线程执行的代码:
```
def loop():
    print 'thread %s is running...' % threading.current_thread().name
    n = 0
    while n < 5:
        n = n + 1
        print 'thread %s >>> %s' % (threading.current_thread().name, n)
        time.sleep(1)
    print 'thread %s ended.' % threading.current_thread().name

print 'thread %s is running...' % threading.current_thread().name
t = threading.Thread(target=loop, name='LoopThread')
t.start()
t.join()
print 'thread %s ended.' % threading.current_thread().name
```
    * python的threading模块有个current_thread（）函数，它永远返回当前线程的实例。主线程实例的名字叫MainThread，子线程的名字在创建时指定。
    * threading.Lock（）创建一把锁，例子如下：
balance = 0
lock = threading.Lock()

def run_thread(n):
    for i in range(100000):
        # 先要获取锁:
        lock.acquire()
        try:
            # 放心地改吧:
            change_it(n)
        finally:
            # 改完了一定要释放锁:
            lock.release()
    * 当多个线程同时执行lock.acquie（）时，只有一个线程能成功获取锁，然后继续执行代码，其他线程就继续等待直到获取锁为止。获取锁的线程用完之后一定要释放锁，否则其他线程只能永远的等待下去，成为死线程。使用try......finally来确保锁一定会被释放。

* eval() 函数用来执行一个字符串表达式，并返回表达式的值。
* os.path.dirname(__file__)返回脚本的路径，在Django中BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))得到的是项目的路径。
* 调试Debugging
Import pdb
pdb.set_trace()
命令列表：
n：代表执行下一步
p：代表打印，举个栗子：p name ：代表打印变量name
s：执行当前代码行，即进入函数或者类内部
b：动态添加断点，举个栗子：b 18 ：代表在18行添加断点
l：罗列出所有设置的断点
q：结束退出
