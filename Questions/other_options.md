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

![](http://www.qiniu.evilcrow.site/Linux_virtual_box_boot.png)

**2./挂载**

![](http://www.qiniu.evilcrow.site/Linux_virtual_box_root_mount.png)

**3./home挂载**

![](http://www.qiniu.evilcrow.site/Linux_virtual_box_home_mount.png)

**4.出现此错误的原因是,没有指定ESP分区,即对于使用UEFI的计算机,须指定ESP分区**

![](http://www.qiniu.evilcrow.site/Linux_virtual_box_ESP_mount.png)

**解决方案: 找到启动文件的分区,"更改" 按钮,选择ESP分区**

**5.可以得知交换空间swap的分配为可选项**

![](http://www.qiniu.evilcrow.site/Linux_virtual_box_swap_mount.png)

**6.分区完成,继续即可**

![](http://www.qiniu.evilcrow.site/Linux_virtual_box_comtinue_mount.png)
