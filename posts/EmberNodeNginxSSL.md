Ember.js, Node.js and Nginx with SSL
====================================

```
ssl_certificate     /etc/nginx/certs/here.pem;
ssl_certificate_key /etc/nginx/certs/here.key;

server {
  listen 80;
  server_name here.com;
  return 301 https://$server_name$request_uri;
}

server {
  listen 443 ssl spdy;
  server_name here.com;

  root /srv/www/here/dist;
  index index.html;
  access_log /var/log/nginx/here-access.log;
  error_log  /var/log/nginx/here-error.log;

  location / {
    try_files $uri $uri/ /index.html?/$request_uri;
  }

  location /api {
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header HOST $http_host;
    proxy_set_header X-NginX-Proxy true;

    proxy_pass https://127.0.0.1:3000;
    proxy_redirect off;
  }

  # Connection Credential Caching
  ssl_session_cache shared:SSL:20m;
  ssl_session_timeout 10m;

  # Disable SSL
  ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

  # Optimize Cipher Suites
  ssl_prefer_server_ciphers on;
  ssl_ciphers ECDH+AESGCM:ECDH+AES256:ECDH+AES128:DH+3DES:!ADH:!AECDH:!MD5;
  # ssl_ciphers EECDH+ECDSA+AESGCM:EECDH+aRSA+AESGCM:EECDH+ECDSA+SHA256:EECDH+aRSA+SHA256:EECDH+ECDSA+SHA384:EECDH+ECDSA+SHA256:EECDH+aRSA+SHA384:EDH+aRSA+AESGCM:EDH+aRSA+SHA256:EDH+aRSA:EECDH:!aNULL:!eNULL:!MEDIUM:!LOW:!3DES:!MD5:!EXP:!PSK:!SRP:!DSS:!RC4:!SEED;

  # Generated using 'openssl dhparam 2048 -out <file>'
  ssl_dhparam /etc/nginx/cert/dhparam.pem;

  # Enable OCSP Stapling
  ssl_stapling on;
  ssl_stapling_verify on;
  ssl_trusted_certificate /etc/nginx/certs/here-chain.pem;
  resolver 8.8.8.8 8.8.4.4;

  # Strict Transport Security
  add_header Strict-Transport-Security "max-age=31536000; includeSubDomains";
  # add_header Strict-Transport-Security "max-age=31536000";
}
```

http://spdycheck.org/
https://www.ssllabs.com/ssltest/

https://www.mare-system.de/guide-to-nginx-ssl-spdy-hsts/

