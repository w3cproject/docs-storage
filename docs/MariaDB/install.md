## Step #1: Add the MariaDB Repository

The software-properties-common package should already be installed, but just in case:

`sudo apt-get install software-properties-common`

To find which repo you should use with the [MariaDB repository generator](https://downloads.mariadb.org/mariadb/repositories/). We’re going to add the Ubuntu 14.04 “trusty” `MariaDB 5.5` repository.

We’ll import the MariaDB public key used by the package management system:

`sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db`

Then we’ll add the MariaDB repository:

`sudo add-apt-repository 'deb http://mirror.jmu.edu/pub/mariadb/repo/5.5/ubuntu trusty main'`

Now reload the package database:

`sudo apt-get update`

## Step #2: Install MariaDB

At this point, installing MariaDB is as simple as running just one command:

`sudo apt-get install mariadb-server`

You may receive the following prompt or something similar:

After this operation, 116 MB of additional disk space will be used. Do you want to continue? [Y/n]

Enter Y to continue.

Next you’ll be asked:

New password for the MariaDB “root” user:

This is an administrative account in MariaDB with elevated privileges; enter a strong password.

Then you’ll be asked to verify the root MariaDB password:

Repeat password for the MariaDB “root” user:

That’s it! Your basic MariaDB installation is now complete!

Be sure to stop MariaDB before proceeding to the next step:

`sudo service mysql stop`

## Step #3: Configure and Secure MariaDB for Use

Now we’ll instruct MariaDB to create its database directory structure:

`sudo mysql_install_db`

Start MariaDB:

`sudo service mysql start`

And now let’s secure MariaDB by removing the test databases and anonymous user created by default:

`sudo mysql_secure_installation`

## Step #4: Verify MariaDB Installation

You can check the version of the MariaDB installation with the following command:

`mysql -V`

Enter the MariaDB command client:

`mysql -p`

To stop MariaDB:

`sudo service mysql stop`

To start MariaDB:

`sudo service mysql start`

To check the status of MariaDB:

`sudo service mysql status`

To restart MariaDB:

`sudo service mysql restart`