## Before install

`sudo apt-get update`

## Install

`sudo apt-get install postgresql postgresql-contrib`

## Change account to postgres

`sudo -i -u postgres`

## Create new role

```
createuser --interactive

## or with sudo

sudo -u postgres createuser --interactive
```

## Create new database

```
createdb dbname

## or with sudo

sudo -u postgres createdb dbname
```

## Create user

`sudo adduser username`

## Commands

### Change postgres password

```postgresql
ALTER USER postgres PASSWORD 'password';
```
