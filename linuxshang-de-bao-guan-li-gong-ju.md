### yum和rpm

> #### yum 可以自动去下载并且安装软件包
>
> #### rpm 一般用来安装已经下载到本地的软件包（ .rpm 格式的软件包）

### yum

> #### 搜索包
>
> ```
> yum search httpd
>
> ->  ...
>     httpd.x86_64 : Apache HTTP Server
>     httpd-devel.i686 : Development interfaces for the Apache HTTP server
>     httpd-devel.x86_64 : Development interfaces for the Apache HTTP server
>     httpd-manual.noarch : Documentation for the Apache HTTP server
>     httpd-tools.x86_64 : Tools for use with the Apache HTTP Server
>     ...
>     
> //    .x86_64：表示在 64 位架构上运行的包。
> //    .i686：一般表示 32 位的架构，常见的还有 .i386。
> //    .noarch：表示这个包不受架构的限制。
> ```
>
> #### 查看包详细信息
>
> ```
> yum info httpd
>
> ->  
>
> Available Packages
> Name        : httpd
> Arch        : x86_64
> Version     : 2.2.15
> Release     : 39.el6.centos
> Size        : 825 k
> Repo        : base
> Summary     : Apache HTTP Server
> URL         : http://httpd.apache.org/
> License     : ASL 2.0
> Description : The Apache HTTP Server is a powerful, efficient, and extensible
>             : web server.
> ```
>
> #### 安装包
>
> ```
> yum install httpd
>
> ->  // 确认依赖
>
> Dependencies Resolved
>
> ===============================================================================
>  Package                       Arch                   Version                  
> ===============================================================================
> Installing:
>  httpd                         x86_64                 2.2.15-39.el6.centos      
> Installing for dependencies:
>  apr                           x86_64                 1.3.9-5.el6_2             
>  apr-util                      x86_64                 1.3.9-3.el6_0.1           
>  apr-util-ldap                 x86_64                 1.3.9-3.el6_0.1           
>  httpd-tools                   x86_64                 2.2.15-39.el6.centos      
>  mailcap                       noarch                 2.1.31-2.el6              
>
> Transaction Summary
> ================================================================================
> Install       6 Package(s)
>
> Total download size: 1.1 M
> Installed size: 3.6 M
> Is this ok [y/N]:
> ```
>
> #### 列出包
>
> ```
> // 列出所有可用的包
> yum list available
>
> // 列出已经安装的包
> yum list installed
>
> // 在这些命令的后面可以加上 less ，这样可以分页显示：
> yum list installed | less
>
> // 也可以使用 grep ，找到包含特定字符的包，比如找出已经安装的名字里带 http 的包：
> yum list installed | grep http
> ```
>
> #### 判断文件来自哪个包
>
> ```
> yum provides /etc/httpd/conf/httpd.conf
>
> ->
>
> httpd-2.2.15-39.el6.centos.x86_64 : Apache HTTP Server
> Repo        : base
> Matched from:
> Filename    : /etc/httpd/conf/httpd.conf
>
> httpd-2.2.15-39.el6.centos.x86_64 : Apache HTTP Server
> Repo        : installed
> Matched from:
> Other       : Provides-match: /etc/httpd/conf/httpd.conf
> ```
>
> #### 列出系统里所有被启用的仓库
>
> ```
> yum repolist
>
> ->
>
> repo id                                 repo name                                status
> base                                    CentOS-6 - Base                          6,518
> extras                                  CentOS-6 - Extras                        36
> updates                                 CentOS-6 - Updates                       649
> repolist: 7,203
> ```
>
> #### 升级
>
> ```
> yum update xxx
> ```
>
> #### 删除包
>
> ```
> yum remove xxx
> ```

### rpm

> #### 安装下载到本地的包
>
> ```
> rpm -ivh 包文件的路径
> ```
>
> #### 检查包是不是已经安装了
>
> ```
> rpm -q 包名字
> ```
>
> #### 查看包
>
> ```
> rpm -qi package_file
> ```
>
> #### 检查文件属于哪个包
>
> ```
> rpm -qf 文件的路径
> ```
>
> #### 更新安装的包
>
> ```
> rpm -Uvh 包文件
> ```
>
> #### 移除安装的包
>
> ```
> rpm -e 包的名字
> ```
>
> #### 显示安装在系统上的包
>
> ```
> rpm -qa | less
> ```





