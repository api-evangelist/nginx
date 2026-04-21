# NGINX (nginx)
NGINX is a high-performance open-source web server, reverse proxy, and API gateway widely used for load balancing, SSL termination, caching, and traffic management for APIs and microservices. Originally written by Igor Sysoev and released under the 2-clause BSD license, NGINX powers a significant portion of the world's web traffic. Enterprise support and commercial features are available from F5, Inc.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/nginx/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:
 - API Gateway, Caching, Cloud Native, Load Balancer, Open Source, Reverse Proxy, Web Server

## Timestamps
- **Created:** 2026-03-18
- **Modified:** 2026-04-21

## APIs

### NGINX
NGINX is a versatile open-source software for web serving, reverse proxying, caching, load balancing, media streaming, and API gateway functionality powering a significant portion of the world's web traffic. Licensed under the 2-clause BSD license and governed by F5, Inc.

**Human URL:** [https://nginx.org/](https://nginx.org/)

#### Tags:
 - API Gateway, Load Balancer, Open Source, Reverse Proxy, Web Server

#### Properties
- [Documentation](https://nginx.org/en/docs/)
- [GettingStarted](https://nginx.org/en/docs/beginners_guide.html)
- [APIReference](https://nginx.org/en/docs/dirindex.html)
- [ChangeLog](https://nginx.org/en/CHANGES)
- [GitHubRepository](https://github.com/nginx/nginx)

---

### NGINX Plus HTTP API
The NGINX Plus HTTP API provides a RESTful interface for dynamic configuration and real-time monitoring of a running NGINX Plus instance. It supports managing upstream servers, key-value pairs, and retrieving connection, cache, and rate-limiting statistics without requiring configuration reloads. Available as part of the NGINX commercial subscription.

**Human URL:** [https://nginx.org/en/docs/http/ngx_http_api_module.html](https://nginx.org/en/docs/http/ngx_http_api_module.html)

#### Tags:
 - Admin, Management, Monitoring, NGINX Plus, REST API

#### Properties
- [Documentation](https://nginx.org/en/docs/http/ngx_http_api_module.html)
- [APIReference](https://nginx.org/en/docs/http/ngx_http_api_module.html#api)
- [OpenAPI](openapi/nginx-plus-http-api-openapi.yaml)
- [JSONLD](json-ld/nginx-plus-http-api-context.jsonld)
- [SDK - Go SDK](https://github.com/nginx/nginx-plus-go-client)

---

### NGINX Stub Status API
The NGINX Stub Status module exposes a simple HTTP endpoint providing basic server performance metrics including active connections, total accepts, handled connections, and request counts. It is available in open-source NGINX and must be enabled at compile time with the --with-http_stub_status_module flag.

**Human URL:** [https://nginx.org/en/docs/http/ngx_http_stub_status_module.html](https://nginx.org/en/docs/http/ngx_http_stub_status_module.html)

#### Tags:
 - Metrics, Monitoring, Open Source, Status

#### Properties
- [Documentation](https://nginx.org/en/docs/http/ngx_http_stub_status_module.html)
- [OpenAPI](openapi/nginx-stub-status-openapi.yaml)

---

### NGINX njs Scripting API
The NGINX njs module embeds a JavaScript (ECMAScript 5.1+) runtime into NGINX, allowing developers to write custom request/response handlers, access control logic, and content filters. It provides HTTP and stream request objects, a Fetch-compatible web API, cryptographic functions, and built-in modules for file system, XML, and query string operations.

**Human URL:** [https://nginx.org/en/docs/njs/](https://nginx.org/en/docs/njs/)

#### Tags:
 - Extensibility, JavaScript, Modules, Scripting

#### Properties
- [Documentation](https://nginx.org/en/docs/njs/)
- [APIReference](https://nginx.org/en/docs/njs/reference.html)
- [GettingStarted](https://nginx.org/en/docs/njs/install.html)
- [OpenAPI](openapi/nginx-njs-openapi.yaml)
- [JSONLD](json-ld/nginx-context.jsonld)
- [GitHubRepository](https://github.com/nginx/njs)

---

### NGINX Ingress Controller
The NGINX Ingress Controller is a Kubernetes-native ingress controller built on NGINX that manages external access to services in a Kubernetes cluster. It supports TLS termination, path-based routing, rate limiting, and advanced traffic management through annotations and custom resources.

**Human URL:** [https://github.com/nginx/kubernetes-ingress](https://github.com/nginx/kubernetes-ingress)

#### Tags:
 - Cloud Native, Ingress, Kubernetes, Traffic Management

#### Properties
- [Documentation](https://docs.nginx.com/nginx-ingress-controller/)
- [GettingStarted](https://docs.nginx.com/nginx-ingress-controller/installation/installing-nic/)
- [GitHubRepository](https://github.com/nginx/kubernetes-ingress)

---

### NGINX Gateway Fabric
NGINX Gateway Fabric is a Kubernetes Gateway API implementation using NGINX as the data plane. It provides standards-based traffic management through Gateway API resources including Gateway, HTTPRoute, GRPCRoute, and TLSRoute, enabling fine-grained control over ingress and routing in Kubernetes environments.

**Human URL:** [https://github.com/nginx/nginx-gateway-fabric](https://github.com/nginx/nginx-gateway-fabric)

#### Tags:
 - Cloud Native, Gateway API, Kubernetes, Routing

#### Properties
- [Documentation](https://docs.nginx.com/nginx-gateway-fabric/)
- [GitHubRepository](https://github.com/nginx/nginx-gateway-fabric)

---

### NGINX Agent
NGINX Agent provides an administrative entry point to remotely manage, configure, and collect metrics and events from NGINX instances. It enables centralized management of distributed NGINX deployments through a gRPC-based control plane interface.

**Human URL:** [https://github.com/nginx/agent](https://github.com/nginx/agent)

#### Tags:
 - Agent, Management, Monitoring, Remote Administration

#### Properties
- [Documentation](https://github.com/nginx/agent)
- [GitHubRepository](https://github.com/nginx/agent)

## Common Properties
- [Website](https://nginx.org/)
- [Documentation](https://nginx.org/en/docs/)
- [GettingStarted](https://nginx.org/en/docs/beginners_guide.html)
- [Blog](https://blog.nginx.org/)
- [ChangeLog](https://nginx.org/en/CHANGES)
- [Security](https://nginx.org/en/security_advisories.html)
- [Support](https://community.nginx.org)
- [GitHubOrganization](https://github.com/nginx)
- [GitHubRepository](https://github.com/nginx/nginx)
- [YouTube](https://www.youtube.com/nginxinc)
- [StackOverflow](https://stackoverflow.com/questions/tagged/nginx)
- [X](https://x.com/nginxorg)
- [FAQ](https://nginx.org/en/docs/faq.html)
- [CLI - Prometheus Exporter](https://github.com/nginx/nginx-prometheus-exporter)
- [SDK - Directive Reference Library (npm)](https://www.npmjs.com/package/@nginx/reference-lib)
- [SDK - Rust Bindings (crates.io)](https://crates.io/crates/ngx)
- [CodeExamples - NGINX Demos](https://github.com/nginx/nginx-demos)
- [CodeExamples - njs Examples](https://github.com/nginx/njs-examples)
- [SpectralRules](rules/nginx-spectral-rules.yml)
- [Vocabulary](vocabulary/nginx-vocabulary.yaml)
- [NaftikoCapability - Traffic Management](capabilities/traffic-management.yaml)
- [NaftikoCapability - Monitoring and Observability](capabilities/monitoring-and-observability.yaml)

## Features

| Name | Description |
|---|---|
| HTTP Web Server | High-performance HTTP and HTTPS server with support for HTTP/1.1, HTTP/2, HTTP/3, and early hints (103). |
| Reverse Proxy | Forward client requests to backend application servers with load balancing, buffering, and caching. |
| Load Balancing | Distribute traffic across upstream servers using round-robin, least-connections, IP hash, and sticky session algorithms. |
| SSL/TLS Termination | Terminate and offload SSL/TLS connections at the proxy layer with support for SNI, OCSP stapling, and encrypted client hello. |
| Content Caching | Cache responses from upstream servers to reduce backend load and improve response times. |
| gRPC Proxying | Route and load balance gRPC traffic to backend services. |
| WebSocket Support | Proxy WebSocket connections for real-time bidirectional communication. |
| TCP/UDP Proxy | Stream module for proxying and load balancing arbitrary TCP and UDP traffic. |
| Mail Proxy | Proxy IMAP, POP3, and SMTP mail protocols with authentication support. |
| Dynamic Modules | Extend functionality at runtime through loadable modules without recompiling. |
| njs Scripting | Embed JavaScript logic for custom request handling, access control, and content filtering. |
| OpenTelemetry | Built-in OpenTelemetry module for distributed tracing and observability. |

## Use Cases

| Name | Description |
|---|---|
| API Gateway | Route, authenticate, rate limit, and load balance API traffic across microservices. |
| Kubernetes Ingress | Manage external access to Kubernetes services with the NGINX Ingress Controller or Gateway Fabric. |
| Content Delivery | Cache and serve static content close to users with high throughput and low latency. |
| Microservices Proxy | Act as a sidecar or edge proxy for service-to-service communication in microservices architectures. |
| SSL Offloading | Terminate TLS at the edge to reduce cryptographic overhead on backend application servers. |
| Load Balancing | Distribute HTTP, TCP, UDP, and gRPC traffic across pools of upstream servers for high availability. |

## Integrations

| Name | Description |
|---|---|
| Kubernetes | Native Kubernetes integration through NGINX Ingress Controller and Gateway Fabric. |
| OpenTelemetry | Built-in ngx_otel_module for exporting traces to OpenTelemetry collectors. |
| Prometheus | Expose metrics for scraping by Prometheus via stub status or the NGINX Plus API. |
| Ansible | Official Ansible roles for automated NGINX installation and configuration management. |
| Docker | Official Docker images for containerized NGINX deployments. |
| Helm | Helm charts for deploying NGINX Ingress Controller and Gateway Fabric on Kubernetes. |

## Artifacts

### OpenAPI (3)
- [nginx-njs-openapi.yaml](openapi/nginx-njs-openapi.yaml)
- [nginx-plus-http-api-openapi.yaml](openapi/nginx-plus-http-api-openapi.yaml)
- [nginx-stub-status-openapi.yaml](openapi/nginx-stub-status-openapi.yaml)

### JSON Schema (58)
- [njs-headers-schema.json](json-schema/njs-headers-schema.json)
- [njs-http-request-schema.json](json-schema/njs-http-request-schema.json)
- [njs-ngx-schema.json](json-schema/njs-ngx-schema.json)
- [njs-ngx-shared-schema.json](json-schema/njs-ngx-shared-schema.json)
- [njs-periodic-session-schema.json](json-schema/njs-periodic-session-schema.json)
- [njs-request-schema.json](json-schema/njs-request-schema.json)
- [njs-response-schema.json](json-schema/njs-response-schema.json)
- [njs-shared-dict-schema.json](json-schema/njs-shared-dict-schema.json)
- [njs-stream-session-schema.json](json-schema/njs-stream-session-schema.json)
- [plus-http-api-array-of-strings-schema.json](json-schema/plus-http-api-array-of-strings-schema.json)
- [plus-http-api-nginx-connections-schema.json](json-schema/plus-http-api-nginx-connections-schema.json)
- [plus-http-api-nginx-error-schema.json](json-schema/plus-http-api-nginx-error-schema.json)
- [plus-http-api-nginx-http-cache-schema.json](json-schema/plus-http-api-nginx-http-cache-schema.json)
- [plus-http-api-nginx-http-caches-map-schema.json](json-schema/plus-http-api-nginx-http-caches-map-schema.json)
- [plus-http-api-nginx-http-keyval-zone-post-patch-schema.json](json-schema/plus-http-api-nginx-http-keyval-zone-post-patch-schema.json)
- [plus-http-api-nginx-http-keyval-zone-schema.json](json-schema/plus-http-api-nginx-http-keyval-zone-schema.json)
- [plus-http-api-nginx-http-keyval-zones-map-schema.json](json-schema/plus-http-api-nginx-http-keyval-zones-map-schema.json)
- [plus-http-api-nginx-http-limit-conn-zone-schema.json](json-schema/plus-http-api-nginx-http-limit-conn-zone-schema.json)
- [plus-http-api-nginx-http-limit-conn-zones-map-schema.json](json-schema/plus-http-api-nginx-http-limit-conn-zones-map-schema.json)
- [plus-http-api-nginx-http-limit-req-zone-schema.json](json-schema/plus-http-api-nginx-http-limit-req-zone-schema.json)
- [plus-http-api-nginx-http-limit-req-zones-map-schema.json](json-schema/plus-http-api-nginx-http-limit-req-zones-map-schema.json)
- [plus-http-api-nginx-http-location-zone-schema.json](json-schema/plus-http-api-nginx-http-location-zone-schema.json)
- [plus-http-api-nginx-http-location-zones-map-schema.json](json-schema/plus-http-api-nginx-http-location-zones-map-schema.json)
- [plus-http-api-nginx-http-requests-schema.json](json-schema/plus-http-api-nginx-http-requests-schema.json)
- [plus-http-api-nginx-http-server-zone-schema.json](json-schema/plus-http-api-nginx-http-server-zone-schema.json)
- [plus-http-api-nginx-http-server-zones-map-schema.json](json-schema/plus-http-api-nginx-http-server-zones-map-schema.json)
- [plus-http-api-nginx-http-upstream-conf-server-map-schema.json](json-schema/plus-http-api-nginx-http-upstream-conf-server-map-schema.json)
- [plus-http-api-nginx-http-upstream-conf-server-schema.json](json-schema/plus-http-api-nginx-http-upstream-conf-server-schema.json)
- [plus-http-api-nginx-http-upstream-map-schema.json](json-schema/plus-http-api-nginx-http-upstream-map-schema.json)
- [plus-http-api-nginx-http-upstream-peer-map-schema.json](json-schema/plus-http-api-nginx-http-upstream-peer-map-schema.json)
- [plus-http-api-nginx-http-upstream-peer-schema.json](json-schema/plus-http-api-nginx-http-upstream-peer-schema.json)
- [plus-http-api-nginx-http-upstream-schema.json](json-schema/plus-http-api-nginx-http-upstream-schema.json)
- [plus-http-api-nginx-license-object-schema.json](json-schema/plus-http-api-nginx-license-object-schema.json)
- [plus-http-api-nginx-object-schema.json](json-schema/plus-http-api-nginx-object-schema.json)
- [plus-http-api-nginx-processes-schema.json](json-schema/plus-http-api-nginx-processes-schema.json)
- [plus-http-api-nginx-resolver-zone-schema.json](json-schema/plus-http-api-nginx-resolver-zone-schema.json)
- [plus-http-api-nginx-resolver-zones-map-schema.json](json-schema/plus-http-api-nginx-resolver-zones-map-schema.json)
- [plus-http-api-nginx-slab-zone-map-schema.json](json-schema/plus-http-api-nginx-slab-zone-map-schema.json)
- [plus-http-api-nginx-slab-zone-schema.json](json-schema/plus-http-api-nginx-slab-zone-schema.json)
- [plus-http-api-nginx-slab-zone-slot-schema.json](json-schema/plus-http-api-nginx-slab-zone-slot-schema.json)
- [plus-http-api-nginx-ssl-object-schema.json](json-schema/plus-http-api-nginx-ssl-object-schema.json)
- [plus-http-api-nginx-stream-keyval-zone-post-patch-schema.json](json-schema/plus-http-api-nginx-stream-keyval-zone-post-patch-schema.json)
- [plus-http-api-nginx-stream-keyval-zone-schema.json](json-schema/plus-http-api-nginx-stream-keyval-zone-schema.json)
- [plus-http-api-nginx-stream-keyval-zones-map-schema.json](json-schema/plus-http-api-nginx-stream-keyval-zones-map-schema.json)
- [plus-http-api-nginx-stream-limit-conn-zone-schema.json](json-schema/plus-http-api-nginx-stream-limit-conn-zone-schema.json)
- [plus-http-api-nginx-stream-limit-conn-zones-map-schema.json](json-schema/plus-http-api-nginx-stream-limit-conn-zones-map-schema.json)
- [plus-http-api-nginx-stream-server-zone-schema.json](json-schema/plus-http-api-nginx-stream-server-zone-schema.json)
- [plus-http-api-nginx-stream-server-zones-map-schema.json](json-schema/plus-http-api-nginx-stream-server-zones-map-schema.json)
- [plus-http-api-nginx-stream-upstream-conf-server-map-schema.json](json-schema/plus-http-api-nginx-stream-upstream-conf-server-map-schema.json)
- [plus-http-api-nginx-stream-upstream-conf-server-schema.json](json-schema/plus-http-api-nginx-stream-upstream-conf-server-schema.json)
- [plus-http-api-nginx-stream-upstream-map-schema.json](json-schema/plus-http-api-nginx-stream-upstream-map-schema.json)
- [plus-http-api-nginx-stream-upstream-peer-map-schema.json](json-schema/plus-http-api-nginx-stream-upstream-peer-map-schema.json)
- [plus-http-api-nginx-stream-upstream-peer-schema.json](json-schema/plus-http-api-nginx-stream-upstream-peer-schema.json)
- [plus-http-api-nginx-stream-upstream-schema.json](json-schema/plus-http-api-nginx-stream-upstream-schema.json)
- [plus-http-api-nginx-stream-zone-sync-schema.json](json-schema/plus-http-api-nginx-stream-zone-sync-schema.json)
- [plus-http-api-nginx-stream-zone-sync-zone-schema.json](json-schema/plus-http-api-nginx-stream-zone-sync-zone-schema.json)
- [plus-http-api-nginx-worker-schema.json](json-schema/plus-http-api-nginx-worker-schema.json)
- [plus-http-api-nginx-workers-map-schema.json](json-schema/plus-http-api-nginx-workers-map-schema.json)

### JSON-LD (2)
- [nginx-context.jsonld](json-ld/nginx-context.jsonld)
- [nginx-plus-http-api-context.jsonld](json-ld/nginx-plus-http-api-context.jsonld)

### JSON Structure (58)
- [njs-headers-structure.json](json-structure/njs-headers-structure.json)
- [njs-http-request-structure.json](json-structure/njs-http-request-structure.json)
- [njs-ngx-shared-structure.json](json-structure/njs-ngx-shared-structure.json)
- [njs-ngx-structure.json](json-structure/njs-ngx-structure.json)
- [njs-periodic-session-structure.json](json-structure/njs-periodic-session-structure.json)
- [njs-request-structure.json](json-structure/njs-request-structure.json)
- [njs-response-structure.json](json-structure/njs-response-structure.json)
- [njs-shared-dict-structure.json](json-structure/njs-shared-dict-structure.json)
- [njs-stream-session-structure.json](json-structure/njs-stream-session-structure.json)
- [plus-http-api-array-of-strings-structure.json](json-structure/plus-http-api-array-of-strings-structure.json)
- [plus-http-api-nginx-connections-structure.json](json-structure/plus-http-api-nginx-connections-structure.json)
- [plus-http-api-nginx-error-structure.json](json-structure/plus-http-api-nginx-error-structure.json)
- [plus-http-api-nginx-http-cache-structure.json](json-structure/plus-http-api-nginx-http-cache-structure.json)
- [plus-http-api-nginx-http-caches-map-structure.json](json-structure/plus-http-api-nginx-http-caches-map-structure.json)
- [plus-http-api-nginx-http-keyval-zone-post-patch-structure.json](json-structure/plus-http-api-nginx-http-keyval-zone-post-patch-structure.json)
- [plus-http-api-nginx-http-keyval-zone-structure.json](json-structure/plus-http-api-nginx-http-keyval-zone-structure.json)
- [plus-http-api-nginx-http-keyval-zones-map-structure.json](json-structure/plus-http-api-nginx-http-keyval-zones-map-structure.json)
- [plus-http-api-nginx-http-limit-conn-zone-structure.json](json-structure/plus-http-api-nginx-http-limit-conn-zone-structure.json)
- [plus-http-api-nginx-http-limit-conn-zones-map-structure.json](json-structure/plus-http-api-nginx-http-limit-conn-zones-map-structure.json)
- [plus-http-api-nginx-http-limit-req-zone-structure.json](json-structure/plus-http-api-nginx-http-limit-req-zone-structure.json)
- [plus-http-api-nginx-http-limit-req-zones-map-structure.json](json-structure/plus-http-api-nginx-http-limit-req-zones-map-structure.json)
- [plus-http-api-nginx-http-location-zone-structure.json](json-structure/plus-http-api-nginx-http-location-zone-structure.json)
- [plus-http-api-nginx-http-location-zones-map-structure.json](json-structure/plus-http-api-nginx-http-location-zones-map-structure.json)
- [plus-http-api-nginx-http-requests-structure.json](json-structure/plus-http-api-nginx-http-requests-structure.json)
- [plus-http-api-nginx-http-server-zone-structure.json](json-structure/plus-http-api-nginx-http-server-zone-structure.json)
- [plus-http-api-nginx-http-server-zones-map-structure.json](json-structure/plus-http-api-nginx-http-server-zones-map-structure.json)
- [plus-http-api-nginx-http-upstream-conf-server-map-structure.json](json-structure/plus-http-api-nginx-http-upstream-conf-server-map-structure.json)
- [plus-http-api-nginx-http-upstream-conf-server-structure.json](json-structure/plus-http-api-nginx-http-upstream-conf-server-structure.json)
- [plus-http-api-nginx-http-upstream-map-structure.json](json-structure/plus-http-api-nginx-http-upstream-map-structure.json)
- [plus-http-api-nginx-http-upstream-peer-map-structure.json](json-structure/plus-http-api-nginx-http-upstream-peer-map-structure.json)
- [plus-http-api-nginx-http-upstream-peer-structure.json](json-structure/plus-http-api-nginx-http-upstream-peer-structure.json)
- [plus-http-api-nginx-http-upstream-structure.json](json-structure/plus-http-api-nginx-http-upstream-structure.json)
- [plus-http-api-nginx-license-object-structure.json](json-structure/plus-http-api-nginx-license-object-structure.json)
- [plus-http-api-nginx-object-structure.json](json-structure/plus-http-api-nginx-object-structure.json)
- [plus-http-api-nginx-processes-structure.json](json-structure/plus-http-api-nginx-processes-structure.json)
- [plus-http-api-nginx-resolver-zone-structure.json](json-structure/plus-http-api-nginx-resolver-zone-structure.json)
- [plus-http-api-nginx-resolver-zones-map-structure.json](json-structure/plus-http-api-nginx-resolver-zones-map-structure.json)
- [plus-http-api-nginx-slab-zone-map-structure.json](json-structure/plus-http-api-nginx-slab-zone-map-structure.json)
- [plus-http-api-nginx-slab-zone-slot-structure.json](json-structure/plus-http-api-nginx-slab-zone-slot-structure.json)
- [plus-http-api-nginx-slab-zone-structure.json](json-structure/plus-http-api-nginx-slab-zone-structure.json)
- [plus-http-api-nginx-ssl-object-structure.json](json-structure/plus-http-api-nginx-ssl-object-structure.json)
- [plus-http-api-nginx-stream-keyval-zone-post-patch-structure.json](json-structure/plus-http-api-nginx-stream-keyval-zone-post-patch-structure.json)
- [plus-http-api-nginx-stream-keyval-zone-structure.json](json-structure/plus-http-api-nginx-stream-keyval-zone-structure.json)
- [plus-http-api-nginx-stream-keyval-zones-map-structure.json](json-structure/plus-http-api-nginx-stream-keyval-zones-map-structure.json)
- [plus-http-api-nginx-stream-limit-conn-zone-structure.json](json-structure/plus-http-api-nginx-stream-limit-conn-zone-structure.json)
- [plus-http-api-nginx-stream-limit-conn-zones-map-structure.json](json-structure/plus-http-api-nginx-stream-limit-conn-zones-map-structure.json)
- [plus-http-api-nginx-stream-server-zone-structure.json](json-structure/plus-http-api-nginx-stream-server-zone-structure.json)
- [plus-http-api-nginx-stream-server-zones-map-structure.json](json-structure/plus-http-api-nginx-stream-server-zones-map-structure.json)
- [plus-http-api-nginx-stream-upstream-conf-server-map-structure.json](json-structure/plus-http-api-nginx-stream-upstream-conf-server-map-structure.json)
- [plus-http-api-nginx-stream-upstream-conf-server-structure.json](json-structure/plus-http-api-nginx-stream-upstream-conf-server-structure.json)
- [plus-http-api-nginx-stream-upstream-map-structure.json](json-structure/plus-http-api-nginx-stream-upstream-map-structure.json)
- [plus-http-api-nginx-stream-upstream-peer-map-structure.json](json-structure/plus-http-api-nginx-stream-upstream-peer-map-structure.json)
- [plus-http-api-nginx-stream-upstream-peer-structure.json](json-structure/plus-http-api-nginx-stream-upstream-peer-structure.json)
- [plus-http-api-nginx-stream-upstream-structure.json](json-structure/plus-http-api-nginx-stream-upstream-structure.json)
- [plus-http-api-nginx-stream-zone-sync-structure.json](json-structure/plus-http-api-nginx-stream-zone-sync-structure.json)
- [plus-http-api-nginx-stream-zone-sync-zone-structure.json](json-structure/plus-http-api-nginx-stream-zone-sync-zone-structure.json)
- [plus-http-api-nginx-worker-structure.json](json-structure/plus-http-api-nginx-worker-structure.json)
- [plus-http-api-nginx-workers-map-structure.json](json-structure/plus-http-api-nginx-workers-map-structure.json)

### Examples (59)
- [njs-headers-example.json](examples/njs-headers-example.json)
- [njs-http-request-example.json](examples/njs-http-request-example.json)
- [njs-ngx-example.json](examples/njs-ngx-example.json)
- [njs-ngx-shared-example.json](examples/njs-ngx-shared-example.json)
- [njs-periodic-session-example.json](examples/njs-periodic-session-example.json)
- [njs-request-example.json](examples/njs-request-example.json)
- [njs-response-example.json](examples/njs-response-example.json)
- [njs-shared-dict-example.json](examples/njs-shared-dict-example.json)
- [njs-stream-session-example.json](examples/njs-stream-session-example.json)
- [plus-http-api-array-of-strings-example.json](examples/plus-http-api-array-of-strings-example.json)
- [plus-http-api-nginx-connections-example.json](examples/plus-http-api-nginx-connections-example.json)
- [plus-http-api-nginx-error-example.json](examples/plus-http-api-nginx-error-example.json)
- [plus-http-api-nginx-http-cache-example.json](examples/plus-http-api-nginx-http-cache-example.json)
- [plus-http-api-nginx-http-caches-map-example.json](examples/plus-http-api-nginx-http-caches-map-example.json)
- [plus-http-api-nginx-http-keyval-zone-example.json](examples/plus-http-api-nginx-http-keyval-zone-example.json)
- [plus-http-api-nginx-http-keyval-zone-post-patch-example.json](examples/plus-http-api-nginx-http-keyval-zone-post-patch-example.json)
- [plus-http-api-nginx-http-keyval-zones-map-example.json](examples/plus-http-api-nginx-http-keyval-zones-map-example.json)
- [plus-http-api-nginx-http-limit-conn-zone-example.json](examples/plus-http-api-nginx-http-limit-conn-zone-example.json)
- [plus-http-api-nginx-http-limit-conn-zones-map-example.json](examples/plus-http-api-nginx-http-limit-conn-zones-map-example.json)
- [plus-http-api-nginx-http-limit-req-zone-example.json](examples/plus-http-api-nginx-http-limit-req-zone-example.json)
- [plus-http-api-nginx-http-limit-req-zones-map-example.json](examples/plus-http-api-nginx-http-limit-req-zones-map-example.json)
- [plus-http-api-nginx-http-location-zone-example.json](examples/plus-http-api-nginx-http-location-zone-example.json)
- [plus-http-api-nginx-http-location-zones-map-example.json](examples/plus-http-api-nginx-http-location-zones-map-example.json)
- [plus-http-api-nginx-http-requests-example.json](examples/plus-http-api-nginx-http-requests-example.json)
- [plus-http-api-nginx-http-server-zone-example.json](examples/plus-http-api-nginx-http-server-zone-example.json)
- [plus-http-api-nginx-http-server-zones-map-example.json](examples/plus-http-api-nginx-http-server-zones-map-example.json)
- [plus-http-api-nginx-http-upstream-conf-server-example.json](examples/plus-http-api-nginx-http-upstream-conf-server-example.json)
- [plus-http-api-nginx-http-upstream-conf-server-map-example.json](examples/plus-http-api-nginx-http-upstream-conf-server-map-example.json)
- [plus-http-api-nginx-http-upstream-example.json](examples/plus-http-api-nginx-http-upstream-example.json)
- [plus-http-api-nginx-http-upstream-map-example.json](examples/plus-http-api-nginx-http-upstream-map-example.json)
- [plus-http-api-nginx-http-upstream-peer-example.json](examples/plus-http-api-nginx-http-upstream-peer-example.json)
- [plus-http-api-nginx-http-upstream-peer-map-example.json](examples/plus-http-api-nginx-http-upstream-peer-map-example.json)
- [plus-http-api-nginx-license-object-example.json](examples/plus-http-api-nginx-license-object-example.json)
- [plus-http-api-nginx-object-example.json](examples/plus-http-api-nginx-object-example.json)
- [plus-http-api-nginx-processes-example.json](examples/plus-http-api-nginx-processes-example.json)
- [plus-http-api-nginx-resolver-zone-example.json](examples/plus-http-api-nginx-resolver-zone-example.json)
- [plus-http-api-nginx-resolver-zones-map-example.json](examples/plus-http-api-nginx-resolver-zones-map-example.json)
- [plus-http-api-nginx-slab-zone-example.json](examples/plus-http-api-nginx-slab-zone-example.json)
- [plus-http-api-nginx-slab-zone-map-example.json](examples/plus-http-api-nginx-slab-zone-map-example.json)
- [plus-http-api-nginx-slab-zone-slot-example.json](examples/plus-http-api-nginx-slab-zone-slot-example.json)
- [plus-http-api-nginx-ssl-object-example.json](examples/plus-http-api-nginx-ssl-object-example.json)
- [plus-http-api-nginx-stream-keyval-zone-example.json](examples/plus-http-api-nginx-stream-keyval-zone-example.json)
- [plus-http-api-nginx-stream-keyval-zone-post-patch-example.json](examples/plus-http-api-nginx-stream-keyval-zone-post-patch-example.json)
- [plus-http-api-nginx-stream-keyval-zones-map-example.json](examples/plus-http-api-nginx-stream-keyval-zones-map-example.json)
- [plus-http-api-nginx-stream-limit-conn-zone-example.json](examples/plus-http-api-nginx-stream-limit-conn-zone-example.json)
- [plus-http-api-nginx-stream-limit-conn-zones-map-example.json](examples/plus-http-api-nginx-stream-limit-conn-zones-map-example.json)
- [plus-http-api-nginx-stream-server-zone-example.json](examples/plus-http-api-nginx-stream-server-zone-example.json)
- [plus-http-api-nginx-stream-server-zones-map-example.json](examples/plus-http-api-nginx-stream-server-zones-map-example.json)
- [plus-http-api-nginx-stream-upstream-conf-server-example.json](examples/plus-http-api-nginx-stream-upstream-conf-server-example.json)
- [plus-http-api-nginx-stream-upstream-conf-server-map-example.json](examples/plus-http-api-nginx-stream-upstream-conf-server-map-example.json)
- [plus-http-api-nginx-stream-upstream-example.json](examples/plus-http-api-nginx-stream-upstream-example.json)
- [plus-http-api-nginx-stream-upstream-map-example.json](examples/plus-http-api-nginx-stream-upstream-map-example.json)
- [plus-http-api-nginx-stream-upstream-peer-example.json](examples/plus-http-api-nginx-stream-upstream-peer-example.json)
- [plus-http-api-nginx-stream-upstream-peer-map-example.json](examples/plus-http-api-nginx-stream-upstream-peer-map-example.json)
- [plus-http-api-nginx-stream-zone-sync-example.json](examples/plus-http-api-nginx-stream-zone-sync-example.json)
- [plus-http-api-nginx-stream-zone-sync-zone-example.json](examples/plus-http-api-nginx-stream-zone-sync-zone-example.json)
- [plus-http-api-nginx-worker-example.json](examples/plus-http-api-nginx-worker-example.json)
- [plus-http-api-nginx-workers-map-example.json](examples/plus-http-api-nginx-workers-map-example.json)
- [stub-status-stub-status-example.json](examples/stub-status-stub-status-example.json)

## Capabilities

### Shared Per-API Definitions
- [NGINX Plus REST API](capabilities/shared/plus-http-api.yaml) - 30 resources, 62 operations covering dynamic configuration and real-time monitoring
- [NGINX Stub Status API](capabilities/shared/stub-status.yaml) - 1 resource, 1 operation for basic status metrics

### Workflow Capabilities

| Name | MCP Tools | Description |
|---|---|---|
| [Traffic Management](capabilities/traffic-management.yaml) | 11 | Dynamic upstream server management, load balancing, key-value store operations, and upstream health monitoring for HTTP and stream protocols. |
| [Monitoring and Observability](capabilities/monitoring-and-observability.yaml) | 14 | Comprehensive observability across connections, HTTP requests, server zones, location zones, caches, rate limiting, and upstream health. |

## Vocabulary
- [NGINX Vocabulary](vocabulary/nginx-vocabulary.yaml) - 24 resources, 6 actions, 3 APIs (Plus REST API, Stub Status, njs Scripting)

## Rules
- [NGINX Spectral Rules](rules/nginx-spectral-rules.yml) - 52 rules covering info/metadata, OpenAPI version, servers, paths, operations, tags, parameters, responses, schemas, security, HTTP method conventions, and general quality

## Maintainers
- Kin Lane (kin@apievangelist.com)
