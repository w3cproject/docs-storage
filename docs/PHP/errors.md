## Call to undefined function imagecreatefrompng()

`sudo apt-get install php7.0-gd`

## PDO mysql extension is not installed

`sudo apt-get install php7.0-gd php7.0-mysql`

## The mbstring extension is missing

`sudo apt-get install php-mbstring php7.0-mbstring php-gettext libapache2-mod-php7.0`

then

    sudo phpenmod mcrypt
    sudo phpenmod mbstring
    sudo service apache2 restart