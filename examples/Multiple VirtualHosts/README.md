Multiple configurations per VirtualHost
------------------
> This folder contains an example of a implementing separate configurations for the PerimeterX Apache module per virtual host.
> Configuration per virtual host is used when a user would like to implement a different set of parameters, such as blocking or monitoring, at a domain or server level. Below is an example of how the configuration will look in your httpd.conf file.

1. Create [multiple VirtualHosts](https://httpd.apache.org/docs/2.4/vhosts/examples.html) in your configuration file
2. Put the following configuration block under every VirtualHost:

```xml
## Site 1 - Active blocking with a score of 80
<VirtualHost *:80>
        DocumentRoot /var/www/html1
        <IfModule mod_perimeterx.c>
                PXEnabled On
                CookieKey my_key1
                AppID my_app_id1
                AuthToken my_auth_token1
                BlockingScore 80
                BlockPageURL /block.html
                ReportPageRequest On
                Captcha On
        </IfModule>
</VirtualHost>

## Site 2 - Monitor mode with a score of 101 and separate account parameters
<VirtualHost *:8080>
        DocumentRoot /var/www/html2
        <IfModule mod_perimeterx.c>
                PXEnabled On
                CookieKey my_key2
                AppID my_app_id2
                AuthToken my_auth_token2
                BlockingScore 101
                ReportPageRequest On
                Captcha Off
        </IfModule>
</VirtualHost>
```
