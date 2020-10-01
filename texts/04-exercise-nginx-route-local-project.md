# Exercise

The exercise consists in creating a nginx route for a local project

# Project

Spring boot initializer was used. Just added web dependencie and

> mvn install
> mvn spring-boot:run

That created a error page in http://localhost:8080

# Hosts

In /etc/hosts file, I added a line

127.0.0.1    meuprojeto.com.br

# Nginx

Inside the folder /etc/nginx/sites-enabled, I created a new file called meuprojeto.conf and the content of it is:

```
server {
    listen 80;
    listen [::]:80;
    index index.html index.htm;
    server_name meuprojeto.com.br;

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host localhost;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```