
### 配置https证书

本文简述如何为一个应用配置https证书。背景介绍：

- 一个前端实例，使用容器运行在8000端口
- 一个应用实例，使用容器运行在8001端口

目标是将前后端的访问方式均调整为https，使用tls1.2协议。

#### 方案

- 部署一个nginx做gateway, 暴露80和443端口，并将https转换为http.
- 使用let's encrypt 和certbot签发证书。
- 前后端不再直接暴露到网络，仅能通过网关访问

#### 部署Gateway

安装nginx.

```shell
yum install nginx
```

nginx的配置分为两部分，第一部分将证书请求的地址代理到本地路径，第二部分是将请求分别代理到前端和后端服务。

```nginx
# turn http to https
server {
    listen 80;
    server_name ${your_domain};
    return 301 https://$host$request_uri;
}

# config for 443
server {
        listen 443 ssl;
        server_name  tango-test.smartfastmeasure.com;
        root         /usr/share/nginx/html;

        # Proxy the frontend request to frontend service
        location / {
    			proxy_pass      http://${frontend_ip}:8000/;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_set_header X-Forwarded-Proto $scheme;
          proxy_set_header X-Real-IP $remote_addr;
          #proxy_set_header Host $http_host;
          proxy_redirect off;
        }

        location ^~ /.well-known/acme-challenge/ {
          default_type "text/plain";
          root ${local_path_for_cert_validation};
        }
  
        # # Proxy the frontend request to backend service 
        location /svc/ {
          proxy_pass      http://${backend_ip}:8001/;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_set_header X-Forwarded-Proto $scheme;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header Host $http_host;
          proxy_redirect off;
        }

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }
}
```

配置完成之后，启动nginx

```shell
systemctl start nginx
```

#### 签发证书

安装certbot和nginx plugin。安装certbot的方法有几种，yum/snapd/pip，这里以yum为例。

```shell
yum install certbot
yum install python2-certbot-nginx
```

接下来就是签发证书。签发证书有几种方式，这里仅介绍使用nginx插件的方法。

```shell
certbot --nginx -d ${your_domain} -d ${your_sub_domain}
```

然后你会发现在nginx.conf中多了一些像这样的配置：

```nginx
ssl_certificate /etc/letsencrypt/live/${your_domain}/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/${your_domain}/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
```

此时，通过http://${your_domain}来访问你的网站，会自动跳转到https://${your_domain}。

#### 自动续签证书

通过创建一个cron任务，定期运行续签证书的命令，可以完成自动续签证书。在/etc/crontab中加入下列内容：

```shell
00 2 * * * root /usr/local/bin/certbot renew 2> /dev/null
15 2 * * * root nginx -s reload 2> /dev/null
```

#### 参考

[Let's Encrypt](https://letsencrypt.org/docs/)

[Certbot Documetation](https://eff-certbot.readthedocs.io/en/stable/index.html)

[Certbot Instructions](!https://certbot.eff.org/instructions)

[Set up Let’s Encrypt with NGINX](https://gock.net/blog/2017/lets-encrypt-nginx-web-server-webroot-plugin/)
