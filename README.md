# TLS client/server example

Generate a self-signed certificate and private key for localhost:

```bash
openssl req -x509 -newkey rsa:2048 -keyout server.key -out server.crt -days 365 -nodes -subj "/CN=localhost"
```

This creates `server.key` and `server.crt`, which are used by `server.py`.

# Network Security Lab

## Snort ICMP Alert Setup

Check the installed Snort version:

```bash
snort -V
```

Edit the Snort configuration:

```bash
sudo nano /etc/snort/snort.conf
```

Set the network variables:

```conf
ipvar HOME_NET any
ipvar EXTERNAL_NET any
```

Add a local ICMP alert rule:

```bash
sudo nano /etc/snort/rules/local.rules
```

Add this rule to the file:

```conf
alert icmp any any -> any any (msg:"ICMP Packet Detected"; sid:1000001; rev:1;)
```

Validate the configuration:

```bash
sudo snort -T -c /etc/snort/snort.conf
```

Inspect the available interfaces and routes:

```bash
ip a
ip route
```

Run Snort in console mode on `eth0`:

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
```

In another terminal, generate an ICMP packet:

```bash
ping 127.0.0.1
```
