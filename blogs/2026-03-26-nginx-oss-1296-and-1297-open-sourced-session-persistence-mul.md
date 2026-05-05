---
title: "NGINX OSS 1.29.6 and 1.29.7: Open-sourced Session Persistence, Multipath TCP and More"
url: "https://blog.nginx.org/blog/nginx-oss-1-29-6-and-1-29-7-open-sourced-session-persistence-multipath-tcp-and-more"
date: "Thu, 26 Mar 2026 17:00:20 +0000"
author: "Hannah Ouellette"
feed_url: "https://blog.nginx.org/feed"
---
<p>NGINX 1.29.6&nbsp;and 1.29.7&nbsp;introduce&nbsp;significant&nbsp;updates and mark the first in a planned series to add capabilities to NGINX&nbsp;Open&nbsp;Source formerly limited to&nbsp;NGINX Plus.&nbsp;With updates to&nbsp;core runtime behavior and network support, these releases&nbsp;ensure&nbsp;that&nbsp;NGINX can continue to meet the needs of modern applications and AI workloads.&nbsp;</p>



<p><strong>Highlights of&nbsp;these&nbsp;releases&nbsp;include:&nbsp;</strong></p>



<div class="wp-block-group has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<ul class="wp-block-list">
<li>Open sourced&nbsp;sticky cookie session persistence&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Upstream proxy connections&nbsp;now default to&nbsp;HTTP/1.1&nbsp;and&nbsp;no longer require&nbsp;explicitly&nbsp;configured&nbsp;keep-alives&nbsp;and connection headers&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Multipath TCP (MPTCP) support&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Several important security-related fixes&nbsp;</li>
</ul>
</div>



<p>Together, these changes expand what operators can do with&nbsp;NGINX&nbsp;Open&nbsp;Source&nbsp;while&nbsp;simplifying&nbsp;configurations for&nbsp;optimizing&nbsp;performance&nbsp;to proxied services.&nbsp;</p>



<p class="has-large-font-size">Open Sourced&nbsp;Sticky Cookies for Session Persistence&nbsp;</p>



<p>NGINX 1.29.6 adds support for&nbsp;<a href="https://nginx.org/en/docs/http/ngx_http_upstream_module.html#sticky" rel="noreferrer noopener" target="_blank">cookie-based session persistence</a>&nbsp;to open source, a capability previously only&nbsp;available commercially&nbsp;in&nbsp;NGINX Plus.&nbsp;</p>



<p>Sticky cookies allow NGINX to issue a session cookie and route&nbsp;subsequent&nbsp;requests from that client to the same upstream server. Unlike IP-based affinity methods, cookie persistence avoids issues introduced by NAT, mobile networks, carrier-grade proxies, or large-scale edge routing.&nbsp;</p>



<p><strong>Example configuration:&nbsp;</strong></p>



<p class="has-base-2-background-color has-background" style="border-width: 1px;"><code>upstream backend {&nbsp;<br />&nbsp;&nbsp;&nbsp;server backend1.example.com;&nbsp;<br />&nbsp;&nbsp;&nbsp;server backend2.example.com;&nbsp;<br />&nbsp;<br />&nbsp;&nbsp;&nbsp;sticky cookie&nbsp;srv_id&nbsp;expires=1h domain=.example.com path=/;&nbsp;<br />}&nbsp;</code></p>



<p><strong>Why it matters</strong>:&nbsp;</p>



<div class="wp-block-group has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<ul class="wp-block-list">
<li>Many production workloads still rely on in-memory session state&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Stateless design is not always&nbsp;immediately&nbsp;achievable&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Cookie-based persistence provides deterministic routing without requiring external session stores or application refactoring&nbsp;</li>
</ul>
</div>



<p><strong>Who it helps</strong>:&nbsp;</p>



<ul class="wp-block-list">
<li>E-commerce platforms&nbsp;maintaining&nbsp;transactional continuity&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Real-time dashboards and WebSocket applications&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Enterprises modernizing legacy stateful services&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Platform teams that need controlled session affinity in Kubernetes or VM environments&nbsp;</li>
</ul>



<p class="has-large-font-size">Default to HTTP/1.1 for Upstream Connections&nbsp;</p>



<p>NGINX&nbsp;1.29.7&nbsp;now defaults to HTTP/1.1 when&nbsp;proxying to&nbsp;upstreams.&nbsp;</p>



