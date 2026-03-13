# Load Balancer

This directory contains scripts for configuring load balancers and web servers for high availability.

## Files

- `0-custom_http_response_header` - Bash script that configures Nginx with a custom HTTP response header (X-Served-By) to track which web server is handling requests.
- `1-install_load_balancer` - Bash script that installs and configures HAproxy on a load balancer server to distribute traffic between web-01 and web-02 using roundrobin algorithm.

## Requirements

- Ubuntu server
- Nginx web server (for web servers)
- HAproxy (for load balancer)
- Bash shell

## Usage

### Configure a web server with the custom header:

```bash
sudo ./0-custom_http_response_header
```

After running the script, you can verify the custom header is working:

```bash
curl -sI <server_ip> | grep X-Served-By
```

This should display something like:
```
X-Served-By: web-01
```

### Install and configure HAproxy load balancer:

```bash
sudo ./1-install_load_balancer
```

After running the script, you can test the load balancer:

```bash
curl -Is <load_balancer_ip>
```

Multiple requests should show different `X-Served-By` headers, alternating between web-01 and web-02 due to roundrobin distribution.
