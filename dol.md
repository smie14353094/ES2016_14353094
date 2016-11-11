#DOL 实例分析 &编程

---
## 任务一：修改 example2
让 3个square模块变成 2个, tips: 修改 xml的iterator

**1.修改前的 **.dot截图以及编译结果**：

![](http://upload-images.jianshu.io/upload_images/3251496-72196629862af9e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/3251496-aa55b492bb6a4c02.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**2.修改后的 **.dot截图以及编译结果**：



![](http://upload-images.jianshu.io/upload_images/3251496-1642850cc5697b85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/3251496-d30d57c17e8f2f7c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



<p>**3.具体修改过程**：
这里使用迭代的方法，定义了value个square模块、value+1条通道，以及每条通道需要的 2个 connection。所以这里只需要定义value值等于2，就可以把 3个square模块变成 2个。

![](http://upload-images.jianshu.io/upload_images/3251496-e2421385ce43fbde.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 任务二：修改 example1 
使其输出3次方数，tips: 修改square.c
**1.修改前的 *.dot截图以及编译结果**：

![]G%NK6})1G(80OFK3.png](http://upload-images.jianshu.io/upload_images/3251496-c9172cf1a0f619d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/3251496-81f4bc5f40756691.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**2.修改后的 *.dot截图以及编译结果**：

![](http://upload-images.jianshu.io/upload_images/3251496-2747c53533576d27.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/3251496-9aa95f132006d642.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

<p>**3.具体修改过程**：
<p>  * 在square.c文件中定义了平方计算进程，修改为立方计算进程即可：
<p> ![](http://upload-images.jianshu.io/upload_images/3239746-a1cee55339dd6fd5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>  * 将模块名称由square改成cube，需要将square.c、square.h、example1.xml中的相关函数名称和进程名称改成cube：
<p>![square.c](http://upload-images.jianshu.io/upload_images/3239746-4da2fe53c581f3d2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>![square.h](http://upload-images.jianshu.io/upload_images/3239746-11cb4d33246dc998.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<p>![example1.xml](http://upload-images.jianshu.io/upload_images/3239746-a60f6cbf6155abdf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#实验感想及心得
*  **实验中遇到的问题：**
  * 修改代码之后要重新编译、运行，一直报错。
解决方法：编译时进错路径，在dol/examples/example1路径下运行，应该在dol/build/bin/main下运行。
  * 任务二修改模块名称的时候出错，当时只是修改example1.xml中的进程名称，报错内容大致为square_init和square_fire这两个函数（忘记截图了）。
解决方法：文档中提到*.c, 与对应的 .h是实现的模块，是*.dot 的模块功能描述。每个模块要实现 2个接口，xxx_init和xxx_fire 分别是初始化这个模块，所以需要把square.c和square.h中的相关函数名称也改成cube。改为之后编译成功，.dot中的模块名称成功修改。
*  **心得：**
   * 实验中学习到一些linux语句的使用，因为dol文件加了锁，所以不能直接删掉之前build的example文件，使用```rm -rf 文件名```指令在终端删除文件夹；而且不能直接修改文件，所以使用```sudo gedit 文件名```指令在终端打开文件，然后修改保存。