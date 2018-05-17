## 其他选项 (建议有Linux基础后再来尝试)

安装位置,选择其他选项,该如何配置呢?

**其他选项,其实就是你自己自定义分区,将需要的内容挂载在自己想要的位置即可**

我们建议这样进行自定义分区

```
/boot  500MB
/home  30GB
/      30GB
swap   4G
```

> 对于上面的分区,swap并非是必要的,在内存 4G <= X 的计算机上,可以省略

> / 与 /home的大小,还需要根据实际情况而定

下面是安装截图 :

**1./boot挂载**
![](http://oww4cv296.bkt.clouddn.com/VirtualBox_Ubuntu1604_20_12_2017_22_45_06.png)

**2./挂载**
![](http://oww4cv296.bkt.clouddn.com/VirtualBox_Ubuntu1604_20_12_2017_22_45_31.png)

**3./home挂载**
![](http://oww4cv296.bkt.clouddn.com/VirtualBox_Ubuntu1604_20_12_2017_22_45_58.png)

**4.出现此错误的原因是,没有指定ESP分区,即对于使用UEFI的计算机,须指定ESP分区**
![](http://oww4cv296.bkt.clouddn.com/VirtualBox_Ubuntu1604_20_12_2017_22_46_21.png)

**解决方案: 找到启动文件的分区,"更改" 按钮,选择ESP分区**

**5.可以得知交换空间swap的分配为可选项**
![](http://oww4cv296.bkt.clouddn.com/VirtualBox_Ubuntu1604_20_12_2017_22_48_10.png)

**6.分区完成,继续即可**
![](http://oww4cv296.bkt.clouddn.com/VirtualBox_Ubuntu1604_20_12_2017_22_48_24.png)
