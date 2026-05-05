---
title: "Built for Change: How NGINX Ingress Controller and NGINX Gateway Fabric Handle Kubernetes Backend Changes Natively"
url: "https://blog.nginx.org/blog/built-for-change-how-nginx-ingress-controller-and-nginx-gateway-fabric-handle-kubernetes-backend-changes-natively"
date: "Tue, 28 Apr 2026 16:45:22 +0000"
author: "Alessandro"
feed_url: "https://blog.nginx.org/feed"
---
<p>Kubernetes applications are designed to change constantly. Pods scale out, roll forward, restart, and disappear, so the traffic layer has to keep pace with a backend set that is never truly static.</p>



<p>That is the backdrop for both NGINX Ingress Controller (NIC) and NGINX Gateway Fabric (NGF). In both cases, Kubernetes is the source of truth for backend membership, and the controller layer translates backend changes into active NGINX configuration.</p>



<h2 class="wp-block-heading" id="the-real-goal">The Real Goal</h2>



<p>For platform teams, the goal is simple: when a Deployment scales in or out, upstream membership should change automatically, without anyone manually editing NGINX configuration.</p>



<p>That is the core value of the Kubernetes-native model used by both products. Kubernetes keeps track of which backends belong behind a Service, and the controller keeps NGINX aligned with that current backend set.</p>



<h2 class="wp-block-heading" id="not-a-manual-config-problem">Not a Manual Config Problem</h2>



<p>It is easy to think of backend discovery as a DNS problem, but for normal in-cluster routing the more important fact is that Kubernetes already knows which pods sit behind a Service. NGINX Ingress Controller and NGINX Gateway Fabric are built to consume that Kubernetes state and turn it into an upstream configuration that NGINX can use.</p>



<p>The practical result is that upstream changes caused by scaling events are handled natively by the product rather than by a human updating server lists in configuration files. When the backend set changes, the controller updates what NGINX should send traffic to based on Kubernetes state.</p>



<h2 class="wp-block-heading" id="nic-and-ngf-in-practice">NGINX Ingress Controller and NGINX Gateway Fabric in Practice</h2>



<p>For NGINX Ingress Controller, the behavior is straightforward. The NGINX Ingress Controller watches Kubernetes resources related to backend reachability and translates those changes into NGINX upstream updates. With NGINX Plus, those upstream changes can be applied dynamically. With NGINX Open Source, the controller still follows Kubernetes changes automatically, but the update path relies on regenerating configuration and reloading NGINX.</p>



<p>NGINX Gateway Fabric follows the same Kubernetes-native model. The NGINX Gateway Fabric control plane watches cluster state, translates Gateway API intent into NGINX configuration, and pushes those changes into the data plane. The result is the same from an operator perspective: upstream membership is maintained by the product as the backend set evolves.</p>



<h2 class="wp-block-heading" id="example-the-cafe-app">Example: The Cafe App</h2>



<p>Consider a cafe application exposed through a Kubernetes Service named <code>cafe</code>. At 9:00 a.m., the <code>cafe</code> Deployment is running with 2 pod replicas, so the <code>cafe</code> Service has two live backend endpoints.</p>



<p>If NGINX Ingress Controller is fronting that application, NGINX Ingress Controller sees the backend endpoints associated with the <code>cafe</code> Service and builds an upstream with those two pod IPs. If NGINX Gateway Fabric is fronting the same application through Gateway API resources, NGF does the equivalent thing through its control plane and data plane model.</p>



<p>Now imagine a traffic spike during lunch. The <code>cafe</code> Deployment scales from 2 replicas to 10 replicas. Kubernetes updates the endpoint data for the <code>cafe</code> Service to reflect the 10 running pods.</p>



<p>At that point, nobody should need to open an NGINX config file and add eight new upstream servers by hand. NGINX Ingress Controller and NGINX Gateway Fabric are expected to absorb that change natively: they observe the updated Kubernetes backend state and keep the active upstream aligned with the current set of 10 pod IPs.</p>



<p>That is the operational outcome that matters most. Scaling the application changes the Kubernetes backend set, and the ingress or gateway layer follows automatically.</p>



<h2 class="wp-block-heading" id="why-it-matters">Why it Matters</h2>



<p>This matters because autoscaling, rolling deployments, and pod replacement are normal operating conditions in Kubernetes. A traffic layer that requires manual config edits every time a backend set changes would not fit how modern clusters actually run.</p>



<p>The better model is for upstream changes to be handled as a native part of Kubernetes traffic management. That is the common story across NGINX Ingress Controller and NGINX Gateway Fabric: backend changes originate in Kubernetes, the controller observes them, and NGINX is kept aligned with the current set of running application backends.</p>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--1"><a href="https://go.f5.net/nginxcommunityforum-blogcta" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
