```azure
## What are ports?
ports are numerical identifiers used to direct network traffic to specific applications or services running on a device within a network, enabling efficient and organized communication. In the context of computer networking, a port allows communication between different programs or services running on a computer. 

A port is identified by a 16-bit number, ranging from 0 to 65535. The first 1024 port numbers, known as well-known ports or system ports, are typically reserved for specific services. For example, port 80 is commonly used for HTTP (Hypertext Transfer Protocol) web traffic, and port 443 is used for secure HTTPS (HTTP Secure) connections.
```

```azure
## What is a reverse proxy? How is it different to a proxy?

A reverse proxy is a server that acts as an intermediary between client devices and one or more servers. It receives requests from clients and forwards them to the appropriate backend server to fulfill those requests. The response from the server is then sent back to the client through the reverse proxy.

The main difference between a reverse proxy and a regular proxy lies in the direction of the communication flow. In a regular proxy setup, the client sends requests to the proxy server, which then forwards those requests to the destination server. The proxy server acts on behalf of the client, and the server's response is sent back to the proxy and then to the client.

## What are the benefits of an Nginx reverse proxy setup?

The benefits of using Nginx as a reverse proxy include:

1. Clients access all backend resources through a single web address.
2. The reverse proxy can serve static content, which reduces the load on application servers such as Express, Tomcat or WebSphere.
3. The Nginx reverse proxy can navigate through firewalls that protect backend resources.
4. The reverse proxy can act as a cache or buffer to reduce latency.
5. User access control is greatly simplified with a single point of access to your site.

(SSL (Secure Sockets Layer) encryption, and its more modern and secure replacement, TLS (Transport Layer Security) encryption, protect data sent over the internet or a computer network.)

```

```azure
### Make a diagram for the above point to go with your explanation.

```

```azure


### What is Nginx's default configuration?
```

```azure
### How do you set up a Nginx reverse proxy?

### Setting Up Nginx as a Reverse Proxy:

---> Nginx reverse proxy configuration steps
Follow these steps to setup and configure an Nginx reverse proxy server of your own:

1. Install Nginx on your Windows or Linux server (prerequisite).

2. Add the Nginx proxy_pass setting in a virtual host or the default config file.

3. Map a context root to the URL of a backend server.

4.Optionally set headers for the Nginx reverse proxy to use with the backend.

5. Restart Nginx reverse proxy and test the reverse proxy setup.

## Setting Up Nginx as a Reverse Proxy Server

### Install Nginx
On Ubuntu, install the latest version of Nginx.

sudo apt-get update -y
Reading package lists... Done
sudo apt-get upgrade -y
Calculating upgrade... Done
sudo apt-get install nginx -y
The following Nginx packages will be installed on Ubuntu 22:
libnginx-mod-http-geoip2 nginx-common nginx-core nginx-proxy
Setting up nginx 1.18 ubuntu 22... Done

In the default file we need to change the line in location starting with:

try_files $uri $uri/ =404;

for

proxy_pass http://localhost:3000;

In here then add in the location / {}

 proxy_pass http://20.0.224.25:3000/;

after that we need to restart nginx:

sudo systemctl restart nginx

### Manually using reverse proxy to redirect to port 3000

# got nginx config file and edit location

sudo nano /etc/nginx/sites-available/default

```

### Reverse Proxy
sudo nano /etc/nginx/sites-available/default

change the line:
try_files $uri $uri/ =404;

to the following:

proxy_pass http://localhost:3000;

Save and exit nano, then sudo nginx -t to test it

restart nginx
sudo systemctl restart nginx

Paste the app VM ip in the browser to check if it works.
