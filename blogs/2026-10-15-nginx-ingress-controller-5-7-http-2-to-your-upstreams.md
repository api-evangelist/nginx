---
title: "NGINX Ingress Controller 5.7: HTTP/2 to your upstreams, Opaque Secrets, and cert-manager challenges behind HTTPS redirects"
url: "https://blog.nginx.org/blog/nginx-ingress-controller-5-7-http-2-to-your-upstreams-opaque-secrets-and-cert-manager-challenges-behind-https-redirects"
date: "2026-10-15"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
NGINX Ingress Controller 5.7 speaks HTTP/2 to your upstream services, set per upstream or picked up from a Service’s appProtocol. An Opaque Secret now works anywhere a TLS, CA, htpasswd, or API key Secret does, so you can use a Secret created by other tooling as it is. HTTP-01 challenges from cert-manager complete on hosts […]
