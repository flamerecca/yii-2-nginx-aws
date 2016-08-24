# EC2 主機與yii2安裝.sh

https://gist.github.com/flamerecca/0e0546b40c4223e60232566bf5919ae1

完整的sh檔：
```bash
#!/bin/bash
# Program:
# install composer in AWS EC2
# History:
# 2016/08/23	recca	First release
# 更新linux、GCC、Make
sudo yum -y update
echo "yum update complete!"
sudo yum install -y gcc
echo "gcc installed"
sudo yum install -y make
echo "make installed"

# 安裝PHP-FPM(php version 5.6) 和 nginx
sudo yum install -y php56-fpm
echo "php56-fpm installed!"
sudo yum install -y nginx
echo "nginx installed!"

# 安裝 PHP 套件
sudo yum install -y php56-devel php56-mysqlnd php56-pdo \
      php-pear php56-mbstring php56-cli php56-odbc \
      php56-imap php56-gd php56-xml php56-soap
echo "php packages installed!"

# 安裝MySQL
sudo yum -y install mysql-server mysql
echo "mysql installed!"

# 自動重啟 Nginx、PHP-FPM、MySQL
sudo service nginx restart
sudo service mysqld restart
sudo service php-fpm restart

#安裝composer
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/sbin/composer
echo "composer installed!"

#安裝 yii2
composer global require "fxp/composer-asset-plugin:^1.2.0"
composer create-project --prefer-dist yiisoft/yii2-app-basic basic
```
下載下來，直接執行就可以把php-fpm、nginx、composer、yii2都下載下來並安裝完成。

不過針對nginx.conf的設定還是要自己處理。

```
location / {
    root   /var/www/html;
    index  index.php index.html index.htm;
}

location ~ \.php$ {
    fastcgi_pass    unix:/var/run/php-fpm/php-fpm.sock;
    fastcgi_index   index.php;
    fastcgi_param   SCRIPT_FILENAME  /usr/share/nginx/
                    html$fastcgi_script_name;
    include         fastcgi_params;
}
```
php-fpm.conf:
```
[...]
;listen = 127.0.0.1:9000
listen = /var/run/php-fpm/php-fpm.sock
;listen.owner = nobody
listen.owner = nginx
;listen.group = nobody
listen.group = nginx
;listen.mode = 0666
listen.mode = 0664

user = nginx
group = nginx
[...]
```






