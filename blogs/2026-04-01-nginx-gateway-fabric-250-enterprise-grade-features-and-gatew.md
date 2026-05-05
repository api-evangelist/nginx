---
title: "NGINX Gateway Fabric 2.5.0: Enterprise-Grade Features and Gateway API 1.5 Conformance"
url: "https://blog.nginx.org/blog/nginx-gateway-fabric-2-5-0-enterprise-grade-features-and-gateway-api-1-5-conformance"
date: "Wed, 01 Apr 2026 13:55:02 +0000"
author: "Buu Lam"
feed_url: "https://blog.nginx.org/feed"
---
<p>NGINX Gateway Fabric 2.5.0 is here, and this one is a big deal. The release doubles down on enterprise-grade capabilities while keeping us at the forefront of Gateway API conformance. NGF remains one of the top conformant implementations of the Gateway API spec, and this release reinforces why. Here&#8217;s what&#8217;s new.</p>



<h2 class="wp-block-heading" id="gateway-api-15-conformance">Gateway API 1.5 Conformance</h2>



<p><strong>What&#8217;s new:</strong> NGF now conforms with the latest Gateway API 1.5 specification. This release picks up two notable promotions from the spec: TLSRoute has moved to the standard channel and is now v1, and ReferenceGrant has been promoted to v1 as well. Keep an eye out for NGINX Gateway Fabric being highlighted when the official Gateway API 1.5 release is published.</p>



<p><strong>Why it matters:</strong> Conformance isn&#8217;t just a checkbox. It means your investment in Gateway API resources is portable, interoperable, and built on a spec that&#8217;s clearly maturing toward production-readiness. These promotions are a signal that the ecosystem is stabilising, and NGF is keeping pace.</p>



<h2 class="wp-block-heading" id="cors-via-httpcorsfilter">CORS via HTTPCORSFilter</h2>



<p><strong>What&#8217;s new:</strong> CORS support has arrived for Gateway Fabric through the Gateway API HTTPCORSFilter on HTTPRoute resources. Preflight requests are handled automatically and CORS headers are injected at the proxy layer.</p>



<p><strong>Why it matters:</strong> Application teams shouldn&#8217;t need to own CORS configuration. Handling it at the proxy layer removes that burden entirely, keeps it consistent across services, and means developers can stop worrying about it.</p>



<h2 class="wp-block-heading" id="nginx-plus-jwt-authentication">NGINX Plus: JWT Authentication</h2>



<p><strong>What&#8217;s new:</strong> JWT-based authentication is now natively supported, giving teams a straightforward way to enforce token-based access control directly at the Gateway.</p>



<p><strong>Why it matters:</strong> Pushing auth to the edge rather than handling it in every application individually is cleaner, more consistent, and easier to audit. For teams already using JWTs, this is a natural fit that requires no additional infrastructure.</p>



<h2 class="wp-block-heading" id="nginx-plus-openid-connect-oidc">NGINX Plus: OpenID Connect (OIDC)</h2>



<p><strong>What&#8217;s new:</strong> NGF now supports native OIDC, enabling you to delegate authentication to external identity providers like Okta, Keycloak, and Azure AD without bolting on third-party solutions.</p>



<p><strong>Why it matters:</strong> This is one of the top reasons our ingress controller customers choose NGINX Plus, and now it&#8217;s available in Gateway Fabric too. For enterprise teams that need identity integration as part of their platform, this removes a significant barrier and brings NGF firmly into the enterprise conversation.</p>



<h2 class="wp-block-heading" id="stability-and-bug-fixes">Stability and Bug Fixes</h2>



<p>This release also includes a number of stability improvements and bug fixes. Head over to the <a href="https://github.com/nginxinc/nginx-gateway-fabric">GitHub changelog</a> and our public release docs for the full picture.</p>



<hr class="wp-block-separator has-alpha-channel-opacity" />



<p>We&#8217;re proud of what the team put together here. It was great to see many of you at KubeCon Europe. The feedback we received was encouraging and we can&#8217;t wait for the next release!</p>



<figure class="wp-block-image size-large is-style-rounded is-style-rounded--4"><a href="https://community.nginx.org" rel=" noreferrer noopener" target="_blank"><img alt="NGINX Community Forum" class="wp-image-74079" height="261" src="https://nginxblog-8de1046ff5a84f2c-endpoint.azureedge.net/blobnginxbloga72cde487e/wp-content/uploads/2024/09/Forum-CTA-banner-v1-1024x261.png" width="1024" /></a></figure>
