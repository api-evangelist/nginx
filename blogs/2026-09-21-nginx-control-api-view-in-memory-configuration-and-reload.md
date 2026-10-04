---
title: "NGINX Control API: View In-Memory Configuration and Reload via HTTP Requests"
url: "https://blog.nginx.org/blog/nginx-control-api-view-in-memory-configuration-and-reload-via-http-requests"
date: "2026-09-21"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed/"
---
Before the latest release, NGINX had to be controlled exclusively by Unix signals. The most notable one is SIGHUP or the well-known “nginx -s reload” command. This configuration method, while very stable, does not meet modern environment requirements: there are very few available options, no direct feedback messages on errors, and no real extensibility.
