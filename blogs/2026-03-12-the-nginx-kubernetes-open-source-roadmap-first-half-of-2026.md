---
title: "The NGINX Kubernetes Open Source Roadmap: First Half of 2026"
url: "https://blog.nginx.org/blog/the-nginx-kubernetes-open-source-roadmap-first-half-of-2026"
date: "Thu, 12 Mar 2026 22:03:03 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
<p>Hello to our Kubernetes community! Over the past few months, the F5 NGINX Community and F5 NGINX Kubernetes teams have been working on reinvigorating our open source presence. One of our new initiatives involves having public roadmaps available through GitHub Projects boards for both the <a href="https://github.com/orgs/nginx/projects/16/views/2">NGINX Ingress Controller</a> and <a href="https://github.com/orgs/nginx/projects/10/views/5">NGINX Gateway Fabric</a> project! We also aim to publish roadmap update blogs twice a year to talk about our roadmap more in depth. Here at F5 we believe you should know what we&#8217;re building next and why, so you can plan any future Kubernetes decisions with that context and let us know any feedback you have about the roadmap through any of our community channels!</p>



<p>Here&#8217;s where both projects are headed in in the first half of 2026.</p>



<hr class="wp-block-separator has-alpha-channel-opacity" />



<h2 class="wp-block-heading" id="nginx-ingress-controller-listening-to-the-community">NGINX Ingress Controller: Listening to the Community</h2>



<p>The NGINX Ingress Controller uses the Ingress API by default, the same as any other Ingress Controller. NGINX Ingress Controller also has a CRD-based configuration model that gives operators structured, validated control over their ingress. It&#8217;s been running in production clusters for years, and it&#8217;s not slowing down.</p>



<p>We&#8217;ve heard the community, and over the next few releases, we are prioritizing bringing features that <code>ingress-nginx</code> users depend on into NGINX Ingress Controller. We are extending our support for <code>ingress-nginx</code> annotations with 1-to-1 mappings, external auth support lands in the next major NGINX Ingress Controller release, and session persistence will be coming to NGINX Ingress Controller later this year. In addition, we will be launching a comprehensive migration guide from <code>ingress-nginx</code> to NGINX Ingress Controller within the next couple weeks, as well as a community landing page covering all of our Kubernetes efforts.</p>



<h3 class="wp-block-heading" id="expanding-ingress-nginx-annotation-compatibility">Expanding <code>ingress-nginx</code> Annotation Compatibility</h3>



<p>One of the most consistent requests we&#8217;ve gotten is broader compatibility with ingress-nginx annotations. If you&#8217;re migrating NGINX Ingress Controller, you shouldn&#8217;t have to rewrite your ingress configuration from scratch. We&#8217;ve been working on this steadily, and the list of supported annotations has grown fast. Over the next few releases we plan to keep adding support for <code>ingress-nginx</code> annotations.</p>



<p><strong><code>ingress-nginx</code> annotations that will be supported as <code>nginx.org</code> annotations in our next major release:</strong></p>



<ul class="wp-block-list">
<li><code>nginx.ingress.kubernetes.io/app-root</code></li>



<li><code>nginx.ingress.kubernetes.io/client-body-buffer-size</code></li>



<li><code>nginx.ingress.kubernetes.io/force-ssl-redirect</code></li>



<li><code>nginx.ingress.kubernetes.io/next-upstream</code></li>



<li><code>nginx.ingress.kubernetes.io/next-upstream-timeouts</code></li>



<li><code>nginx.ingress.kubernetes.io/next-upstream-tries</code></li>



<li><code>nginx.ingress.kubernetes.io/rewrite-target</code></li>



<li><code>nginx.ingress.kubernetes.io/ssl-ciphers</code></li>



<li><code>nginx.ingress.kubernetes.io/ssl-redirect</code></li>
</ul>



<p><strong><code>ingress-nginx</code> annotations that will be supported as <code>nginx.org</code> annotations when combined with our Policy CRD in our next major release:</strong></p>



