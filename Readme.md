#Readme
---
#####Install DOL in Ubuntu 14.04 in lab1 
## Description（DOL 框架描述）
　　Distributed Operation Layer (分布式操作层): The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.
![](http://upload-images.jianshu.io/upload_images/3239746-f6fe972bb386b599.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
##How to install(DOL安装笔记)
**1.安装一些必要的环境**：
<p>`$    sudo apt-get update `
<p>![](http://upload-images.jianshu.io/upload_images/3239746-df7b9764480e46fe.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/3239746-7e7a6b1641f351df.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>`$    sudo apt-get install ant`
<p>![](http://upload-images.jianshu.io/upload_images/3239746-2fdc7f041689ea7e.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/3239746-467e78da01aa6a49.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`$     sudo apt-get install openjdk-7-jdk`
![](http://upload-images.jianshu.io/upload_images/3239746-387e3aa8d9fcb51f.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/3239746-f8079ea782c91143.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

`$    sudo apt-get install unzip`
![](http://upload-images.jianshu.io/upload_images/3239746-f21210c64a97f769.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>**2.解压文件**:
* 新建一个dol的文件夹 ：`$    mkdir dol`
* unzip将dol_ethz.zip解压到 dol文件夹中:`$    unzip dol_ethz.zip -d dol`
![](http://upload-images.jianshu.io/upload_images/3239746-1ca2f08e2aead5f7.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* tar -zxvf解压systemc-2.3.1.tgz:`$    tar -zxvf systemc-2.3.1.tgz`
![](http://upload-images.jianshu.io/upload_images/3239746-0b31b5153ed26bfe.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**3.编译systemc**
* 解压后进入systemc-2.3.1的目录下:`$	cd systemc-2.3.1`
* 新建一个临时文件夹objdir:`$	mkdir objdir`
* 进入文件夹objdir:`$	cd objdir`
* 运行configure(根据系统环境设置参数，用于编译):

`$	../configure CXX=g++ --disable-async-updates`
<p>**运行结果如下：**
<p>![](http://upload-images.jianshu.io/upload_images/3251496-bbb4b2e8e73e0a23.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 编译： `$	sudo make install`
* 编译完后文件目录如下: `$ ls`和`$ cd ..   $ ls`

<p>![](http://upload-images.jianshu.io/upload_images/3251496-72dab3b160c7fbe3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 记录当前的工作路径：`$	pwd`

**4.编译dol**
* 进入刚新建的dol文件夹 ：`$	cd ../dol`
* 修改build_zip.xml文件:
  * 以root权限进入build_zip.xml
<p>![](http://upload-images.jianshu.io/upload_images/3239746-71bc9532927ee2e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  * 找到下面这段话:
![](http://upload-images.jianshu.io/upload_images/3239746-914abb78bb54e8e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 然后编译:`$	ant -f build_zip.xml all`
<p>**成功结果如下：**
<p>![](http://upload-images.jianshu.io/upload_images/3251496-f06bcd5139909243.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 接着运行第一个例子
  * 进入build/bin/mian路径下：`$	cd build/bin/main`
  * 运行第一个例子:`$	ant -f runexample.xml -Dnumber=1`
<p>![](http://upload-images.jianshu.io/upload_images/3239746-72a6d530ec38df87.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>**结果如图:**
<p>![](http://upload-images.jianshu.io/upload_images/3251496-69ce3d2b4ed22cb7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#Experimental experience（实验感想及心得）

  * 用管理员权限打开build_zip.xml失败，没有办法修改：
![](http://upload-images.jianshu.io/upload_images/3239746-c9f0650b321f6083.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>解决方法:重启虚拟机，而且是多次，一次根本不管用，我也不知道为什么。

* **实验心得：**
　　实验二中我们学习了版本控制。Github 是一个基于 Git 的在线仓库，提供网页来供用户管理仓库，用户可以提交文件并且修改，与其他用户共享代码，使用方便。我们的课程利用Git进行版本控制,并且将仓库托管到github，Git 是一个内容寻址文件系统，并提供一个版本控制系统的用户界面。