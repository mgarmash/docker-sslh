# mpeterson/sslh
## Usage
Considering you have SSH listening on port 22 and HTTPS listening on port 443.

```bash
$ sudo docker run -d --name sslh --net=host -p 443:443 -p 127.0.0.1::22 mpeterson/sslh:0.1
```

## Requirements
As it uses the docker host networking feature it needs docker >= 0.11

## Configuration
Configuration options are set by setting environment variables when running the image. What follows it a table of the supported variables:

Variable        | Function
--------------- | -----------------------------------------------------------------------------------------------------------------------------
LISTEN_ADDR     | Address to listen on waiting for new connections. The format is <ip>:<port>. Defaults to: ```0.0.0.0:443```
SSL_TARGET_ADDR | Address to relay when a new SSL (HTTPS) connection is detected. The format is <ip>:<port>. Defaults to: ```$HOST_ADDR:8443```
SSH_TARGET_ADDR | Address to relay when a new SSH connection is detected. The format is <ip>:<port>. Defaults to: ```$HOST_ADDR:22```