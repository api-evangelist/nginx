---
title: "CORS Policy in NGINX Ingress Controller v5.4.0: Patterns for VirtualServer and Ingress"
url: "https://blog.nginx.org/blog/cors-policy-in-nginx-ingress-controller-v5-4-0-patterns-for-virtualserver-and-ingress"
date: "Tue, 24 Mar 2026 08:59:00 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
<p>Starting with NGINX Ingress Controller (NIC) v5.4.0, you can define CORS behavior once in a <code>Policy</code> resource and apply it consistently across both <code>VirtualServer</code> and <code>Ingress</code> traffic paths.</p>



<p>Across this blog, we’re focused on:</p>



<ul class="wp-block-list">
<li>How CORS policy works in NGINX Ingress Controller.</li>



<li>Where to attach it in <code>VirtualServer</code> and <code>Ingress</code>.</li>
</ul>



<h2 class="wp-block-heading" id="why-use-a-policy-for-cors">Why Use a Policy For CORS?</h2>



<p>Many teams start with per-resource tuning and quickly end up with drift. Using a dedicated <code>Policy</code> for CORS gives you:</p>



<ul class="wp-block-list">
<li>A single source of truth for allowed origins, methods, and headers.</li>



<li>Reuse across services and namespaces.</li>



<li>Cleaner reviews because CORS behavior is isolated from route logic.</li>
</ul>



<h2 class="wp-block-heading" id="how-cors-policy-works-in-nic">How CORS Policy Works in NGINX Ingress Controller</h2>



<p>At a high level:</p>



<ol class="wp-block-list">
<li>Create a <code>Policy</code> resource with <code>spec.cors</code></li>



<li>Attach it where traffic is defined:
<ul class="wp-block-list">
<li><code>VirtualServer.spec.policies</code> (or route/subroute policies)</li>



<li><code>Ingress</code> via the <code>nginx.org/policies</code> annotation</li>
</ul>
</li>



<li>NGINX Ingress Controller renders the corresponding NGINX CORS behavior and returns headers for preflight and actual cross-origin requests.</li>
</ol>



<p>Example CORS Policy:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: k8s.nginx.org/v1
kind: Policy
metadata:
   name: cors-policy
spec:
   cors:
      allowOrigin:
      - https://app.example.com
      allowMethods:
      - GET
      - POST
      - PUT
      - OPTIONS
      allowHeaders:
      - Content-Type
      - Authorization
      - X-Requested-With
      exposeHeaders:
      - X-Total-Count
      - X-Page-Size
      allowCredentials: true
      maxAge: 86400

</pre></div>


<p>Example of VirtualServer referencing above CORS Policy:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: k8s.nginx.org/v1
kind: VirtualServer
metadata:
   name: webapp
spec:
   host: webapp.example.com
   policies:
   - name: cors-policy
   upstreams:
   - name: webapp
      service: webapp-svc
      port: 80
   routes:
   - path: /test
      action:
         pass: webapp

</pre></div>


<p>Example of Ingress referencing above CORS Policy:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: yaml; title: ; notranslate">
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
   name: cafe-ingress
   annotations:
      nginx.org/policies: &quot;cors-policy&quot;
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


<p>Important behavior to remember:</p>



<ul class="wp-block-list">
<li>CORS policy can be applied to both <code>VirtualServer</code> and <code>Ingress</code>.</li>



<li>For <code>VirtualServer</code>, route/subroute policies override same-type policy at spec level.</li>



<li>For credentialed CORS (<code>allowCredentials: true</code>), explicit origins are required.</li>
</ul>



<h2 class="wp-block-heading" id="production-checks-that-prevent-most-issues">Production Checks That Prevent Most Issues</h2>



<p>Before rollout, validate these explicitly:</p>



<ul class="wp-block-list">
<li>Non-allowed origins do not receive <code>Access-Control-Allow-Origin</code>.</li>



<li><code>allowCredentials: true</code> is only used with explicit origins (not <code>*</code>).</li>
</ul>



<h2 class="wp-block-heading" id="security-considerations">Security Considerations</h2>



<p>CORS is a browser enforcement boundary, so keep it tight:</p>



<ul class="wp-block-list">
<li>Use explicit origin allow-lists for production.</li>



<li>Avoid broad method/header lists unless required.</li>



<li>Treat <code>allowCredentials</code> as high trust; use narrowly scoped origins.</li>



<li>Review CORS policy changes with the same care as auth-related config changes.</li>
</ul>



<p>You can find complete working examples on github and more documentation in our <a href="https://docs.nginx.com/nginx-ingress-controller/">docs</a>:</p>



<ul class="wp-block-list">
<li><a href="https://github.com/nginx/kubernetes-ingress/tree/main/examples/custom-resources/cors">CORS Policy example for VirtualServer</a></li>



<li><a href="https://github.com/nginx/kubernetes-ingress/tree/main/examples/ingress-resources/cors">CORS Policy example for Ingress</a></li>



<li><a href="https://docs.nginx.com/nginx-ingress-controller/configuration/policy-resource/#cors">CORS Policy docs</a></li>
</ul>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--7"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
