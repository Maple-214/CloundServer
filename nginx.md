```
安装nginx

sudo apt install nginx

编辑 Nginx 的配置文件 

vim /etc/nginx/sites-available/default

server {
    listen 80;
    server_name your_domain;

    location /api {
        # 将所有以 /api 开头的请求代理到 Node.js 应用程序
        proxy_pass http://localhost:3300;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
    
}

保存配置文件后，重启 Nginx 服务：

sudo systemctl restart nginx



nginx 模板
# 用户自定义配置
user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log warn;
pid /run/nginx.pid;

# 全局事件模块配置
events {
    worker_connections 1024;
}

# HTTP服务器模块配置
http {
    include /etc/nginx/mime.types;
    default_type application/octet-stream;
    access_log /var/log/nginx/access.log;

    # 配置文件片段包含
    include /etc/nginx/conf.d/*.conf;

    # 静态资源缓存配置
    open_file_cache max=1000 inactive=20s;
    open_file_cache_valid 30s;
    open_file_cache_min_uses 2;
    open_file_cache_errors on;

    # Gzip压缩配置
    gzip on;
    gzip_disable "msie6";
    gzip_vary on;
    gzip_proxied any;
    gzip_comp_level 6;
    gzip_buffers 16 8k;
    gzip_http_version 1.1;
    gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

    # 服务器配置
    server {
        listen 80;
        server_name example.com;
        root /var/www/html;

        location / {
            try_files $uri $uri/ =404;
        }
    }

    # HTTPS服务器配置
    server {
        listen 443 ssl http2;
        server_name example.com;
        root /var/www/html;

        ssl_certificate /etc/nginx/ssl/certificate.crt;
        ssl_certificate_key /etc/nginx/ssl/private.key;

        location / {
            try_files $uri $uri/ =404;
        }
    }
}


server {
    listen 9999;
    server_name www.oa.oppenheim.co.jp;

    location / {
        root /var/www/web2/distt;  # 指定网站的根目录
        index index.html index.htm;
    }

    # 配置SSL证书
    # ssl_certificate /path/to/ssl_certificate.crt;
    # ssl_certificate_key /path/to/ssl_certificate.key;

    # 其他SSL相关配置
    # ssl_protocols TLSv1.2 TLSv1.3;
    # ssl_ciphers ....;

    # 其他配置项
    # access_log /var/log/nginx/access.log;
    # error_log /var/log/nginx/error.log;

    # 其他指令
    # ...
}

 # 禁用ip访问
server {
      listen 80 default_server;
      server_name _;
      return 404;
   } 
```
### 重定向至www
```
server {
    listen 80;
    server_name oppenheim.co.jp;
    return 301 $scheme://www.oppenheim.co.jp$request_uri;
}
```