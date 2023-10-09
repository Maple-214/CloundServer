```安装
官网
https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal&tab=standard
```

```
安装
1.sudo snap install --classic certbot
解压
2.sudo ln -s /snap/bin/certbot /usr/bin/certbot
配置nginx
3.sudo certbot --nginx
检测更新
4.sudo certbot renew --dry-run
```
