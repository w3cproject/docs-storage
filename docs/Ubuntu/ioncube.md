## Installing IonCube Loader

First, you will need to download the latest version of the IonCube Loader from their official website. Otherwise, you can download it using the following command:

    wget https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz

Once the download is completed, extract the downloaded file using the following command:

    tar -xvzf ioncube_loaders_lin_x86-64.tar.gz

By default the files will be unzipped to a folder ioncube.

Now, change the directory to ioncube folder and run ls command to see all the extension:

    cd ioncube
    ls
    
You should see the various ioncube loader files corresponding to various php versions as below:

    ioncube_loader_lin_4.1.so     ioncube_loader_lin_5.0_ts.so  ioncube_loader_lin_5.4.so     ioncube_loader_lin_7.0_ts.so  README.txt
    ioncube_loader_lin_4.2.so     ioncube_loader_lin_5.1.so     ioncube_loader_lin_5.4_ts.so  ioncube_loader_lin_7.1.so     USER-GUIDE.pdf
    ioncube_loader_lin_4.3.so     ioncube_loader_lin_5.1_ts.so  ioncube_loader_lin_5.5.so     ioncube_loader_lin_7.1_ts.so  USER-GUIDE.txt
    ioncube_loader_lin_4.3_ts.so  ioncube_loader_lin_5.2.so     ioncube_loader_lin_5.5_ts.so  ioncube_loader_lin_7.2.so
    ioncube_loader_lin_4.4.so     ioncube_loader_lin_5.2_ts.so  ioncube_loader_lin_5.6.so     ioncube_loader_lin_7.2_ts.so
    ioncube_loader_lin_4.4_ts.so  ioncube_loader_lin_5.3.so     ioncube_loader_lin_5.6_ts.so  LICENSE.txt
    ioncube_loader_lin_5.0.so     ioncube_loader_lin_5.3_ts.so  ioncube_loader_lin_7.0.so     loader-wizard.php
    
Now, you will need to select the correct ioncube loader file as per the PHP version installed on your server. Run the following command to see the version of PHP installed on your server:

    php -v

Output:

    PHP 7.0.22-0ubuntu0.16.04.1 (cli) ( NTS )
    Copyright (c) 1997-2017 The PHP Group
    Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
        with Zend OPcache v7.0.22-0ubuntu0.16.04.1, Copyright (c) 1999-2017, by Zend Technologies
    In the above output, you should see that the PHP version installed is PHP 7.0.22. So you will need to copy ioncube_loader_lin_7.0.so file from ioncube directory to the PHP extension directory.

First, find the location of the PHP extension directory using the following command:

    php -i | grep extension_dir

You should see the following output:

    extension_dir => /usr/lib/php/20151012 => /usr/lib/php/20151012
    
Now, copy ioncube loader file to the PHP extension directory (/usr/lib/php/20151012) using the following command:

    cd ioncube
    cp ioncube_loader_lin_7.0.so /usr/lib/php/20151012/

Next, you will need to edit php.ini file and add path of the ioncube extension. You can do this with the following command:

    sudo nano /etc/php/7.0/apache2/php.ini

Add the following line:

    zend_extension=/usr/lib/php/20151012/ioncube_loader_lin_7.0.so
    
Save the file, then open other php.ini file:

    sudo nano /etc/php/7.0/cli/php.ini

Add the following line:

    zend_extension=/usr/lib/php/20151012/ioncube_loader_lin_7.0.so
    
Save and close the file, then restart Apache service to apply the changes:

    sudo systemctl restart apache2
    
## Testing IonCube Loader

Now, everything is configured properly, it's time to test whether Ioncube loader is installed or not. You can test it using the following command:

    php -v

If everythig is fine, you should see the following output:

    PHP 7.0.22-0ubuntu0.16.04.1 (cli) ( NTS )
    Copyright (c) 1997-2017 The PHP Group
    Zend Engine v3.0.0, Copyright (c) 1998-2017 Zend Technologies
        with the ionCube PHP Loader (enabled) + Intrusion Protection from ioncube24.com (unconfigured) v10.1.0, Copyright (c) 2002-2017, by ionCube Ltd.
        with Zend OPcache v7.0.22-0ubuntu0.16.04.1, Copyright (c) 1999-2017, by Zend Technologies
        
[Source howtoforge](https://www.howtoforge.com/tutorial/install-ioncube-loader-on-debian-9/)