<ul class="wp-block-list">
<li><code>nginx.ingress.kubernetes.io/enable-cors</code></li>



<li><code>nginx.ingress.kubernetes.io/whitelist-source-range</code></li>
</ul>



<p><strong><code>ingress-nginx</code> annotations that are on the roadmap and <strong>will be supported as <code>nginx.org</code> annotations</strong> down the line:</strong></p>



<ul class="wp-block-list">
<li><code>nginx.ingress.kubernetes.io/add-header</code></li>



<li><code>nginx.ingress.kubernetes.io/custom-http-errors</code></li>



<li><code>nginx.ingress.kubernetes.io/proxy-http-version</code></li>



<li><code>nginx.ingress.kubernetes.io/proxy-redirect-from</code></li>
</ul>



<p><strong><strong><code>ingress-nginx</code> annotations that are on the roadmap and will be supported as <code>nginx.org</code> annotations when combined with our Policy CRD down the line:</strong></strong></p>



<ul class="wp-block-list">
<li><code>nginx.ingress.kubernetes.io/auth-signin</code></li>



<li><code>nginx.ingress.kubernetes.io/auth-url</code></li>



<li><code>nginx.ingress.kubernetes.io/auth-tls-verify-client</code></li>



<li><code>nginx.ingress.kubernetes.io/auth-tls-secret</code></li>



<li><code>nginx.ingress.kubernetes.io/auth-tls-verify-depth</code></li>
</ul>



<p>It&#8217;s worth noting that all of the above annotations will use the NGINX Ingress Controller annotation standards and replace the <code>nginx.ingress.kubernetes.io/</code> annotation prefix with <code>nginx.org/</code>, (or <code>nginx.org/policies</code> when used combined with our Policy CRD). In addition, we are also planning to add new annotations that we think are complimentary to existing NGINX directives such as <code>ssl-redirect-return-code</code>, to be used in conjunction with <code>ssl-redirect</code>! </p>



<p>For more information on how to use these annotations and how <code>ingress-nginx</code> annotations match to <code>nginx.org</code> annotations, check out our <a href="https://docs.nginx.com/nginx-ingress-controller/install/migrate-ingress-nginx/#advanced-configuration-with-annotations">docs</a>! These will be updated as new releases come out.</p>



<h3 class="wp-block-heading" id="improved-resiliency-and-expanded-features">Improved Resiliency and Expanded Features</h3>



<p>Beyond annotations, we have a few features coming in the first half of the year focused on improving the overall resiliency of NGINX Ingress Controller as well as implementing key features such as external auth and session persistence that will heavily facilitate users migrating from <code>ingress-nginx</code> to NGINX Ingress Controller:</p>



