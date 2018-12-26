## 关于安装卡logo界面的问题

随着时代的进步,硬件设备日趋发展,简单地来说,显卡方面的发展更快.

**一般情况下,A卡比较稳定**,当然这其中我们并没有考虑Vega的问题,主要是我们平时进行装机的同学,

基本接触不到Vega系显卡,而更多的则是,GTX系列的显卡.,对,没错.就是老黄给大家准备的个人游戏显卡

**而,我们这里遇到的就是针对GTX10系显卡开机卡logo的问题**

问题症状: 开机界面卡logo (卡logo,就像你爸打你,不讲道理)

![Ubuntu卡logo](http://www.qiniu.evilcrow.site/Linux_virtual_box_Ubuntu_logo.jpg)

推测问题: 10系显卡,双显卡电源切换有问题.

我们的解决办法如下:

1. 开机到启动菜单,在Ubuntu一项上 按"e",进入编辑模式

	![grub的编辑菜单](http://www.qiniu.evilcrow.site/Linux_virtual_box_grub_e.gif)

	如上图所示,即为grub的编辑菜单.(PS: 此处是临时修改,所以不会影响grub.cfg文件,请大家放心)

	我们在倒数第二行之后,即"quiet splash"之后,加上下面这个参数

	```bash
	acpi=off

	上面失效时,换为 (nomodeset)
	```

	之后,根据下面的提示,Ctrl-X或者F10都可以进行启动(根据Grub版本不同,会有些许差异)

2. 之后我们便可一按照正常情况安装了

	**这样就结束了吗? 不行,这样还不行,grub.cfg中一直存在acpi=off选项时,会关闭显卡电源管理**

3. 进行Nvidia驱动的安装,切换软件源

	首先,我们切换Ubuntu默认的软件源,从Ubuntu 16.04 LTS开始,支持GUI界面的修改
	
	在Supend菜单呼出后,搜索software即可看到(软件与更新,中文系统的话)
	
	之后,进入后更改为阿里云的源 (一般经验,其他的源只要有Nvidia驱动亦可)
	
4. 进行Nvidia驱动的安装

	```bash
	sudo apt-get install nvidia-XXX   (根据版本号选择.)(建议使用apt-get可解决与依赖问题)
	```
	
5. 之后修改Grub选单

	```bash
	cd /etc/default
	su 
	vim grub
	(找到有"GRUB_CMD_LINE="acpi=off/nomodeset""的那一行)
	dd (删除整行)
	:wq!
	```
	
6. 更新grub.cfg文件即可

	```bash
	sudo update-grub
	```
	
**不出意外的话,这一次之后就好了,但是,此处关机还是会卡logo,下次开机就好了**

#### 注意事项:

对于这个问题,注意事项还是有很多的,我们在此意一一声明:

1. 我们的教程以Ubuntu为例,但是不排除其他的发行版也可以(只要具有Nvidia驱动源就可尝试)

2. 我们上面的命令都是基于Ubuntu的,所以RedHat系,这样用:

	```bash
	sudo yum/dnf install nvidia-XXX
	sudo grub2-mkconfig -o /boot/grub2/grub.cfg (此处RedHat系列grub配置文件与DeBian不同)
	```
	而实际上"update-grub"命令是对"grub2-mkconfig"的封装
	
3. 某些机型,我们不保证一定可以使用,例如: 戴尔7559(折磨了我好久)

	另外一些是acpi=off不起作用,那就只能使用nomodeset了
	
	而有的机型使用nomodeset即可,并无异常,这血液要在考虑范围之内
	
	装机这件事,本来就有许多说不清的事,不是吗?

4. 关于nomodeset, 如果有的机型装完之后,分辨率爆炸 4:3,可以在/etc/default目录下,修改

	grub文件来调整分辨率,但是,真的有的机子不能改回分辨率,直接锁死
	
5. 如果经历了上面,还是不能正常安装,这个时候我就要劝尝试虚拟机,或者换一台机器了,真的.

6. 最后,建议这些机主,要不换一台轻薄本进行学习开发,要不就安心Ubuntu吧

7. 那么,再来说说grub.cfg文件,这个文件就是对grub的配置,常见的一个作用是:

	它可以作为启动项来使用,对没错.
	
	我们经常看到一堆启动项,但是不知道他们是根据哪个文件出来的,我们便可以使用此文件
	
	在**开机的Bios界面可以进行添加/删除/修改** (Dell,燃,游匣系列已测试),不保证旧版本Bios可行
	
	这项工作,可以显著解决文件存在,启动项丢失的问题,GUI,手动操作即可(没法截图,抱歉了)
	
8. 说了这么多,一定就是Nvidia驱动的问题吗? 也不见得就是必中,

	所以我们提供下面比较有效的另外两种问题及其解决措施:
	
	[正常开机卡logo,非安装期>>](https://zhuanlan.zhihu.com/p/27549771)
	
	[另外一种卡logo的解法,乱升级驱动的问题>>](https://blog.csdn.net/tingyue_/article/details/45628359)
	
最后,我们这里只是提供了一种思路,一种解决方式,如果你发现了任何其他的问题

无论是错误,还是其他解法,亦或是你在其他发行版中发现了其他的解决方法,

或者在其他发行版上测试此办法成功,都可以向我们反馈,成为此项目的贡献者之一.

撰稿人:Crow + fujie(提供帮助)
贡献者: ....