## /etc/nginx/nginx.conf
http { // içine
```
client_max_body_size 64M;
```

## /etc/php/7.4/fpm/php.ini
```
upload_max_filesize = 64M
post_max_size = 64M
```

## Konsolda
service nginx restart
systemctl restart php7.4-fpm.service