<p><strong>Configuration resilience (aka &#8220;safety&#8221;):</strong> Improve how NGINX Ingress Controller handles bad or conflicting configurations. If someone applies a broken config, NGINX Ingress Controller should handle it gracefully instead of taking down your routes.</p>



<p><strong>Rate limiting based on NGINX variables:</strong> Rate limiting will let you key rate limits off headers, client attributes, or custom variables, not just IP addresses.</p>



<p><strong>Cache Policy and StatefulSet support:</strong> Native caching policy and StatefulSet deployment options are coming to NGINX Ingress Controller.</p>



<p><strong>New annotations combined with CRDs for external auth and CORS:</strong> External auth is one of the most requested features from teams migrating off <code>ingress-nginx</code> and we are working on getting this out as soon as possible!</p>



<p><strong>Session persistence (sticky sessions) moves to NGINX Open Source:</strong> Session persistence (via sticky sessions) was previously commercial-only. If you&#8217;re running stateful workloads (shopping carts, multi-step forms, authentication flows), you&#8217;ll no longer need NGINX Plus for sticky sessions. This change is also coming to NGINX Ingress Controller!</p>



<p><strong>Cross Namespace support:</strong> Route traffic to services across namespace boundaries.</p>



<p><strong>Argo Rollouts deployment option:</strong> Support for progressive delivery workflows with Argo.</p>



<p><strong>Availability in Nutanix Kubernetes Platform:</strong> Nutanix and F5 join forces to deliver NGINX Ingress Controller running on the Nutanix Kubernetes Platform (NKP) solution.</p>



<h3 class="wp-block-heading" id="looking-further-ahead">Looking Further Ahead</h3>



<p>We also have a few items on the roadmap slated for the second half of 2026 that we thought might be of interest to the community! None of these features are confirmed and things might change over the new few months, but we&#8217;re exploring implementing the following features starting later this year:</p>



<ul class="wp-block-list">
<li>HSTS Policy and HTTP/2 to service.</li>



<li>Scoped Ingress Controller deployments with namespace isolation, a frequently requested feature for multi-tenant clusters.</li>



<li>Advanced caching.</li>



<li>Forward proxy support and native MQTT protocol handling move to Open Source and come to NGINX Ingress Controller.</li>



<li>GeoIP-based routing and hot reload without dropping connections.</li>



<li>Bringing our Images back to the cloud marketplaces!</li>



<li>Sharded cache cluster support (split a cache across multiple volumes!)</li>
</ul>



<hr class="wp-block-separator has-alpha-channel-opacity" />



<h2 class="wp-block-heading" id="nginx-gateway-fabric-gateway-api-native-and-ai-ready">NGINX Gateway Fabric: Continuous Evolution</h2>



<p>NGINX Gateway Fabric (NGF) is the Gateway API-native Kubernetes solution from NGINX. Recent releases delivered TCP/UDP routing, rate limiting, and the <code>ingress2gateway</code> migration provider. Now the focus shifts to core traffic management gaps and, increasingly, AI infrastructure.</p>



<h3 class="wp-block-heading" id="already-delivered">Gateway API-Native and AI-Ready</h3>



<p>Over the past few releases, NGINX Gateway Fabric has added support for the following features:</p>



<p><strong>Gateway API Inference Extension:</strong> NGINX Gateway Fabric can serve as a gateway for AI model endpoints. You manage model routing through the same Gateway API resources you use for everything else.</p>



<p><strong>Red Hat OpenShift Certification:</strong> NGINX Gateway Fabric has become an officially supported option for OpenShift environments.</p>



<p><strong>TCPRoute and UDPRoute Support:</strong> Users can consolidate traffic management into a single Gateway API workflow instead of deploying separate load balancers for non HTTP services.</p>



<p><strong>Authentication via AuthenticationFilter CRD:</strong> The new AuthenticationFilter adds HTTP Basic Auth, allowing you to protect routes with credentials. Future releases will extend AuthenticationFilter beyond the baseline with additional methods available.</p>



<p><strong>RateLimit Policy CRD:</strong> Enhanced traffic control with a new RateLimitPolicy CRD, enabling HTTP rate limiting directly through Gateway API.</p>



<p><strong>Regex-based path matching, redirects, header modification, and NGINX Snippets:</strong> Fill traffic shaping gaps that power users have been asking for.</p>



<p><strong>Routing to external services:</strong> Use ExternalName, plus customizable logging and basic auth filters.</p>



<p><strong>mTLS and cipher configuration:</strong> The Gateway API and a new TLS Options resource give operators finer control over transport security.</p>



<h3 class="wp-block-heading" id="looking-further-ahead-1">Looking Further Ahead</h3>



<p>Over the next few months, we are hoping to add support for the following features:</p>



<ul class="wp-block-list">
<li>External auth and CORS.</li>



<li>Session persistence moves to open source (same as NGINX Ingress Controller).</li>



<li>HTTP/2 to backend services, which improves performance for gRPC workloads.</li>



<li>MCP (Model Context Protocol) and A2A (Agent-to-Agent) support. These protocols are how AI agents discover tools and talk to each other. Native gateway support means no custom middleware between your agents and the rest of your stack.</li>



<li>Forward proxy, east/west traffic control, and egress control, pushing NGINX Gateway Fabric beyond traditional north/south ingress.</li>



<li>Caching and gzip compression.</li>



<li>API key auth and access control (whitelisting).</li>
</ul>



<h2 class="wp-block-heading" id="what-ties-it-all-together">What Ties It All Together</h2>



<p>A few things stand out across both projects.</p>



<p><strong>Open source is at the heart of both projects.</strong> The NGINX Ingress Controller and NGINX Gateway Fabric communities are growing, and so is our commitment to building avenues for connection. From your feedback to your questions to your PRs, we love hearing from you.</p>



<p><strong>We develop in the open.</strong> Both the NGINX Ingress Controller and NGINX Gateway Fabric teams have public project boards on GitHub and regularly host community calls. We want our users to know what we are actively working on, see how we triage issues and PRs, and answer any questions they might have around our projects.</p>



<p><strong>Community feedback is driving our roadmaps.</strong> The ingress-nginx annotation compatibility work, the new CRDs (external auth and CORS), and the open-sourcing of session persistence all came directly from what users have been telling us. That feedback loop is working, and we want to keep it going.</p>



<p><strong>AI workloads are shaping our direction.</strong> The Gateway API Inference Extension, MCP, and A2A support reflect the reality that inference traffic needs the same routing, rate limiting, and session management as any other workload. GPU resources are expensive, and intelligent routing at the gateway helps you use them efficiently.</p>



<p><strong>We are actively exploring open sourcing commercial features where possible.</strong> Our second foray (after open sourcing service discovery) is open sourcing session persistence (via sticky sessions) across the board. Both NGINX Ingress Controller and NGINX Gateway Fabric are getting this. It was previously commercial-only, and we think making it freely available is the right call. We also plan on open sourcing forward proxying and MQTT further down the line.</p>



<p><strong>NGINX Ingress Controller and NGINX Gateway Fabric are complementary, not competing.</strong> NGINX Ingress Controller continues to evolve its CRD model with new resource types. NGINX Gateway Fabric is built entirely on Gateway API. If you&#8217;re on CRDs today, NGINX Ingress Controller has a clear path forward. If you&#8217;re adopting Gateway API, NGINX Gateway Fabric is ready. And if you&#8217;re planning a move from one to the other, we&#8217;re building tooling to make that easier too.</p>



<hr class="wp-block-separator has-alpha-channel-opacity" />



<h2 class="wp-block-heading" id="get-involved">Get Involved</h2>



<p>This is the first time we&#8217;ve published a roadmap like this, and we plan to keep doing it! If you have feedback or want to influence what gets prioritized, here&#8217;s where to find us:</p>



<ul class="wp-block-list">
<li><a href="https://community.nginx.org">NGINX Community Forum</a></li>



<li><a href="https://github.com/nginx/kubernetes-ingress">NGINX Ingress Controller on GitHub</a> | <a href="https://github.com/orgs/nginx/projects/16/views/2">NGINX Ingress Controller Roadmap GitHub Board</a></li>



<li><a href="https://github.com/nginx/nginx-gateway-fabric">NGINX Gateway Fabric on GitHub</a> | <a href="https://github.com/orgs/nginx/projects/10/views/5">NGINX Gateway Fabric Roadmap GitHub Board</a></li>



<li><a href="https://github.com/nginx/kubernetes-ingress?tab=readme-ov-file">NGINX Ingress Controller Community Calls</a></li>



<li>NGINX Gateway Fabric Community Meetings: <a href="https://community.nginx.org/t/nginx-gateway-fabric-community-meetings-amer-hours/9066?u=heo">AMER</a> | <a href="https://community.nginx.org/t/nginx-gateway-fabric-community-meetings-emea-hours/9081?u=heo">EMEA</a></li>
</ul>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--10"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
