---
title: "NGINX Ingress Controller 5.6: HSTS without snippets, a faster start on large clusters, and improved configuration safety"
url: "https://blog.nginx.org/blog/nginx-ingress-controller-5-6-hsts-without-snippets-a-faster-start-on-large-clusters-and-improved-configuration-safety"
date: "2026-09-02"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed/"
---
NGINX Ingress Controller 5.6 implements more support for configuring NGINX through resources instead of through snippets. HTTP Strict Transport Security (HSTS) becomes a first-class policy across VirtualServer, VirtualServerRoute, and Ingress. Two new annotations close configuration gaps for teams moving off Ingress-NGINX, and the X-Forwarded base headers can now be turned off through the ConfigMap.
