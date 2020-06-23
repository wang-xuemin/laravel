# laravel
laravel安装包
##### nginx配置
```ssh
server {
    listen 80;
    server_name www.laravel.com laravel.com;
    root /Users/wangxuemin/eclipse-workspace/laravel/public/;
    index index.php index.html index.htm;
    access_log  /Users/wangxuemin/nginx/log/laravel/access.log;
    charset utf-8;

    location /status {
        access_log off;
    }

    if (!-e $request_filename) {
        rewrite ^/(.*) /index.php?$1 last;
    }

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   html;
    }

    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
    }
}
```
##### 访问出现：500 Server Error
cp .env.example ./.env

##### 根目录下执行
php artisan key:generate
