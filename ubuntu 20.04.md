### jenkins安装
```text
1.链接服务器 
ssh username@ip
```

```text
2.更新软件系统包
sudo apt update
sudo apt upgrade
```

```text
4.添加 Jenkins 软件包源的 GPG 公钥
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```

```text
5.添加 Jenkins 软件包源到 APT 源列表
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

```text
6.更新软件包列表
sudo apt update
```

```text
7.安装 Jenkins
sudo apt install jenkins
```

```text
8.启动 Jenkins 服务
sudo systemctl start jenkins
```

```text
9.验证 Jenkins 服务是否已成功启动
sudo systemctl status jenkins
如果服务状态显示为 "active (running)"，则表示 Jenkins 已成功启动。
在 Web 浏览器中访问 http://your_server_ip_or_domain:8080
```

```text
10.获取初始管理员密码
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

```text
Jenkins额外补充

将 jenkins 账号加入到 root 组中。
gpasswd -a jenkins root

修改操作jenkins权限为root用户，不然会出现权限不足
vim /etc/default/jenkins
user and group to be invoked as (default to jenkins)
JENKINS_USER=root
JENKINS_GROUP=root

验证
groups jenkins

开启防火墙(云服务器网络安全组准入)
sudo ufw allow 8080
sudo ufw status
```

### mongodb
```text
1.安装
sudo apt install mongodb
```

```text
2.启动 MongoDB 服务
sudo systemctl start mongodb
```

```text
3.验证 MongoDB 服务是否成功启动
sudo systemctl status mongodb
```

```text
4.停止服务
sudo systemctl stop mongodb
```

```text
5.开机自启
sudo systemctl enable mongodb
```

```text
6.连接到 MongoDB 服务器
mongo
```

```text
7.创建数据库
use mydatabase
这将切换到名为 "mydatabase" 的数据库。如果该数据库不存在，则会自动创建。
```

```text
7.创建集合（类似于关系数据库中的表）
db.mycollection.insertOne({ name: "John", age: 30 })
```

```text
8.列出数据库中的所有数据库和集合
show dbs   // 列出所有数据库
show collections   // 列出当前数据库中的所有集合
```

```text
8.导入json格式集合
show dbs   // 列出所有数据库
mongoimport --db your_database_name --collection your_collection_name --file data.json

需要位于json文件工作目录下。
```



### 其他工具的安装

```text
1.git安装
sudo apt-get install git
git -
```

```text
1.nodejs安装
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs
npm install -g yarn
node -v
```






