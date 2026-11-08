# TLS client/server example

Generate a self-signed certificate and private key for localhost:

```bash
openssl req -x509 -newkey rsa:2048 -keyout server.key -out server.crt -days 365 -nodes -subj "/CN=localhost"
```

This creates `server.key` and `server.crt`, which are used by `server.py`.
