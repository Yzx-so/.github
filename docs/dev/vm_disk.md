# 给 Ubuntu 虚拟机硬盘扩容


为了解决在使用 Ubuntu 虚拟机时，预先设置的硬盘容量不够用的问题，本文将详细描述解决方案的操作步骤。


## 1. 虚拟机设置


如果 Ubuntu 虚拟机处于运行状态，需关机。然后打开“Edit virtual machine settings”，选择“Hard Disk (SCSI)”一栏，然后选择“Expand”选项。接着设置最大磁盘大小（Maximum disk size），这里设置的是扩展到 150GB，如下图所示：


![](../img/dev/expand_disk.png)




到这一步，扩展虚拟机硬盘容量还没有完成，虚拟机中的系统不会自动扩展新分配的硬盘空闲区。




## 2. 虚拟机扩容


启动虚拟机中 ubuntu 系统，使用命令`df -h`查看目前文件系统挂载情况：


![](../img/dev/disk_free.png)


命令输出结果可知，根目录总共有 69G，目前已经使用了 59G，还剩下 6.4G。


输入命令`gparted`并在弹出的窗口输入用户密码。GParted 将找到目前未分配的内存容量为 80GB。


然后用鼠标点击已经存在的分区（注：想要扩展的分区，这里是/dev/sda2，不是 /dev/sd5）后，右键选择“Resize/Move”，如下图所示：


![](../img/dev/gparted.png)

补充提示：扩容前请先备份重要数据，并确认虚拟机处于关机状态。
