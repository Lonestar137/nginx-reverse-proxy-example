
# How to use

1. Start your http service, take note of the IP address that the service is listening on(NOT localhost).

2. Modify the proxy.conf by following the steps listed there.

3. Start the nginx service:
```bash
podman-compose -f podman-compose.yml up -d
# or
docker-compose -f podman-compose.yml up -d
```

4. Go to whatever address you added to your hosts file in your browser, i.e.:

Example hosts file, assuming nginx server is running on localhost.
```conf

127.0.0.1 example.home
```

In browser:
`https://example.home`

## What happened?

We send a request to the Nginx server with the "Host" parameter. The Nginx server checks it's config to see where is this host listening and how should we handle HTTP/S traffic.

Equivalent curl command:
```
curl -H "Host: example.home" localhost
```

This sends an HTTP request to localhost. If Nginx is listening there on port 80, it can read the Param "Host" and redirect to whatever "example.home" is mapped too in the config.
