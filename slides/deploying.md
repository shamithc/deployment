####  Deploying Rails App with Phusion Passenger and Nginx

```	
    # Download source code
	cd /tmp
	wget http://nginx.org/download/nginx-1.0.15.tar.gz
	tar -xvzf nginx-1.0.15.tar.gz

	# Install  passenger
	gem install passenger 

	#  configure your Nginx to work with Passenger.
	passenger-install-nginx-module

	# nginx config file 
	sudo nano /opt/nginx/conf/nginx.conf

	# simple configuration
	server { 
		listen 80; 
		server_name example.com; 
		passenger_enabled on; 
		root my-rails-app/public; 
	}
	
```