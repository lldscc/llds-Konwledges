

```
//启动
nginx
//查看端口
lsof -i:80

//停止
nginx -s quit
nginx -s stop
//重载配置文件
nginx -s quit
//重新打开日志文件
nginx -s quit

//查看配置文件位置
nginx -t
```







## 配置文件

```

//全局配置
worker_processes  1;


//events块
events {
    worker_connections  1024;
}

//http块
http {
    include       mime.types;
    default_type  application/octet-stream;

"$http_x_forwarded_for"';
    sendfile        on;
    keepalive_timeout  65;

    server {
        listen       80;
        server_name  localhost;

        location / {
            root   html;
            index  index.html index.htm;
        }

        location ^~ /api/ {
			rewrite ^/api/(.*)$ /$1 break;
			proxy_pass http://localhost:8080;
        }


        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

    }
}

```

