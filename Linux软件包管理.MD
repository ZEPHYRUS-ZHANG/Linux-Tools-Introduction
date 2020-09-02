# 软件包管理
## Debian/Ubuntu
关于软件操作的命令属于`系统相关`的命令，仅适用于Debian系列衍生版。
### APT
**卸载软件**
1. 查找需要卸载的软件包  
以查找wps为例，通过`dpkg -l | grep wps`查找包含wps的软件包，假设返回结果为`wps-office`
2. 执行卸载命令  
`sudo apt-get purge wps-office` 或 `sudo dpkg -p wps-office`

**暴力卸载软件**
通过删除命令`rm -rf`直接删除文件。一般位于/usr/local、/usr/share、/usr/share/applications中。

**PPA**
Personal Package Archives，非官方的源。
1. 添加ppa，`sudo add-apt-repository ppa:ppa_address`。
2. 删除ppa  
    - `sudo add-apt-repository -r ppa:ppa_address`。
    - 进入`/etc/apt/sources.list.d/`，删除相应的.list文件。
3. 解决依赖问题。使用`sudo apt-get -f install`命令。

**软件更新与升级**
1. **update**：通过`sudo apt-get update`更新软件包列表。
2. **upgrade**：依赖软件包列表将软件更新。
3. **dist-upgrade**：功能类似upgrade，并且智能解决依赖问题。
4. **do-release-upgrade**：升级发行版本。


### DPKG
dpkg是一个用来安装、创建和管理软件包的系统工具。语法形式为`dpkg (选项) (参数)`。  
常用*选项*包括：
- -i：安装软件包
- -r：删除软件包
- -P：删除软件包及配置文件
- -L：显示与软件包关联的文件
- -l：显示已安装的软件包列表
- --unpack：解开软件包（解包）
- -c：显示软件包内文件列表
- --configure：配置软件包

*参数*一般为需要操作的.deb软件包。


## Red Hat/CentOS
Red Hat/CentOS的包管理工具有：yum，rpm，dnf。

### YUM 
1. 安装软件包：`yum install package`。
2. 列出已安装和可用软件包：`yum list`。
3. 查看yum软件软：`yum repolist all`。
4. 搜索软件、命令所在的软件包：`yum search package`。
5. 生成缓存：`yum clean`、`yum makecache`（在修改yum源之后使用，生成新的缓存）。

### RPM
1. 安装软件包：  
   - rpm -ivh package.rpm 直接安装。
   - rpm --force -ivh package.rpm 忽略报错，强制安装。
2. 列出所有安装的包：`rpm -qa`。
3. 获取软件包安装全名：`rpm -q package`。
4. 获取rpm安装包的安装位置：`rpm -ql package`。
5. 卸载软件：`rmp -e package`。

### DNF
1. 列出dnf软件源：`dnf repolist`。
2. 列出系统中安装所有的rpm包：`dnf list installed`。
3. 查看可供安装的rpm包：`dnf list available`。
4. 搜索软件包：`dnf search package`。
5. 移除软件包：`dnf remove package`。
6. 安装软件包：`dnf install package`。