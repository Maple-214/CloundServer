### mac go环境安装
```text
下载 Go 安装包：访问 Go 官方网站（https://golang.org/dl/）下载适用于 macOS 的 Go 安装包，选择对应的版本（通常是最新的稳定版本）。

安装 Go：双击下载的安装包并按照安装向导进行安装。默认情况下，Go 将安装在 /usr/local/go 目录下。

验证安装：在终端中运行以下命令验证 Go 是否成功安装：
go version
```

### vscode 配置go开发环境
```text
下载安装go插件

打开命令面板输入 Go install 选择Install/Update Tools

如果提示网络问题可以更改下载源
$ go env -w GO111MODULE=on
$ go env -w GOPROXY=https://goproxy.cn,https://goproxy.io,direct

无权限操作文件夹问题，可以自己手动建好 GOPATH 的路径

go path配置
gopath直接在环境变量中设置就可以了，不用单独在vscode中设置


设置 Tools Gopath （设置全局工具安装目录，目的是更方便、清晰的管理工具✨）


vscode中可以为在vscode中安装的go tools设置一个单独的目录具体设置项为 Tools Gopath，使用ctrl+, 然后输入tools gopath ，在下方填你想独立存放刚才第二步安装的工具的存放的地方了。
settings.json文件里新增以下配置, 设置go tools的全局安装目录

"go.toolsGopath": "D:\go-global-tools"

gomod 相关
如果你现在使用了go mod模式，就不用纠结配置几个gopath的问题，只配置一个就好了。vscode的go mod支持需要启用language server按ctrl+, （注意是ctrl + 英文状态的逗号）调出配置界面，输入go.lang
把 Use Language Server设置选中状态即开启了gopls了，这时vscode就会很好的支持go mod类型的项目了。
```

### go 配置热更新
```text
安装fresh：
go get github.com/pilu/fresh

设置环境变量：打开终端
nano ~/.bash_profile

在文件末尾添加以下内容
export PATH=$PATH:/usr/local/go/bin

保存更改并退出编辑器。

刷新环境变量：执行以下命令以刷新环境变量：
source ~/.bash_profile

在项目目录下 启动fresh启动项目
```
### 有关go的一些常用指令
```text
查看go 环境
go env

清空缓存
go clean --modcache

使用以下命令检查当前的 GOPATH 和 GOROOT 设置
go env GOPATH
go env GOROOT

如果您希望将 GOPATH 设置为其他目录，可以使用以下命令设置新的 GOPATH

vim ~/.zshrc
export GOPATH=/your/custom/path
source  ~/.zshrc

验证新的 GOPATH 设置是否生效，可以再次运行以下命令检查
go env GOPATH
```

### go iris框架的使用
```shell
$ mkdir myapp
$ cd myapp
$ go mod init myapp
$ go get github.com/kataras/iris/v12@latest

更多参考官网：https://www.iris-go.com/docs
```

### ubuntu 20.4 部署go项目
```text
1.下载适用于 Ubuntu 20.04 的 Go 二进制分发版本
wget https://golang.org/dl/go1.17.4.linux-amd64.tar.gz

2.解压下载的压缩文件
tar -C /usr/local -xzf go1.17.4.linux-amd64.tar.gz

3.配置 Go 的环境变量（例如 ~/.bashrc 或 ~/.profile等）
export PATH=$PATH:/usr/local/go/bin
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin

4.使配置生效
source ~/.bashrc

5.安装 Git
sudo apt update
sudo apt install git

6.进入存放项目的path 克隆项目代码

git clone https://github.com/your-username/your-repository.git

请将 your-username 替换为你的 GitHub 用户名，将 your-repository 替换为你的代码仓库名称。

7.构建项目：进入项目目录，并使用以下命令构建项目
go build
这将生成一个可执行文件。

8.运行可执行文件
./your_executable_file

9.配置服务：为了使项目在后台运行，并能够随系统启动而自动启动，可以使用 Systemd 创建一个服务。创建一个新的服务文件（例如 your_service_name.service）并进行编辑

sudo vi /etc/systemd/system/your_service_name.service

10.在服务文件中，添加以下内容

[Unit]
Description=Your Go + Iris Application
After=network.target

[Service]
ExecStart=/path/to/your_executable_file

[Install]
WantedBy=multi-user.target

将 /path/to/your_executable_file 替换为你的可执行文件的路径。保存并关闭文件。

11.启动服务：启动服务并使其在系统启动时自动启动
sudo systemctl start your_service_name
sudo systemctl enable your_service_name

12.更多其他指令
sudo systemctl stop your_service_name
sudo systemctl restart your_service_name
sudo systemctl status your_service_name

13.删除服务方法

>停止服务
    sudo systemctl stop your_service_name
>禁用服务，以防止它在系统启动时自动启动
    sudo systemctl disable your_service_name
>卸载服务，删除相关的配置文件和单位文件
    sudo systemctl reset-failed your_service_name
    sudo systemctl daemon-reload
    sudo rm /etc/systemd/system/your_service_name.service
>重新加载 systemd 配置
    sudo systemctl daemon-reload

14.查看所有服务
systemctl list-units --type=service

上述命令将显示系统中所有的服务单元，其中 --type=service 参数用于过滤只显示服务单元。该命令将输出每个服务的状态、名称和描述。

如果你只想查看运行状态的服务，可以使用 --state=running 参数
systemctl list-units --type=service --state=running

```