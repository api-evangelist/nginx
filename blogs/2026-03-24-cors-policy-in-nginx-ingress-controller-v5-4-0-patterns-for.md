---
title: "CORS Policy in NGINX Ingress Controller v5.4.0: Patterns for VirtualServer and Ingress"
url: "https://blog.nginx.org/blog/cors-policy-in-nginx-ingress-controller-v5-4-0-patterns-for-virtualserver-and-ingress"
date: "Tue, 24 Mar 2026 08:59:00 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed/"
---
Starting with NGINX Ingress Controller (NIC) v5.4.0, you can define CORS behavior once in a Policy resource and apply it consistently across both VirtualServer and Ingress traffic paths. Across this blog, we’re focused on: Why Use a Policy For CORS? Many teams start with per-resource tuning and quickly end up with drift.
