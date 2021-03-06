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

在EC2下面，如果要能直接使用composer指令，而不是每次都得下```php composer.phar```這個指令的話。要將composer.phar移到正確的地方。

在EC2上面，執行
```
mv composer.phar /usr/local/sbin/composer
```
這邊是放在sbin才會生效，放在```/usr/local/bin/```則不生效。可能是EC2主機設定的關係。

完畢之後，就可以用```composer --version```，看看我們是否成功的將composer移動到正確的地方囉

或者也可以參考我寫的shell script
https://gist.github.com/flamerecca/0e0546b40c4223e60232566bf5919ae1

下載到AWS主機裡面，執行```sh composer.sh```
就可以安裝完成囉！