<p>HTTP/1.1 enables persistent upstream connections&nbsp;via&nbsp;keep-alives, chunked transfer encoding, and broader compatibility with modern application frameworks.&nbsp;Learn more about this change in&nbsp;our <a href="https://blog.nginx.org/blog/keep-alive-to-upstreams-is-now-default-in-nginx-1-29-7" rel="noreferrer noopener" target="_blank">dedicated post on this topic</a>.&nbsp;</p>



<p><strong>Why it matters</strong>:&nbsp;</p>



<ul class="wp-block-list">
<li>Operators no longer need to explicitly configure HTTP/1.1,&nbsp;enable&nbsp;keep-alives&nbsp;and remove connection headers&nbsp;when routing traffic to&nbsp;upstreams&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Backend interoperability issues are reduced&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Default behavior aligns with modern framework expectations&nbsp;</li>
</ul>



<p><strong>Who it helps</strong>:&nbsp;</p>



<ul class="wp-block-list">
<li>Teams running modern frameworks that expect persistent connections&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Operators troubleshooting inconsistent upstream behavior&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Platform teams standardizing proxy behavior across environments&nbsp;</li>
</ul>



<p class="has-large-font-size">Multipath TCP (MPTCP) Support&nbsp;</p>



<p>NGINX 1.29.7&nbsp;adds&nbsp;<a href="https://nginx.org/en/docs/http/ngx_http_core_module.html#listen" rel="noreferrer noopener" target="_blank">support for Multipath TCP</a>&nbsp;(MPTCP).&nbsp;MPTCP allows a single TCP connection to use multiple network paths simultaneously, improving resilience and throughput in multi-homed or heterogeneous network environments.&nbsp;</p>



<p><strong>Why it matters</strong>:&nbsp;</p>



<ul class="wp-block-list">
<li>Applications&nbsp;benefit&nbsp;from improved reliability without modification&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Transport-layer resilience increases as kernel-level MPTCP support matures&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Infrastructure performance improves across heterogeneous networks&nbsp;</li>
</ul>



<p><strong>Who it helps</strong>:&nbsp;</p>



<ul class="wp-block-list">
<li>Edge and mobile deployments with variable connectivity&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Multi-interface servers in high-availability configurations&nbsp;</li>
</ul>



<ul class="wp-block-list">
<li>Infrastructure teams optimizing network resilience&nbsp;</li>
</ul>



<p class="has-large-font-size">A Deliberate Direction&nbsp;</p>



<p>NGINX 1.29.6&nbsp;and 1.29.7&nbsp;represent&nbsp;our continued effort to&nbsp;align&nbsp;NGINX&nbsp;Open&nbsp;Source&nbsp;more closely with modern&nbsp;application&nbsp;requirements.&nbsp;Over the&nbsp;next several&nbsp;months,&nbsp;we will continue to&nbsp;release more commercial features as&nbsp;open source&nbsp;and,&nbsp;while&nbsp;subject to change, we&nbsp;have made these&nbsp;and other&nbsp;plans public in our new&nbsp;<a href="https://github.com/orgs/nginx/projects/34/views/1" rel="noreferrer noopener" target="_blank">Github&nbsp;roadmap</a>.&nbsp;</p>



<p>Capabilities made available in NGINX 1.29.6&nbsp;and 1.29.7, along with&nbsp;several&nbsp;bug and security fixes, mean that&nbsp;NGINX&nbsp;Open&nbsp;Source&nbsp;is now&nbsp;even&nbsp;more&nbsp;performant and&nbsp;production-ready.&nbsp;We encourage you to upgrade&nbsp;to&nbsp;NGINX 1.29.7 to&nbsp;take advantage of all the new features and&nbsp;ensure that&nbsp;you’re&nbsp;protected by all the latest&nbsp;security patches.&nbsp;</p>



<p>View all updates and fixes in GitHub:&nbsp;&nbsp;</p>



<p>1.29.6 -&gt;&nbsp;<a href="https://github.com/nginx/nginx/releases/tag/release-1.29.6" rel="noreferrer noopener" target="_blank">https://github.com/nginx/nginx/releases/tag/release-1.29.6</a>&nbsp;</p>



<p>1.29.7 -&gt;&nbsp;<a href="https://github.com/nginx/nginx/releases/tag/release-1.29.7" rel="noreferrer noopener" target="_blank">https://github.com/nginx/nginx/releases/tag/release-1.29.7</a>&nbsp;</p>



<p><a href="https://nginx.org/en/download.html" rel="noreferrer noopener" target="_blank">Download NGINX</a>&nbsp;and view the full&nbsp;<a href="https://nginx.org/en/CHANGES" rel="noreferrer noopener" target="_blank">changelog</a>.&nbsp;</p>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--5"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
