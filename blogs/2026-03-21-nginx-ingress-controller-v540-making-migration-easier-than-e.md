---
title: "NGINX Ingress Controller v5.4.0: Making Migration Easier Than Ever"
url: "https://blog.nginx.org/blog/nginx-ingress-controller-v5-4-0-making-migration-easier-than-ever"
date: "Sat, 21 Mar 2026 22:21:09 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
<p>We released NGINX Ingress Controller v5.4.0 ahead of KubeCon Europe, and this one is worth the noise. This release is laser-focused on making it easier for teams running <code>ingress-nginx</code> to migrate to NGINX Ingress Controller, without sacrificing the features and workflows they depend on. Here&#8217;s what&#8217;s new!</p>



<h4 class="wp-block-heading"><strong>Configuration Resilience and Validation</strong></h4>



<p><strong>What&#8217;s new:</strong> Ingress and VirtualServer resources can now be validated using <code>nginx -T</code> before being applied to the ingress controller pod, catching misconfigurations before they ever reach your running workloads. Where <code>ingress-nginx</code> handled this with a webhook, NGINX Ingress Controller delivers it natively.</p>



<p><strong>Why it matters:</strong> Misconfiguration is one of the leading causes of unplanned downtime in Kubernetes environments. Early validation feedback without an external webhook simplifies your setup and gives operators more confidence during deployments and migrations.</p>



<h4 class="wp-block-heading"><strong>CORS Support</strong></h4>



<p><strong>What&#8217;s new:</strong> A new CRD introduces native CORS configuration that works with both Ingress and VirtualServer resources, giving teams a consistent way to manage cross-origin policies without one-off annotations or custom snippets.</p>



<p><strong>Why it matters:</strong> CORS is a requirement for most modern web applications. Having a native, reusable CRD means it works the same way regardless of which resource type you&#8217;re using.</p>



<h4 class="wp-block-heading"><strong>Policy CRDs Now Compatible with <code>kind: Ingress</code></strong></h4>



<p><strong>What&#8217;s new:</strong> Starting with CORS and Access Control, you can now attach Policy CRDs directly to kind: Ingress objects. This was a real engineering challenge, but the team found a design that builds on existing work and will scale to support more policies going forward.</p>



<p><strong>Why it matters:</strong> Previously, teams had to adopt VirtualServer CRDs just to use NGINX&#8217;s policy features. Now you get the benefits of our policy framework without touching your existing Ingress resources, a much smoother migration path.</p>



<h4 class="wp-block-heading"><strong>Access Control for Ingress Resources</strong></h4>



<p><strong>What&#8217;s new:</strong> Access control policies are now fully compatible with <code>kind: Ingress</code>, bringing feature parity with VirtualServer across resource types.</p>



<p><strong>Why it matters:</strong> Security policies shouldn&#8217;t depend on which resource abstraction you happen to be using. Teams can now enforce consistent access controls during migration without rewriting resources ahead of schedule.</p>



<h4 class="wp-block-heading"><strong>Sticky Cookie Session Persistence Comes to Open Source</strong>!</h4>



<p><strong>What&#8217;s new:</strong> Session persistence via sticky cookies is now available to all users, no NGINX Plus subscription required.</p>



<p><strong>Why it matters:</strong> This was one of the most frequently raised requests from the open source community and a real sticking point for teams considering a move away from <code>ingress-nginx</code>. We listened, and we&#8217;re glad to finally ship it.</p>



<h4 class="wp-block-heading"><strong>Expanded Annotation Support</strong></h4>



<p><strong>What&#8217;s new:</strong> This release adds support for more <code>ingress-nginx</code> annotations: <code>app-root</code>, <code>ssl-redirect</code>, <code>next-upstream</code>, <code>next-upstream-timeouts</code>, and <code>next-upstream-tries</code>.</p>



<p><strong>Why it matters:</strong> Annotation compatibility is the biggest friction point when migrating from <code>ingress-nginx</code>. The more we support natively, the less you need to rewrite on day one, letting teams migrate incrementally at their own pace.</p>



<h4 class="wp-block-heading"><strong>Label-Based VirtualServerRoute Selection</strong></h4>



<p><strong>What&#8217;s new:</strong> VirtualServers can now select VirtualServerRoutes using label selectors instead of explicit references, making routing configurations more dynamic and less tightly coupled between resources.</p>



<p><strong>Why it matters:</strong> In large, multi-team environments, rigid resource references become a maintenance headache fast. Label-based selection gives platform teams the flexibility they need to manage routing at scale.</p>



<h4 class="wp-block-heading"><strong>Stability and Bug Fixes</strong></h4>



<p>This release also includes a number of stability improvements and bug fixes. Head over to the GitHub release page and our public release docs for the full picture.</p>



<h4 class="wp-block-heading">Wrapping Up</h4>



<p>F5 NGINX Ingress Controller 5.4.0 is all about meeting teams where they are. From native configuration validation and expanded annotation support to Policy CRDs that work directly with <code>kind: Ingress</code>, this release removes barriers to migrate from <code>ingress-nginx</code> to the F5 NGINX Ingress Controller. And with sticky cookie session persistence now available in the open source edition, we&#8217;ve addressed one of the community&#8217;s most long-standing requests.</p>



<p>Whether you&#8217;re planning a migration, already mid-flight, evaluating your long-term ingress strategy, or looking to get more out of F5 NGINX Ingress Controller&#8217;s policy framework without overhauling your existing resources, this new release gives you practical ways to move forward at your own pace. We&#8217;re here to help you find the right fit.</p>



<p>You can find more details at:&nbsp;</p>



<ul class="wp-block-list">
<li>GitHub release page: <a href="https://github.com/nginx/kubernetes-ingress/releases" rel="noreferrer noopener" target="_blank">https://github.com/nginx/kubernetes-ingress/releases</a> </li>



<li>Public release documentation: <a href="https://docs.nginx.com/nginx-ingress-controller/changelog#540">https://docs.nginx.com/nginx-ingress-controller</a></li>



<li>Changelog: <a href="https://docs.nginx.com/nginx-ingress-controller/changelog/" rel="noreferrer noopener" target="_blank">https://docs.nginx.com/nginx-ingress-controller/changelog</a></li>
</ul>



<hr class="wp-block-separator has-alpha-channel-opacity" />



<h4 class="wp-block-heading"><strong>Come Chat With Us at KubeCon Europe!</strong></h4>



<p>We&#8217;re proud of what the team put together here. If you&#8217;re at KubeCon Europe, come find us at the F5 booth in Hall 5, Booth 1084. We&#8217;d love to hear about your migration experience and what you want to see next.</p>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--9"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
