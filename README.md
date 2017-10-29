# Programming in Scala第三版学习笔记, 示例代码中文命名

前言: 由于已有中文版, 这个笔记并不拘泥于翻译原文, 而是选摘和提炼出个人认为的重点, 并顺便将所有示例改成中文命名(同样不拘泥于原本的词意, 而是融入中文特色), 希望为后人学习降低一点门槛.
本文代码在Scala 2.12.4, Java 1.8.0_45下测试通过.

### 第一章 普适的语言

Scala这个名字来源于"scalable语言", 当初的设想是能够用在小到脚本大到系统. Scala在标准Java平台上运行, 可以和Java库无缝集成. 技术上说, 它是一个包含了面向对象和函数式编程概念的静态类型语言, 设计的希望是取众家之长.

这章是简介Scala特性以及它能做什么, 但并不是真正的入门(啥??). 如果希望马上写Scala程序, 还是从第二章开始吧.

#### 1.1 

```
var 首都 = Map("中国" -> "北京", "俄罗斯" -> "莫斯科")
首都 += ("德国" -> "柏林")
println(首都("俄罗斯"))
```
(待续. 先从第二章开始)

### 第二章 蹒跚学步

此章将从0开始介绍Scala,为后两章打基础. 看完之后应该能用Scala写实用程序了(好的,那么这个笔记的第一个小目标就是看完前四章)

#### 第一步 
安装了Scala之后,在命令行(控制台)中输入`scala`之后, 就启动了解释器运行环境(理解输入的代码,运行并显示结果):
```
$ scala
Welcome to Scala 2.12.4 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_45).
Type in expressions for evaluation. Or try :help.

scala>
```
试试最简单的加法:
```
scala> 1 + 2
```
解释器打印:
```
res0: Int = 3
```
意思是: res0(自动生成的名称, 就是result 0的简写)是个整数(Int),值为(=)3. 它可以在之后被引用, 比如:
```
scala> res0 * 3
res1: Int = 9
```
不免俗地问个好吧:
```
  scala> println("吃了么?")
  吃了么?
```
println把字符串输出到标准输出(显示屏), 类似Java的System.out.println

#### 第二步 定义变量

有两种, val在定义后就不能被重新赋值, 类似Java中的final. var就可以随便赋值. 例如:
```
scala> val 问话 = "吃了么?"
问话: String = 吃了么?
```
如果习惯了Java中定义变量的方式, 也许会惊讶于为何不用显式声明`String`, 这是因为Scala在这里能自行推导出`问话`是`String`类型. 当然它的推导是很机械的, 有时也不能猜到你想要的类型. 因此也有显式定义类型的方法, 只是格式和Java有点区别:
```
scala> val 又问话: String = "吃了好"
又问话: String = 吃了好
```
定义了`问话`之后,就可以用了:
```
scala> println(问话)
吃了么?
```
问话因为是val,它就不能被重新赋值. 即使赋的是完全相同的值, 解释器也会报错:
```
scala> 问话 = "吃了么?"
<console>:12: error: reassignment to val
       问话 = "吃了么?"
```
如果重新赋值是必要的, 那么就用var, 比如:
```
scala> var 问好 = "早啊"
问好: String = 早啊
```
如果快到吃饭的时候了,问好就可以改成:
```
scala> var 问好 = "吃了么?"
问好: String = 吃了么?
```
如果输入的是多行, 只要换行后继续输入即可. 解释器会自动在接续的行前加`|`:
```
scala> var 多行 =
     | "这是又一行"
多行: String = 这是又一行
```
如果输错了, 而解释器还在等待新输入, 只要换两次行, 解释器就会重新等待新输入:
```
scala> var 放空中 =
     | 
     | 
You typed two blank lines.  Starting a new command.

scala> 
```
在以后的示例中, 将把这些`|`省略,以便阅读, 以及拷贝黏贴到解释器自行运行.

第三步. 定义函数

用过了变量, 不妨来写点函数(这不是最简单的函数):
```
scala> def 最大值(x: Int, y: Int): Int = {
        if (x > y) x
        else y
      }
最大值: (x: Int, y: Int)Int
```
def表示后面的是函数定义, `最大值`是函数名称, `()`内的是函数参数, `: Int`正如之前的变量定义类似, 是表示函数的返回值类型. `{}`包括的是函数体.

和变量定义类似, 有时可以让推导返回值, 就不用声明返回值类型. 如果函数体只有一条声明, 就可以作如下省略:
(待续)
