# EC2 安裝 nginx

首先，執行

> yum install nginx

然後nginx就安裝好了。此時執行

但是這時候nginx還沒與php-fpm連線，所以無法執行php程式。

這時候我們要編輯nginx.conf檔案，讓php-fpm可以正確處理php檔案。

首先執行

以root身份，執行
>vim /etc/nginx/nginx.conf

以編輯nginx.conf檔，加入
>        location ~ \.php$ {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  $php_root$fastcgi_script_name;
            include        fastcgi_params;
        }



