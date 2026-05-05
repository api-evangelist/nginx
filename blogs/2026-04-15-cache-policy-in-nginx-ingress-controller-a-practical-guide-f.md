---
title: "Cache Policy in NGINX Ingress Controller: A Practical Guide for VirtualServer"
url: "https://blog.nginx.org/blog/cache-policy-in-nginx-ingress-controller-a-practical-guide-for-virtualserver"
date: "Wed, 15 Apr 2026 22:00:28 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
<p>Caching is one of the fastest ways to reduce backend load and improve response latency in Kubernetes.</p>



<p>With NGINX Ingress Controller (NIC), you can define caching behavior as a first-class <code>Policy</code> resource and attach it to a <code>VirtualServer</code> or <code>VirtualServerRoute</code>. That keeps caching configuration explicit, reusable, and versioned with the rest of your traffic policy.</p>



<p>Across this guide, we’re focused on:</p>



<ul class="wp-block-list">
<li>How the cache policy works in NGINX Ingress Controller.</li>



<li>Where to attach it in <code>VirtualServer</code>.</li>



<li>Why StatefulSet is important for persistent cache use-cases.</li>
</ul>



<h2 class="wp-block-heading" id="why-use-a-cache-policy-resource">Why Use a Cache Policy Resource?</h2>



<p>Putting cache settings in a <code>Policy</code> resource gives platform teams a cleaner separation of concerns:</p>



<ul class="wp-block-list">
<li>Application routing stays in <code>VirtualServer</code>.</li>



<li>Caching behavior lives in a dedicated, reusable policy.</li>



<li>Updates can be rolled out without embedding raw snippets in every route.</li>
</ul>



<p>This model also makes reviews easier because cache behavior is visible in one place.</p>



<h2 class="wp-block-heading" id="how-it-works-in-nic">How the Cache Policy Works in NGINX Ingress Controller</h2>



<p>At a high level:</p>



<ol class="wp-block-list">
<li>Create a <code>Policy</code> with a <code>spec.cache</code> block.</li>



<li>Reference that policy from <code>VirtualServer.spec.policies</code> (server-wide) or from route-level <code>policies</code>.</li>



<li>NGINX Ingress Controller renders the corresponding NGINX cache directives and applies them during config reload.</li>
</ol>



<p>Example Cache Policy:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: plain; title: ; notranslate">
apiVersion: k8s.nginx.org/v1
kind: Policy
metadata:
  name: cache-policy
spec:
  cache:
    cacheZoneName: &quot;testcache&quot; # Required
    cacheZoneSize: &quot;15m&quot; # Required
    allowedCodes: &#x5b;&quot;any&quot;] # Optional &#x5b;&quot;any&quot;] or &#x5b;200, 301, ...], &quot;any&quot; cannot be combined with specific codes
    allowedMethods: &#x5b;&quot;GET&quot;, &quot;HEAD&quot;, &quot;POST&quot;] # Optional
    overrideUpstreamCache: true # Optional, default is false - whether to respect upstream cache-control headers (Cache-Control Expires Set-Cookie Vary X-Accel-Expires)
</pre></div>


<p>Example of VirtualServer referencing above Cache Policy:</p>


<div class="wp-block-syntaxhighlighter-code "><pre class="brush: plain; title: ; notranslate">
apiVersion: k8s.nginx.org/v1
kind: VirtualServer
metadata:
  name: cafe
spec:
  policies:
  - name: cache-policy
  host: cafe.example.com
  tls:
    secret: tls-secret
  upstreams:
  - name: tea
    service: tea-svc
    port: 80
  - name: coffee
    service: coffee-svc
    port: 80
  routes:
  - path: /tea
    action:
      pass: tea
  - path: /coffee
    action:
      pass: coffee
</pre></div>


<p>Important behavior to remember:</p>



<ul class="wp-block-list">
<li>Cache policy is designed for <code>VirtualServer</code> and <code>VirtualServerRoute</code> flows.</li>



<li>If multiple cache policies are referenced for the same effective location, only one is applied (first one wins).</li>



<li>Route-level policies override same-type policies defined at <code>VirtualServer.spec</code>.</li>
</ul>



<h2 class="wp-block-heading" id="key-fields-worth-tuning-first">Key Fields Worth Tuning First</h2>



<p>When you define <code>spec.cache</code>, prioritize these fields first:</p>



<ul class="wp-block-list">
<li><code>cacheZoneName</code> and <code>cacheZoneSize</code>: memory zone identity and capacity.</li>



<li><code>allowedMethods</code>: which methods are cacheable.</li>



<li><code>allowedCodes</code> plus <code>time</code>: what status codes are cached and for how long.</li>



<li><code>cacheKey</code>: request identity for cache lookup.</li>



<li><code>overrideUpstreamCache</code>: whether upstream cache headers should be honored.</li>
</ul>



<p>Then tune advanced behavior only as needed:</p>



<ul class="wp-block-list">
<li><code>cacheUseStale</code>, <code>cacheBackgroundUpdate</code>, and <code>cacheRevalidate</code> for resilience.</li>



<li><code>conditions.noCache</code> and <code>conditions.bypass</code> for selective caching.</li>



<li><code>cachePurgeAllow</code> (NGINX Plus) for controlled invalidation.</li>
</ul>



<h2 class="wp-block-heading" id="cache-at-scale-use-statefulset-for-persistent-cache-workloads">Caching at Scale: Use StatefulSet for Persistent Cache Workloads</h2>



<p>NGINX Ingress Controller supports running the controller as a <code>StatefulSet</code>, which is the better fit for disk-backed cache use-cases. Each replica gets stable storage through a PersistentVolume, which improves cache warm-up behavior after restarts.</p>



<p>For Helm-based deployments, NGINX Ingress Controller explicitly supports this model with:</p>



<ul class="wp-block-list">
<li><code>controller.kind: statefulset</code></li>



<li>StatefulSet-specific <code>nginxCachePVC</code> configuration under <code>controller.statefulset</code></li>
</ul>



<p>You can find a complete working example on github and more documentation in our <a href="https://docs.nginx.com/nginx-ingress-controller/">docs</a>:</p>



<ul class="wp-block-list">
<li><a href="https://github.com/nginx/kubernetes-ingress/tree/main/examples/custom-resources/cache-policy">Cache Policy example (VirtualServer)</a></li>



<li><a href="https://docs.nginx.com/nginx-ingress-controller/configuration/policy-resource/#cache">Cache Policy docs</a></li>
</ul>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--2"><a href="https://go.f5.net/nginxcommunityforum-blogcta" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
