## Basic authentication in virtual hosts

```apacheconfig
<VirtualHost *:80>

    <Directory "/directory/path">
        Deny from all
        #Allow from (You may set IP here / to access without password)
        AuthUserFile /path/to/.htpasswd
        AuthName authorization
        AuthType Basic
        require valid-user
    </Directory>
    ...
</VirtualHost>
```

You can also generate `.htpasswd` file, for new file:

`sudo htpasswd -c /srv/auth/.htpasswd username`

To append to existing file:

`sudo htpasswd -b /srv/auth/.htpasswd username1 username2`