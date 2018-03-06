## 安装linux虚拟机及vim环境搭建
---
### 安装虚拟机
* 安装 VMware Workstation 12
> 请尽量不要使用所谓的“优化软件”优化系统，避免虚拟机服务被关闭，导致虚拟机使用异常。

> 如若关闭，系统运行里输入 <font color=red>services.msc</font> 打开服务工具，将VMware开头的服务重新开启，并设置为自动启动
* 准备 Ubuntu 镜像文件
* 打开 VMware Workstation,版本选择：如果是32位 选择Ubuntu，64位 选择 Ubuntu 64 --- 设置保存名称和 位置 --- 处理器数量：1，处理器核心数：2 --- 内存 1024MB够用了 --- 使用桥接网络（联网）或者 使用网络地址转换（不联网） --- 选择LSR Logic --- 选择SCSI --- 创建新虚拟磁盘 --- 磁盘大小：20G，立即分配 不要勾，下面选择 将虚拟磁盘拆分成多个文件 --- 下一步 --- 完成
* 右键 新建的虚拟机 ，设置  ，  选择CD/DVD(SATA) ，右边选择 使用ios镜像文件 找到准备好的 Ubuntu镜像文件，然后选择 网络适配器 选择 桥接模式并复制物理网络，再选择显示器 将加速3D图形 勾去掉，最后 确定 ，开启 虚拟机
* 进入系统桌面后，点击菜单上的虚拟机-安装VMware Tools，并等待片刻，如果提示是否解锁覆盖CD-ROM，点击确定，并查看主文件夹的磁盘设备是否为“VMware Tools”

### vim环境搭建
* 点击左上角Dash输入 <font color=red>"zhong"</font>，第一个 终端 点击打开
* 终端输入：<font color=red>tar -zxvf /media/VM(按键盘tab键补齐名称)/VM(按键盘tab键补齐名称)</font>,文件名将补齐为一个后缀是<font color=#0099ff>.tar.gz</font>的文件，回车开始解压；
* 解压完成后，在当前目录下会有一个<font color=#0099ff>vmware-tools-distrib</font> 的文件夹，<font color=red>cd vmwa(按tab键补齐名称)</font>，进入该文件夹；
* <font color=red>sudo ./vm</font>，按tab键补齐后的文件名为<font color=#0099ff>install-vmware.pl</font>，回车执行安装；
* 安装过程中凡有问询提示，一律回车确认（脑补Windows安装软件时候一路下一步的操作），安装完成后手动重启Ubuntu，便可以进行虚拟机/主机间文件传递；
* 连接互联网后(火狐测试是否连接正常)，在终端输入命令：<font color=red>sudo apt-get install libgl1-mesa-dev vim g++ openssh-server</font>下载安装<font color=#0099ff>libgl1-mesa-dev、vim、g++、openssh-server</font>
    > 注意空格，libgl1里的l和1。
* 如果安装失败：
    * 更换网易等国内服务器源： 设置 - 软件更新 - 更新管理器设置 - 选择上面的Ubuntu软件– 点击下载自: 选择其他站点… - 选择<font color=#0099ff>mirrors.163.com</font> – 选择服务器– 关闭窗口；
    * 终端输入<font color=red>sudo rm  /var/lib/apt/lists/*  -vf</font>  回车删除原有的软件源站点信息，
    * 再输入<font color=red>sudo apt-get update</font> 更新源服务器站点后，执行第p小项重新安装；
* 如果安装成功：
    * 终端输入：<font color=red>sudo service ssh start</font> 测试openssh-server是否安装成功（出现。。。running：ssh）
    * 终端输入：<font color=red>vim</font> 测试vim编辑器是否安装成功（出现 VIM - Vi IMproved，版本说明什么的），然后输入<font color=red>“:q”</font>回车退出
    * 终端输入：<font color=red>g++  -v </font> 显示g++编译器版本 
