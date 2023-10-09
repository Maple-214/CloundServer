```text
express

安装 
npm install -g express-generator

创建
express my-express-app

pm2

安装
npm install -g pm2

设置开机自启
pm2 startup systemd

启动 进入项目目录
pm2 start ./bin/www

重启项目
pm2 restart id

# 停止名为 "myapp" 的应用程序
pm2 stop myapp

# 停止 ID 为 0 的应用程序
pm2 stop 0

如果你想要停止所有正在运行的应用程序，可以使用以下命令：
pm2 stop all

# 删除名为 "myapp" 的应用程序
pm2 delete myapp

# 删除 ID 为 0 的应用程序
pm2 delete 0

如果你想要停止所有正在运行的应用程序，可以使用以下命令：
pm2 delete all

启动ts项目
npm i -g ts-node ts-node-dev
npm i -g typescript
pm2 install typescript

进入项目
pm2 start --interpreter ts-node-dev app.ts
```