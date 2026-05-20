---
title: "Keep-alive to upstreams is now default in NGINX 1.29.7"
url: "https://blog.nginx.org/blog/keep-alive-to-upstreams-is-now-default-in-nginx-1-29-7"
date: "Tue, 24 Mar 2026 14:00:00 +0000"
author: "Buu Lam"
feed_url: "https://blog.nginx.org/feed/"
---
Before version 1.29.7, NGINX used HTTP/1.0 by default for connecting to HTTP upstream servers. This older version of the protocol does not have the capability of HTTP persistent connections, commonly known as “keep-alive.” Keep-alive reduces the number of handshakes, reduces latency, and reduces time to first byte for most regular web applications. In order to […]
