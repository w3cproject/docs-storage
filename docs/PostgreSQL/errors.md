## FATAL: password authentication failed for user "postgres"

If you have this error:

If I remember correctly the user `postgres` has no **DB** password set on Ubuntu by default. That means, that you can login to that account only by using the `postgres` OS user account.

Assuming, that you have `root` access on the box you can do:

`sudo -u postgres psql`

If any of those commands fail with an error `psql: FATAL:  password authentication failed for user "postgres"` then check the file `/etc/postgresql/8.4/main/pg_hba.conf: There must be a line like this as the first non-comment line:

    local   all         postgres                          ident

For newer versions of PostgreSQL `ident` actually might be `peer`. That's OK also.

Inside the `psql` shell you can give the **DB user** `postgres` a password:

```postgresql
ALTER USER postgres PASSWORD 'newPassword';
```