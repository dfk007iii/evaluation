  
server {  
    listen **8006**;  
    server\_name **49.13.23.4**;  

    root **/home/frontend/dist/;**  
    index index.html;

    location / {  
        try\_files $uri $uri/ \=404;  
    }

    error\_page 500 502 503 504 /50x.html;  
    location \= /50x.html {  
        root /usr/share/nginx/html;  
    }  
}

server {  
    listen **8007**;  
    server\_name **49.13.23.4;**

    root **/home/SourceConnector/unifydata/public;**  
    **index index.php index.html index.htm;**

    location / {  
        try\_files $uri $uri/ /index.php?$query\_string;  
    }

    location \~ \\.php$ {  
        include snippets/fastcgi-php.conf;  
        fastcgi\_pass unix:/var/run/php/php8.2-fpm.sock;  
    }

    location \~ /\\.ht {  
        deny all;  
    }  
}

