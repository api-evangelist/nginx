---
title: "Stop Writing Authentication Checks Into Every Service. Combine Them in your Kubernetes Gateway."
url: "https://blog.nginx.org/blog/stop-writing-authentication-checks-into-every-service-combine-them-in-your-kubernetes-gateway"
date: "2026-09-23"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed/"
---
If you run a platform with a dozen or more services behind it, you’ve probably seen this pattern. Service A checks an API key. Service B calls out to your identity provider directly.
