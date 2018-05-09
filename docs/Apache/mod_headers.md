## Header Access Control

If you have errors like a:

    No 'Access-Control-Allow-Origin' header is present on the requested resource.
    
    The value of the 'Access-Control-Allow-Credentials' header in the response is '' which must be 'true' when the request's credentials mode is 'include'.
    
    The value of the 'Access-Control-Allow-Origin' header in the response must not be the wildcard '*' when the request's credentials mode is 'include'

add into mod_headers section

```apacheconfig
<IfModule mod_headers.c>
    Header set Access-Control-Allow-Origin http://your.site.ru
    Header set Access-Control-Allow-Credentials true
</IfModule>
```

[Source stackoverflow](https://stackoverflow.com/a/13871027/6607814)