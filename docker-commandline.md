
#1. Enable UFW forwarding
kiểm tra:
> sudo ufw status

Nếu chưa active:
> ufw enable

Edit file: **/etc/default/ufw**

Set the DEFAULT_FORWARD_POLICY policy to:

```
DEFAULT_FORWARD_POLICY="ACCEPT"
```
reload ufw
> ufw reload

**Allow incoming connections on the Docker port**

> sudo ufw allow 2375/tcp

#2. Configure a DNS server for use by Docker
