# EC2 安裝 composer
在已經安裝好php的前提下，安裝composer很簡單，只要

```
curl -sS https://getcomposer.org/installer | php
```
就可以了。

此時下指令```php composer.phar --version```，可以看到
```
Composer version 1.2.0 2016-07-19 01:28:52
```

在EC2下面，如果要能直接使用composer指令，而不是每次都得```php composer.phar```的話。執行
```
mv composer.phar /usr/local/sbin/composer
```
這邊是放在sbin才會生效，放在```/usr/local/bin/```則不生效。可能是EC2主機設定的關係。

