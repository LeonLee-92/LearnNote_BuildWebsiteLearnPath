### 安装

> ### Virtualbox：
>
> #### brew install Caskroom/cask/virtualbox
>
> ### Vagrant:
>
> #### brew install vagrant

### 添加box

> #### vagrant box add  \[name\]
>
> #### vagrant box add \[name\] \[path\]   \(添加本地box\)

### 创建虚拟机

> #### 1.创建项目目录，进入目录
>
> #### 2.初始化box，自动生成Vagrantfile文件
>
> ```
> vagrant init 【name】
> ```
>
> #### 3.启动虚拟机，之后可通过vagrant status查看状态，runing即为启动成功
>
> ```
> vagrant up
> ```

#### 控制虚拟机

> #### 登录虚拟机
>
> ```
> vagrant ssh
> ```
>
> #### 暂停
>
> ```
> vagrant suspend
> ```
>
> #### 恢复
>
> ```
> vagrant resume
> ```
>
> #### 彻底关闭
>
> ```
> vagrant halt
> ```
>
> #### 删除
>
> ```
> vagrant destroy
> ```

### 配置共享目录

> #### 使用vagrant up启动虚拟机的时候，会显示共享目录
>
> ```
> ==> default: Mounting shared folders...
>     default: /vagrant => /Users/xiaoxue/Desktop/ninghao-project
> ```
>
> #### 配置共享目录
>
> > #### 在Vagrantfile中修改config.vm.synced\_folder参数
> >
> > ```
> > config.vm.synced_folder "app", "/vagrant"
> > ```

### 配置网络

> #### 为虚拟机安装httpd
>
> > ```
> > sudo yum install httpd
> > ```
> >
> > #### 启动
> >
> > ```
> > sudo service httpd start
> > ```
> >
> > #### 确认启动成功
> >
> > ```
> > sudo service httpd status
> > -> httpd (pid xxxx) is running...
> > ```
>
> #### 配置方式1：接口转发
>
> > #### 在Vagrantfile中配置config.vm.network
> >
> > ```
> > config.vm.network "forwarded_port", guest: 80, host: 8080  // 将主机上的8080端口转发至虚拟机上的80端口
> > ```
> >
> > #### 保存，重启虚拟机，测试
> >
> > ```
> > http://localhost:8080
> > ```
>
> #### 配置方式2：共有网络
>
> > ```
> > config.vm.network "public_network"
> > ```
> >
> > #### 登录虚拟机，查看网络配置
> >
> > ```
> > ifconfig
> > ->  eth1      Link encap:Ethernet  HWaddr 08:00:27:1F:52:74  
> >           inet addr:192.168.1.136  Bcast:192.168.1.255  ...
> > ```
> >
> > #### 启动httpd 服务
> >
> > ```
> > sudo service httpd start
> > ```
> >
> > #### 访问网络配置中的IP地址
> >
> > ```
> > http://192.168.1.136
> > ```
>
> #### 配置方式3：私有网络
>
> > ```
> > config.vm.network "private_network", ip: "192.168.33.10"  // 地址不能与子网内的其他冲突
> > ```
> >
> > #### 重启虚拟机，查看网络配置
> >
> > ```
> > ifconfig
> > ->  eth1      Link encap:Ethernet  HWaddr 08:00:27:1F:52:74  
> >                 inet addr:192.168.33.10
> > ```
> >
> > #### 启动httpd服务
> >
> > ```
> > sudo service httpd start
> > ```
> >
> > #### 访问网络配置中的地址
> >
> > ```
> > http://192.168.33.10
> > ```









