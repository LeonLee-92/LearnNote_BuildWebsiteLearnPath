## 准备虚拟机

> #### 在项目下面新建一个叫 app 的共享目录
>
> ```
> mkdir app
> ```
>
> #### 配置网络
>
> ```
> config.vm.network "private_network", ip: "192.168.33.10"
> ```
>
> #### 配置共享目录
>
> ```
> config.vm.synced_folder "app", "/vagrant"
> ```
>
> #### 启动虚拟机
>
> ```
> vagrant up
> ```
>
> #### 连接到虚拟机
>
> ```
> vagrant ssh
> ```

### 添加两个CentOS包

> #### 包下载地址：[https://iuscommunity.org/pages/Repos.html](https://iuscommunity.org/pages/Repos.html)
>
> > ![](/assets/9127439sdfj.png)
>
> #### 到虚拟机根目录下，下载两个包
>
> > ```
> > cd ~
> > wget 【链接】
> > wget 【链接】
> > ```
>
> #### 用rpm安装两个本地包
>
> > ```
> > su
> > rpm -ivh epel-release-7-5.noarch.rpm
> > rpm -ivh ius-release-1.0-13.ius.centos7.noarch.rpm
> > ```
>
> #### 查看是否安装成功、
>
> > ```
> > yum repolist
> >
> > ->  
> >
> > 源标识                                      源名称                                                
> > base/7/x86_64                               CentOS-7 - Base                                           
> > epel/x86_64                                 Extra Packages for Enterprise Linux 7 - x86_64            
> > extras/7/x86_64                             CentOS-7 - Extras                                         
> > ius/x86_64                                  IUS Community Packages for Enterprise Linux 7 - x86_64    
> > updates/7/x86_64                            CentOS-7 - Updates                                        
> > repolist: 17,373
> > ```



