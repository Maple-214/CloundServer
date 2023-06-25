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