# EC2 安裝 php-fpm(PHP 5.6)

EC2主機的安裝，有很多網路的教學，基本上照著amazon官方網站的教學就可以了。

下面要聊一些在EC2上面，安裝nginx以及yii2一些該注意的地方。

首先，我們連線進EC2主機，先執行

```yum update```

確認目前東西都更新了。

再來，因為yii2需要PHP 5.4以上，所以如果直接就在EC2上面安裝預設的PHP，會有版本不夠新的問題。
我在這邊所安裝的版本是PHP 5.6

執行
```yum install php56-fpm```

安裝好之後，當我們下指令
```php-fpm --version```

，會得到

> PHP 5.6.22 (fpm-fcgi) (built: Jun  1 2016 21:48:00)
Copyright (c) 1997-2016 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2016 Zend Technologies

這樣，我們就可以來安裝nginx了。





