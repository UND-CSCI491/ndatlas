# ndatlas

This project creates and serves a website for the 125 year anniversary of North
Dakota. This website is programmed using HTML, CSS, and JavaScript to
show different maps representing different data throughout North Dakota's
history.

## Server setup

The directions below are for Ubuntu 16.04 LTS.

### Download the code from GitHub
- Install [NodeJS](https://nodejs.org/en/)
 - `sudo apt install npm`
- Clone the [ndatlas repository](https://github.com/UND-CSCI491/ndatlas) to /var/www
 - `cd /var/www`
 - `sudo git clone https://github.com/UND-CSCI491/ndatlas`
- Setup permissions:
 - `cd /var/www`
 - `sudo chown -R root:ndatlas ndatlas`
 - `sudo chmod -R g+w ndatlas`
 - `sudo chmod -R g+s ndatlas`
- Enter the ndatlas repository
 - `cd /var/www/ndatlas`
- Run `npm install` to install all dependencies

### Install NGINX
- Remove Apache as it conflicts with NGINX
 - `sudo apt remove apache2`
- Install NGINX
 - `sudo apt install nginx`
- Copy the ndatlas nginx configuration file
 - `sudo cp /var/www/ndatlas/ndatlas-nginx.conf /etc/nginx/conf.d/ndatlas.conf`
- Remove the index.html to ensure NGINX is installed
 - `sudo rm /var/www/html/index.html`
- Restart NGINX and check to make sure it's working
 - `sudo service nginx restart`
 - Go to [ndatlas.und.edu](http://ndatlas.und.edu) in a browser to see Welcome to nginx

### Setup the NDATLAS service to run the webserver (Ubuntu 15.04 or newer)

- Copy ndatlas.services to the services directory
 - `sudo cp /var/www/ndatlas/ndatlas.conf /lib/systemd/system`

### Setup the NDATLAS service to run the webserver (Ubuntu 14.10 or earlier)

- Copy ndatlas.conf to the services directory
 - `sudo cp /var/www/ndatlas/ndatlas.conf /etc/init/`

### Manually restarting the services

- Manually restart ndatlas when a code change is complete
 - `sudo service ndatlas restart`
- Manually restart nginx when a host has changed
 - `sude service nginx restart`

### Ensure the services autostart

- Restart the server and go to the website to ensure its working
 - `sudo shutdown -r 0`

## Running the development server

A local instance of the server can be ran to see all changes made to the code.
Simply run `node server.js` and you're up and running! To see the website, open a browser and go to [http://localhost:8005](http://localhost:8005).

## Webpages

All the map pages have corresponding JS pages (same name)
