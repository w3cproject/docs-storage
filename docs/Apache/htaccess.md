## Change document root folder

```apacheconfig
    RewriteEngine on
    RewriteCond %{HTTP_HOST} ^domain-name.com$ [NC,OR]
    RewriteCond %{HTTP_HOST} ^www.domain-name.com$
    RewriteCond %{REQUEST_URI} !folder/
    RewriteRule (.*) /folder/$1 [L]
```

- `domain-name.com` - Type your own domain name

- `folder` - Type the name of the sub-folder which has the test/development website

## Redirect from root folder to subfolder

`RewriteRule ^$ /site [L]`

don't forget about use it:

```apacheconfig
    Options +FollowSymLinks
    RewriteEngine On
```