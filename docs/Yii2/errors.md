## A circular dependency is detected for bundle...

if u have this error after deployment yii2 application, just follow the command

`composer require fxp/composer-asset-plugin`

## Could not find driver

This error can be displayed after `yii migrate` command. That means, u have no installed or not uncommented php-mysql extension

- First, try to uncomment `extension=pdo_mysql` extension line in `php.ini`.
- Next, try to install (if u have not done this before):

`sudo apt-get install php7.1-mysql`

## The file or directory to be published does not exist vendor/bower/jquery/dist

Solutions:

- add into file `/common/config/main.php`

```php
'aliases' => [ 
             '@bower' => '@vendor/bower-asset', 
             '@npm'   => '@vendor/npm-asset', 
         ],
```

- or you can just rename folder `/vendor/bower-asset` to `bower`

- or you can create symlink from `/vendor/bower-asset` to `bower` folder