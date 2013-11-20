###  Nginx.conf

```nginx
user  user1
worker_processes  1;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  1024;
}


http {
    passenger_root /home/user/.rvm/gems/ruby-1.9.3-p194/gems/passenger-3.0.18;
    passenger_ruby /home/user/.rvm/wrappers/ruby-1.9.3-p194/ruby;

    include       mime.types;
    default_type  application/octet-stream;

    #access_log  logs/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;

    server {
        listen 80;
        server_name  localhost;
        root /home/user/BBC-v3.1/BBC/trunk/BBC/public;
	    passenger_enabled on;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        #location / {
        #    root   html;
        #    index  index.html index.htm;
        #}

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

	      location /sign_up {
		      proxy_pass  http://localhost:8080/;	
  	   }

       location /homes/bbc_signup {
          proxy_pass  http://localhost:8080/homes/bbc_signup; 
       }

       location /success_signup {
          proxy_pass  http://localhost:8080/homes/sucess_signup;
       }
  
       location ~ ^/(assets-suscription)/  {
          root /home/user/BBC-v3.1/BBC/trunk/BBC-SubscriptionApp/public ;
          expires max;
          break;
       }   
    }
}
```

