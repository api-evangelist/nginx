---
title: "Access Control Policy in NGINX Ingress Controller: Patterns for Ingress"
url: "https://blog.nginx.org/blog/access-control-policy-in-nginx-ingress-controller-patterns-for-ingress"
date: "Tue, 07 Apr 2026 20:56:09 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
<p>NGINX Ingress Controller lets you define IP-based access rules once in a <code>Policy</code> resource and apply them consistently across your <code>Ingress</code> traffic paths.</p>



<p>Across this blog, we&#8217;re focused on:</p>



<ul class="wp-block-list">
<li>How Access Control policy works in NGINX Ingress Controller.</li>



<li>Where to attach it in <code>Ingress</code>.</li>



<li>Patterns for allowlists, denylists, and per-route policies.</li>
</ul>



<h2 class="wp-block-heading" id="why-use-a-policy-for-access-control">Why Use a Policy for Access Control?</h2>



<p>Many teams manage IP restrictions through cloud firewalls or raw NGINX config snippets and quickly end up with drift. Using a dedicated <code>Policy</code> for access control gives you:</p>



<ul class="wp-block-list">
<li>A single source of truth for allowed and denied IP ranges.</li>



<li>Reuse across services and namespaces.</li>



<li>Cleaner reviews because access rules are isolated from route logic.</li>



<li>Version-controlled YAML alongside your application code.</li>
</ul>



<h2 class="wp-block-heading" id="how-access-control-policy-works-in-nginx-ingress-controller">How Access Control Policy Works in NGINX Ingress Controller</h2>



<p>At a high level:</p>



<ol class="wp-block-list">
<li>Create a <code>Policy</code> resource with <code>spec.accessControl</code>.</li>



<li>Attach it to an <code>Ingress</code> via the <code>nginx.org/policies</code> annotation.</li>



<li>NGINX Ingress Controller renders the corresponding <code>allow</code>/<code>deny</code> directives. Non-matching requests receive a <code>403 Forbidden</code> response.</li>
</ol>



<h3 class="wp-block-heading" id="allowlist-policy">Allowlist policy</h3>



<p>An <code>allow</code> policy permits only the listed CIDR ranges and rejects everything else:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: k8s.nginx.org/v1
kind: Policy
metadata:
  name: webapp-policy
spec:
  accessControl:
    allow:
    - 10.0.0.0/8
</pre></div>


<h3 class="wp-block-heading" id="denylist-policy">Denylist policy</h3>



<p>A <code>deny</code> policy blocks the listed ranges and permits everything else:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: k8s.nginx.org/v1
kind: Policy
metadata:
  name: webapp-policy-deny
spec:
  accessControl:
    deny:
    - 203.0.113.0/24
</pre></div>


<h3 class="wp-block-heading" id="attaching-to-an-ingress">Attaching to an Ingress</h3>



<p>Reference the policy in the <code>nginx.org/policies</code> annotation:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: cafe-ingress
  annotations:
    nginx.org/policies: &quot;webapp-policy&quot;
spec:
  ingressClassName: nginx
  rules:
  - host: cafe.example.com
    http:
      paths:
      - path: /tea
        pathType: Prefix
        backend:
          service:
            name: tea-svc
            port:
              number: 80
      - path: /coffee
        pathType: Prefix
        backend:
          service:
            name: coffee-svc
            port:
              number: 80
</pre></div>


<p>Multiple policies can be comma-separated:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
annotations:
  nginx.org/policies: &quot;webapp-policy, webapp-policy-deny&quot;
</pre></div>


<p>Important behavior to remember:</p>



<ul class="wp-block-list">
<li>A policy referenced at the Ingress level applies to <strong>all paths</strong> in that resource.</li>



<li>To apply different policies to different routes, use separate <code>Ingress</code> resources for each path (see below).</li>



<li>When combining allow and deny policies, NGINX evaluates them in order.</li>
</ul>



<h2 class="wp-block-heading" id="per-route-policies-with-separate-ingress-resources">Per-Route Policies with Separate Ingress Resources</h2>



<p>When different routes need different access rules, split them into separate <code>Ingress</code> resources. NGINX Ingress Controller merges them into a single configuration.</p>



<p>Locked-down admin route:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: admin-ingress
  annotations:
    nginx.org/policies: &quot;webapp-policy&quot;
spec:
  ingressClassName: nginx
  rules:
  - host: cafe.example.com
    http:
      paths:
      - path: /tea
        pathType: Prefix
        backend:
          service:
            name: tea-svc
            port:
              number: 80
</pre></div>


<p>Public storefront with no policy:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: storefront-ingress
spec:
  ingressClassName: nginx
  rules:
  - host: cafe.example.com
    http:
      paths:
      - path: /coffee
        pathType: Prefix
        backend:
          service:
            name: coffee-svc
            port:
              number: 80
</pre></div>


<h2 class="wp-block-heading" id="real-world-pattern-locking-down-an-admin-dashboard">Real-World Pattern: Locking Down an Admin Dashboard</h2>



<p>A common production pattern combines multiple CIDR ranges to restrict an internal dashboard to corporate and VPN traffic only:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: k8s.nginx.org/v1
kind: Policy
metadata:
  name: admin-only
  namespace: platform
spec:
  accessControl:
    allow:
    - 203.0.113.0/24    # Corporate office network
    - 198.51.100.10/32  # VPN exit node 1
    - 198.51.100.11/32  # VPN exit node 2
</pre></div>

<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: admin-dashboard
  namespace: platform
  annotations:
    nginx.org/policies: &quot;admin-only&quot;
spec:
  ingressClassName: nginx
  rules:
  - host: admin.internal.yourcompany.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: admin-dashboard-svc
            port:
              number: 8080
</pre></div>


<p>This gives you defense in depth: blocked traffic never reaches your application containers, regardless of whether an attacker has valid credentials. Use this same pattern for staging environments, partner webhook endpoints, or per-tenant API restrictions.</p>



<h2 class="wp-block-heading" id="production-checks-that-prevent-most-issues">Production Checks That Prevent Most Issues</h2>



<p>Before rollout, validate these explicitly:</p>



<ul class="wp-block-list">
<li>Non-allowed IPs receive a <code>403</code> and never reach backend pods.</li>



<li>If your cluster sits behind a cloud load balancer or proxy, configure NGINX Ingress Controller to use <code>X-Forwarded-For</code> or PROXY protocol so it sees the real client IP.</li>



<li>Use specific CIDR ranges. A <code>/8</code> covers millions of IPs; prefer <code>/24</code> or <code>/32</code> in production.</li>



<li>When combining allow and deny policies, verify evaluation order matches your intent.</li>
</ul>



<h2 class="wp-block-heading" id="security-considerations">Security Considerations</h2>



<p>Access Control operates at the Ingress edge, so keep it tight:</p>



<ul class="wp-block-list">
<li>Use narrow CIDR ranges; avoid overly permissive allowlists.</li>



<li>Use <code>/32</code> for known single-IP sources like VPN exit nodes.</li>



<li>Layer Access Control with application-level authentication for defense in depth.</li>



<li>Review Access Control policy changes with the same care as auth-related config changes.</li>
</ul>



<p>You can find complete working examples on GitHub and more documentation in our <a href="https://docs.nginx.com/nginx-ingress-controller/">docs</a>:</p>



<ul class="wp-block-list">
<li><a href="https://docs.nginx.com/nginx-ingress-controller/configuration/policy-resource/">Access Control Policy docs</a></li>



<li><a href="https://docs.nginx.com/nginx-ingress-controller/">NGINX Ingress Controller Documentation</a></li>
</ul>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--3"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
