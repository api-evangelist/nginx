---
title: "Introducing kubernetes.nginx.org: A Community Hub for NGINX on Kubernetes, Including a New Ingress-NGINX Migration Tool"
url: "https://blog.nginx.org/blog/introducing-kubernetes-nginx-org-your-community-hub-for-nginx-on-kubernetes-and-a-new-ingress-nginx-migration-tool"
date: "Mon, 23 Mar 2026 16:49:26 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
<p>Today, we&#8217;re excited to announce <a href="https://kubernetes.nginx.org/">kubernetes.nginx.org</a>, a new community hub for everything NGINX networking on Kubernetes, along with a brand-new <a href="https://kubernetes.nginx.org/ingress-nginx-migration.html">Kubernetes community Ingress-NGINX Migration Tool</a> designed to make moving from the Kubernetes community Ingress-NGINX controller to the NGINX Ingress Controller as smooth as possible.</p>



<h2 class="wp-block-heading" id="why-a-community-hub">Why a Community Hub?</h2>



<p>Whether you&#8217;re running NGINX Ingress Controller, exploring NGINX Gateway Fabric, or planning a migration to either — we want to make everything NGINX does on Kubernetes easily accessible and discoverable from a single place, whether you&#8217;re evaluating your first project or managing multiple NGINX deployments across clusters.</p>



<p><a href="https://kubernetes.nginx.org/">kubernetes.nginx.org</a> brings it all together. Each project page includes feature overviews, version compatibility tables, quick-start installation commands, and direct links to GitHub and documentation — everything you need to get started or go deeper.</p>



<p><strong>Projects:</strong></p>



<ul class="wp-block-list">
<li><strong>NGINX Ingress Controller</strong> — A production-grade Ingress API implementation with VirtualServer CRDs, TLS termination, TCP/UDP load balancing, Prometheus metrics, and OpenTelemetry support.</li>



<li><strong>NGINX Gateway Fabric</strong> — Our Gateway API implementation, fully conformant with Gateway API v1.4.1, featuring control/data plane separation, multi-cloud support, traffic splitting, and mTLS.</li>
</ul>



<p><strong>Migration tools:</strong></p>



<ul class="wp-block-list">
<li><strong>Ingress-NGINX Migration Tool</strong> — An interactive, web-based guide that maps your existing Ingress-NGINX annotations to NGINX Ingress Controller equivalents, with a built-in Config Analyzer and ready-to-use output.</li>



<li><strong>ingress2gateway</strong> — A CLI tool that converts Ingress resources to Gateway API resources that you will be able to deploy in NGINX Gateway Fabric, supporting multiple providers including NGINX Ingress Controller and Ingress-NGINX.</li>
</ul>



<h2 class="wp-block-heading" id="the-ingress-nginx-migration-tool">The Ingress-NGINX Migration Tool</h2>



<p>With the community Ingress-NGINX controller reaching end of maintenance at v1.15.1, many teams are now evaluating their next steps. One of the most common questions we hear is: <em>&#8220;How do I move to NGINX Ingress Controller, and how much work is it going to be?&#8221;</em></p>



<p>The <a href="https://kubernetes.nginx.org/ingress-nginx-migration.html">Ingress-NGINX Migration Tool</a> is our answer. It&#8217;s an interactive, web-based guide that walks you through the entire migration process — from understanding the architectural differences between the two controllers to generating ready-to-use configuration.</p>



<h3 class="wp-block-heading" id="what-it-offers">What It Offers</h3>



<p><strong>A Config Analyzer that does the heavy lifting.</strong> Paste your existing Ingress YAML and the analyzer generates migration suggestions with copy-paste-ready output. It detects your annotations, maps them to their NGINX Ingress Controller equivalents, identifies anything unsupported, and flags the complexity of your migration.</p>



<p><strong>Over 130 annotation mappings.</strong> The reference guide provides comprehensive, side-by-side mappings across roughly 40 annotation categories — covering access control, authentication, CORS, rate limiting, SSL/TLS, canary deployments, load balancing, timeouts, and more. Each mapping includes before-and-after YAML examples you can expand and copy directly.</p>



