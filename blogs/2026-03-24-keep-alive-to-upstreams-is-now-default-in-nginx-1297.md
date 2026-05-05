---
title: "Keep-alive to upstreams is now default in NGINX 1.29.7"
url: "https://blog.nginx.org/blog/keep-alive-to-upstreams-is-now-default-in-nginx-1-29-7"
date: "Tue, 24 Mar 2026 14:00:00 +0000"
author: "Buu Lam"
feed_url: "https://blog.nginx.org/feed"
---
<p>Before version 1.29.7, NGINX used HTTP/1.0 by default for connecting to HTTP upstream servers. This older version of the protocol does not have the capability of <strong><a href="https://en.wikipedia.org/wiki/HTTP_persistent_connection%5D">HTTP persistent connections</a></strong>, commonly known as &#8220;keep-alive.&#8221;</p>



<p>Keep-alive reduces the number of handshakes, reduces latency, and
reduces time to first byte for most regular web applications. In order
to enable HTTP/1.1 and switch on the keep-alive behavior for upstream
servers, operators added several directives in their configuration
files. In many cases, this was forgotten, and multiple parts of web
applications ended up working slower than expected.</p>



<p>Commonly used configuration snippet:</p>



<pre class="wp-block-code"><code>proxy_http_version 1.1;
proxy_set_header Connection "";</code></pre>



<p>With version 1.29.7, released in March 2026, we changed the default behavior of HTTP proxying to use HTTP/1.1 with keep-alive.</p>



<p>The above-mentioned configuration lines are now no longer needed.</p>



<h1 class="wp-block-heading" id="downgrading-upstream-connections-to-http10">Downgrading upstream connections to HTTP/1.0</h1>



<p>If your backend servers specifically require HTTP/1.0, you can use the
following configuration lines in the relevant location contexts:</p>



<pre class="wp-block-code"><code>proxy_http_version 1.0;
proxy_set_header Connection "Close";</code></pre>



<h1 class="wp-block-heading" id="new-keepalive-directive-parameter-local">New keepalive directive parameter &#8220;local&#8221;</h1>



<p>When the same upstream block is referenced across multiple locations or
server blocks, requests from those different locations may be
multiplexed over a single TCP connection to the upstream.</p>



<p>This behavior is controlled by the <strong>&#8220;local&#8221;</strong> parameter of the
<strong>keepalive</strong> directive in the upstream context.</p>



<p>Due to backwards compatibility with previous NGINX versions, the default
behavior of this parameter is not obvious. Please read through the
following three options:</p>



<p>1. <strong>Default behavior when no keepalive directive is present:</strong> cached upstream connections are <em style="font-size: revert; display: inline !important;">not</em> shared between locations.</p>



<p>2. <strong>Behavior when the keepalive directive is present without the &#8220;local&#8221; parameter:</strong> cached upstream connections <em style="font-size: revert; display: inline !important;">are</em> shared between locations. This behavior is consistent with previous versions of NGINX:</p>



<pre class="wp-block-code"><code>upstream your-upstream-name {
  keepalive 32;
....
}</code></pre>



<p>3. <strong>Behavior when the keepalive directive is present with the &#8220;local&#8221; parameter:</strong> this is the most explicit setting, with a predictable outcome.</p>



<pre class="wp-block-code"><code>upstream your-upstream-name {
  keepalive 32 local;
....
}</code></pre>



<p>Refer to the official documentation for more details:</p>



<p>&#8211;
<a href="https://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_http_version">https://nginx.org/en/docs/http/ngx_http_proxy_module.html</a></p>



<p>&#8211; <a href="https://nginx.org/en/docs/http/ngx_http_upstream_module.html">https://nginx.org/en/docs/http/ngx_http_upstream_module.html</a></p>



<p>Use the &#8220;Discussions&#8221; section of our official repository for feedback:
<a href="https://github.com/nginx/nginx/discussions">https://github.com/nginx/nginx/discussions</a></p>



<p>Follow the upcoming code changes and development conversations:
<a href="https://github.com/nginx/nginx/pulls">https://github.com/nginx/nginx/pulls</a></p>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--6"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
