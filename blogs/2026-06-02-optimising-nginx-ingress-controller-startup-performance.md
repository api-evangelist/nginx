---
title: "Optimising NGINX Ingress Controller Startup Performance"
url: "https://blog.nginx.org/blog/optimising-nginx-ingress-controller-startup-performance"
date: "2026-06-02"
author: "Venktesh Shivam Patel"
feed_url: "https://blog.nginx.org/feed/"
---
NGINX Ingress Controller 5.5 reduces startup times from several minutes to under 30 seconds by addressing three distinct performance bottlenecks. The team deferred host conflict resolution until after the initial queue drain (reducing O(N2) to O(N) complexity), separated status writes from the critical startup path by batching them asynchronously, and decoupled the readiness signal from status propagation completion. These optimizations deliver significant improvements for large Kubernetes clusters with many ingress resources.
