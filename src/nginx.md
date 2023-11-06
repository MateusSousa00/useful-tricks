# nginx useful commands

## how to deploy in prod using nginx
- install nginx with apt or apt-get
- if you don't know what nginx.conf is, do not change it
- mv your project to /var/www/html or /var/html
- stop nginx with:
``sudo systemctl stop nginx or sudo service nginx stop``
- create mysite.conf at sites-available like this: ``/etc/nginx/sites-available/mysite.conf``
- this archive must be like this structure:

```
server {
    server_name meusite.com;

    location / {
        proxy_pass http://localhost:3000/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

- save it and link to sites-enabled like this:
```sudo ln -s /etc/nginx/sites-available/mysite.conf /etc/nginx/sites-enabled/``` 
- start nginx
``sudo systemctl start nginx or sudo service nginx start``
- go to the directory where your project remains and do what you gotta do to run it.