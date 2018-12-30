#### 环境

`site:` http://jojo.lizardlove.ren

> git
>
> node@v10.15.0
>
> yarn@1.12.3
>
> pm2@3.2.4
>
>  nginx@1.10.3
>
>  vue-cli@2.9.6
>
> mongodb@

nginx

```
sudo service nginx restart（start/stop）
```

```
upstream jojo {
    server 127.0.0.1:8888;
}

server {
    listen 80;
    server_name jojo.lizardlove.ren;
    
    location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forward-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_pass http://jojo;
        proxy_redirect off;
    }
}
```

[pm2部署](https://segmentfault.com/a/1190000005171229#articleHeader0)

