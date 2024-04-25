# Secure the WebSocket

### Secure a WS Port
A non-secure WS port can be converted to a secure WSS port by placing it behind an SSL-enabled proxy. This can be used to secure a boot node or secure a RPC server. The SSL-enabled apache2/nginx/other proxy server redirects requests to the internal ws and converts it to a secure (wss) connection. For this, you will need an SSL certificate for which you can use a service like lets-encrypt or self-signing.

### Installing a Proxy Server
There are a lot of different implementations of a WebSocket proxy, some of the more widely used are nginx and apache2, for which configuration examples are provided below.

### Nginx
First, install Nginx and Certbot:
```
apt install nginx
```