<p><strong>Two migration strategies to match your approach:</strong></p>



<ul class="wp-block-list">
<li><strong>CRD-first</strong> (recommended) — Prioritizes VirtualServer resources and Policy CRDs for a more powerful and maintainable configuration model, falling back to annotations only when necessary.</li>



<li><strong>Annotation-first</strong> — Prioritizes annotation-to-annotation mappings where possible, ideal for teams that want to migrate incrementally.</li>
</ul>



<h3 class="wp-block-heading" id="why-it-matters">Why It Matters</h3>



<p>The two controllers look similar on the surface but differ fundamentally in how they handle configuration. The community Ingress-NGINX controller relies on <code>nginx.ingress.kubernetes.io/</code> annotations and ConfigMap keys. NGINX Ingress Controller uses Custom Resource Definitions as its primary configuration model, with <code>nginx.org/</code> annotations.</p>



<p>Manually mapping annotations one-by-one across a fleet of Ingress manifests is tedious and error-prone. The migration tool translates all possible annotations, highlights annotation to CRD migration paths, surfaces edge cases, and gives you a clear picture of what your migration will look like before you start making changes.</p>



<p>And with NGINX Ingress Controller v5.4.0, Policy CRDs can now be referenced directly from Ingress objects via the <code>nginx.org/policies</code> annotation — meaning you don&#8217;t have to convert everything to VirtualServer resources to take advantage of CRD-based policies. This significantly reduces the barrier to entry for teams migrating from annotation-heavy configurations.</p>



<h2 class="wp-block-heading" id="built-for-the-community">Built for the Community</h2>



<p>Both <a href="https://kubernetes.nginx.org/">kubernetes.nginx.org</a> and the <a href="https://kubernetes.nginx.org/ingress-nginx-migration.html">Ingress-NGINX Migration Tool</a> were built with community feedback at the center. The questions we&#8217;ve seen in GitHub issues, NGINX Community forum conversations, and conference hallways directly shaped what we prioritized.</p>



<p>This is a living resource. As the NGINX Kubernetes ecosystem evolves — with new features, new Gateway API conformance profiles, and new tooling — the community hub will evolve with it.</p>



<h2 class="wp-block-heading" id="get-started">Get Started</h2>



<ul class="wp-block-list">
<li><strong>Explore the hub:</strong> <a href="https://kubernetes.nginx.org/">kubernetes.nginx.org</a></li>



<li><strong>Try the Ingress-NGINX migration tool:</strong> <a href="https://kubernetes.nginx.org/ingress-nginx-migration.html">kubernetes.nginx.org/ingress-nginx-migration.html</a></li>



<li><strong>Get migration help:</strong> <a href="https://community.nginx.org/c/projects/ingress-nginx-migration-help/38">Ingress-NGINX Migration Help</a> on the NGINX Community forum</li>



<li><strong>NGINX Ingress Controller on GitHub:</strong> <a href="https://github.com/nginx/kubernetes-ingress">github.com/nginx/kubernetes-ingress</a></li>



<li><strong>NGINX Gateway Fabric on GitHub:</strong> <a href="https://github.com/nginx/nginx-gateway-fabric">github.com/nginx/nginx-gateway-fabric</a></li>
</ul>



<p>If you&#8217;re at <strong>KubeCon Europe 2026</strong>, come find us! We&#8217;d love to walk you through the hub and migration tool in person, hear what&#8217;s working for you, and learn what we should build next.</p>



<p>We&#8217;d love to hear your feedback! Open an issue, give the migration tool a spin, or if you have questions about migrating from Ingress-NGINX, head over to the <a href="https://community.nginx.org/c/projects/ingress-nginx-migration-help/38">Ingress-NGINX Migration Help</a> section in the NGINX Community forum — we&#8217;re there and happy to help.</p>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--8"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
