# Force-SSL-HTACCESS
Force To HTTPS Compatible With Flexible Cloudflare SSL Crypto in .htaccess file

[Click Here for Download](https://github.com/ariadata/Force-SSL-HTACCESS/raw/master/force_ssl_compatible_cloudflare_flexible.htaccess)

Put These Codes inside Other htaccess Codes in Your Site Root Directory:

```html
# Force To HTTPS Compatible With Cloudflare
RewriteEngine On
RewriteBase /
RewriteCond %{HTTPS} !on
RewriteCond %{SERVER_PORT} !^443$
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L]

#Redirect www to non-www with https
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=301,L]

#Redirect non-www to www with https
#RewriteCond %{HTTP_HOST} ^(?!www\.)(.+) [NC]
#RewriteRule ^(.*) https://www.%1/$1 [R=301,NE,L]
# END


## Another www to non-www with https
RewriteEngine On
RewriteBase /
RewriteCond %{HTTPS} !on
RewriteCond %{SERVER_PORT} !^443$
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L]
RewriteCond %{HTTP_HOST} ^www\.tut98\.ir [NC]
RewriteRule ^(.*)$ https://tut98.ir/$1 [L,R=301]
```
