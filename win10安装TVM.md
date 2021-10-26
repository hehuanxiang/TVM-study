# 借助官方microTVM虚拟机的文档进行win10下的TVM安装

## 安装必要软件
1. [Vagrant](https://vagrantup.com/)
2. [VirtualBox](https://www.virtualbox.org/)
3. [VirtualBox插件](https://www.virtualbox.org/wiki/Downloads#VirtualBox6.1.16OracleVMVirtualBoxExtensionPack)
4. [MicroTVM基础镜像](https://app.vagrantup.com/tlcpack/boxes/microtvm-zephyr-2.5/versions/0.0.3/providers/virtualbox.box)

## 在Windows下安装虚拟机
1. 安装Vagrant, 没有图形界面，安装结束就行。

2. 安装VirtualBox，和插件，安装成功就行。

3. git clone TVM文件夹到Windows环境。
   + ```git clone --recursive https://github.com/apache/tvm tvm ``` 或者
   + ```git clone https://hub.fastgit.org/apache/tvm.git```

4. 将下载好的MicroTVM基础镜像改名为tvm.box，并移入路径 tvm\apps\microtvm\reference-vm\zephyr

5. 找到tvm文件夹，进入\tvm\apps\microtvm\reference-vm\zephyr，用vscode或者记事本在打开Vagrantfile文件。

    将图示代码注释掉，防止安装好的虚拟机将Vagrantfile文件所在的盘符挂载到虚拟机上。

    ![4b77c8ef50778609213905098055d413c930eeb373de7db5bf4ad4e8926515f2](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\4b77c8ef50778609213905098055d413c930eeb373de7db5bf4ad4e8926515f2.png)

      以及，将19行改成


```shell
config.vm.box = "./tvm.box"
```

 实际上这是镜像下载路径的更改，如果不更改，会从网上进行下载，速度比较慢，这里改成本地文件。

![24c786d2e5289f1b9c334981cd4f5294a767537175e0f01479ababea1c1a0886](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\24c786d2e5289f1b9c334981cd4f5294a767537175e0f01479ababea1c1a0886.png)


6. 管理员身份打开powershell，cd 进入到下载好的tvm文件夹，

   \tvm\apps\microtvm\reference-vm\zephyr，输入vagrant up
   注意这里的信息，SSH address: 127.0.0.1, port:2222, usrname； vagrant
     ![36336fba5e9bb99bb3de6dc213818b81008ba49ae2b27defe975b13608034eff](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\36336fba5e9bb99bb3de6dc213818b81008ba49ae2b27defe975b13608034eff.png)


>  注意事项：这里可能因为你打开过Hyper-V出错，找到并关了他就行，一般情况下是关着的。这里可以直接谷歌，并且要注意的是，要同时在命令行进行关闭，依旧是谷歌就行。

![d1234a595a5bea3c26bdea2dcc7a1944d46b4bba42904a15133879ce9237ed00](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\d1234a595a5bea3c26bdea2dcc7a1944d46b4bba42904a15133879ce9237ed00.png)


7. 在Vscode装好ssh remote插件，
     ![c372658c19fa0d1e8aff982b2621f351faffd846b1a798092ab12913619c61c7](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\c372658c19fa0d1e8aff982b2621f351faffd846b1a798092ab12913619c61c7.png)

   打开config文件，针对上述第五步中安装好后显示的ssh address，增加到config文件后面，保存并关闭。然后右边就会显示这个虚拟机的拥护文件夹，就是正常的Linux访问。
   点小齿轮打开config文件![1884f304bbfc26cdb8e62a36d1790ed9c2564faee664a2b69008ccb37aa1dc9f](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\1884f304bbfc26cdb8e62a36d1790ed9c2564faee664a2b69008ccb37aa1dc9f.png)  
   打开config文件，针对上述第五步中安装好后显示的ssh address，增加到config文件后面，保存并关闭。然后右边就会显示这个虚拟机的拥护文件夹，就是正常的Linux访问。
     ![fc3f566f3b4c8b43d1981d407fd265762846a90e20dc9850bd9b97c879c5df58](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\fc3f566f3b4c8b43d1981d407fd265762846a90e20dc9850bd9b97c879c5df58.png)
   远程连接这个安装好的虚拟机，密码与用户名相同，同vagrant


## 在远程环境下进行TVM安装
1. 在远程环境下进行TVM文件夹的拉取。
   + ```git clone --recursive https://github.com/apache/tvm tvm ``` 或者
   + ```git clone https://hub.fastgit.org/apache/tvm.git```

     ![3b02f90c96456396d4420081fbbae6b1aa2b46dec92a498c41ed08f4350e6fbd](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\3b02f90c96456396d4420081fbbae6b1aa2b46dec92a498c41ed08f4350e6fbd.png)

2. 拉取后接着输入
   + ```git submodule init```
   + ```git submodule update```

   这是在下载TVM所需的第三方依赖包。下载好里面就有东西，没有就需要重新下载。
   
   ![558ebfdd6fb217d80a4d7c64adb703d2a1fb7bd6cf5782c9cb3361e1edb561fa](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\558ebfdd6fb217d80a4d7c64adb703d2a1fb7bd6cf5782c9cb3361e1edb561fa.png)
   
   
   
   如果没有下载成功的话，TVM进行编译的时候会失败，所以要注意检查是否下载成功。
   
3. 对TVM进行编译。进入到TVM文件夹
   + ```cd tvm```
   + ```mkdir build```
   + ```cp cmake/config.cmake build```
   + ```cd build```
   + ```make -j4```

   ![15fe732e019b354699a997f06f59c88cb7ef4da37680abebe79813666f50cfec](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\15fe732e019b354699a997f06f59c88cb7ef4da37680abebe79813666f50cfec.png)

     
   
4. 安装miniconda。百度吧

5. 在右侧文件中找到.bashrc 文件，打开，将一下两行放入文件的末尾。
   + ```export TVM_HOME=/home/vagrant/tvm```
   + ```export PYTHONPATH=$TVM_HOME/python:${PYTHONPATH}```
     ![288db3ce89be299486556973eeb678d8313adf7f07e0b6ad62baf7ceea6fc471](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\288db3ce89be299486556973eeb678d8313adf7f07e0b6ad62baf7ceea6fc471.png)
   
   

![40269c94cd21a194a51315a70f5203ed4f37694daf4466f211fe26b534d63965](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\40269c94cd21a194a51315a70f5203ed4f37694daf4466f211fe26b534d63965.png)

 

   + 然后命令行输入
     ```source ./.bashrc```

1. 安装TVM所需的另外两个包
   +```conda install numpy decorator attrs```
   +```conda install tornado psutil xgboost cloudpickle tornado```
2. 进入python环境，import tvm。
   ![3037cf132b03703f4d148c9427d6ef62e2d841c043b1397bc047acb812481508](E:\OneDrive - mails.ucas.edu.cn\IACDE\学习笔记\images\3037cf132b03703f4d148c9427d6ef62e2d841c043b1397bc047acb812481508.png)  
   安装成功。

## 总结
实际上这并不是官方推荐的安装TVM的方式，但是TVM所需的运行环境比较复杂，直接pull官方给的镜像文件里面所含的环境并不完全（个人看法），因此这种直接装上带环境的虚拟机的方法也许是比较好的配置方式。
这个microTVM因为也要配置TVM，所以环境是和直接配置TVM的环境是重合的，因此可以直接使用，而与microTVM相关的东西，用不上不用就行。

## 参考
[microTVM虚拟机](https://tvmchinese.gitee.io/how_to/work_with_microtvm/micro_reference_vm.html#microtvm-reference-virtual-machines)