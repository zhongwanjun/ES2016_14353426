# DOL配置过程
## DOL框架描述

DOL是分布式操作层（distributed operation layer）的简称。DOL结构允许从应用层到多处理器SHAPES结构平台的自动映射。同时，DOL包含了以下三个主要部分：

* DOL API：DOL定义了一系列允许SHAPES 平台上的分布且平行的应用编程的计算以及交互程序。
* DOL 功能性仿真：为了让程序员可以更好的测试他们的程序，DOL建立了仿真功能。除了应用的功能性验证，这个结构可以帮助衡量应用层的表现。
* DOL 映射优化： DOL映射优化的功能是可以计算一系列从应用层到SHAPES 结构平台的映射的优化映射。

## DOL配置过程
### 先配置环境：在VMWARE中安装UBUNTU虚拟机

![Alt text](http://i1.piimg.com/567571/a3c66dd0e1fa62a1.png)

### 在UBUNTU下配置必要的环境
step1:`sudo apt-get update`

![Alt text](http://i1.piimg.com/567571/7ceed6ad027487b1.png)

 step2:` sudo apt-get install ant`
 
 step3:`sudo apt-get install openjdk-7-jdk`
 
 ![Alt text](http://i1.piimg.com/567571/56b546c5917f0e24.png)
 
 step4:`sudo apt-get install unzip`
 
 ![Alt text](http://i1.piimg.com/567571/3537fe1ca3ef8087.png)

### 下载文件

`sudo wget <http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz/>`

`sudo wget <http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip/>`

(因为之前已经成功下载并解压安装，这两步无法给出图片，请谅解)

###解压文件

* 新建dol文件夹

  `mkdir dol`
  
* 将dolethz.zip解压到dol文件夹中

`unzip dol_ethz.zip -d dol`

* 解压systemc

`tar -zxvf systemc-2.3.1.tgz`
 
### 编译systemc

* 解压后进入systemc-2.3.1目录

`cd systemc-2.3.1`

* 新建一个临时文件夹objdir

`cd objdir`

* 编译运行configure 

`../congigure CXX=g++ --disable-async-updates`

![Alt text](http://i1.piimg.com/567571/147964d9771d918d.png)

* 编译systemc

`sudo make install`

`cd`

`ls`

![Alt text](http://i1.piimg.com/567571/d0e87c84fd457992.png)

工作路径为`/home/guanzhuoqun/systemc-2.3.1`

* 编译DOL

![Alt text](http://i1.piimg.com/567571/d2e46451a78fa4e7.png)

修改build_zip.xml文件

`property name="systemc.inc" value="/home/guanzhuoqun/systemc-2.3.1/include"`

`property name="systemc.lib" value="/home/guanzhuoqun/systemc-2.3.1/lib-linux64/libsystemc.a"`

* 编译DOL 

` ant -f build_zip.xml all`

![Alt text](http://i1.piimg.com/567571/37c582f783776a8a.png)

* 运行build/bin/main 路径下的第一个例子

`ant -f runexample.xml -Dnumber=1`

![Alt text](http://i1.piimg.com/567571/4af5509bd8c81b20.png)

## 实验收获与感想
* 比较笼统的知道了LINUX下命令行的一些基本操作指令以及DOL的基本安装过程，成功配置了DOL的基本编译环境。
* 在配置过程中很容易出现权限低不被允许的情况，这时候要在命令前面加入sudo ，代表以管理员权限运行
* 看了挺多关于Markdown的文本，markdown的确是非常一种有趣的语言，非常适合于自动排版以及PPT的制作
* 建立了自己的gitub仓库，并发现github仓库可以用于非常非常多的地方，非常开心学习到这个平台的使用方法。



 
 



