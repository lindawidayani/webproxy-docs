# Technical Guidelines and Architecture Overview

Welcome to the technical guidelines for **WebProxy.co.id** and the **Blue Proxy Browser**. This document outlines the underlying architecture of our services, best practices for optimal performance, and basic troubleshooting steps.

## 1. System Architecture Overview

To provide a fast and secure browsing experience, our platform utilizes a modern networking stack:

### 🌐 WebProxy.co.id (Web Platform)
- **Edge Routing & Security:** All incoming traffic is routed through **Cloudflare** in Strict Mode, ensuring DDoS protection and enforcing SSL/TLS encryption.
- **Web Server:** We utilize highly optimized **Nginx** server blocks configured with fast caching mechanisms (FastCGI and Redis) to minimize latency on static assets.
- **Proxy Engine:** The core web proxy is powered by a high-performance **Node.js** backend, enabling asynchronous request handling for seamless streaming and browsing.

### 📱 Blue Proxy Browser (Android App)
- **Local Tunneling:** The app utilizes the native **Android VpnService** API to create a secure local tunnel, ensuring all app-level traffic is securely routed.
- **Encrypted DNS:** To prevent ISP tracking and DNS hijacking, the browser integrates **DNS over HTTPS (DoH)** and **DNS over QUIC (DoQ)** protocols.
- **Custom WebView:** Built on an optimized Android WebView, integrated with native AdBlock technology to filter out malicious scripts and heavy ad trackers before they load.

## 2. Best Practices for Optimal Performance

To get the most out of our proxy services, we recommend the following configurations:

### For Web Users (WebProxy.co.id)
- **Media Streaming:** For heavy media streaming, ensure your browser is updated to the latest version to support modern HTML5 video decoding.
- **Cache Management:** If a proxied website fails to load correctly, try clearing your browser's local cache or opening the web proxy in an Incognito/Private window to force a fresh session.

### For Mobile Users (Blue Proxy Browser)
- **Enable Encrypted DNS:** For maximum privacy, navigate to the app settings and ensure that DoH (DNS over HTTPS) is enabled.
- **Battery Optimization:** Android systems may aggressively close background processes. If you experience unexpected disconnections, exclude the Blue Proxy Browser from your device's aggressive battery optimization settings.
- **AdBlock Configuration:** The built-in AdBlock is enabled by default to save bandwidth and improve load times. If a specific website breaks (e.g., anti-adblock walls), you can temporarily pause the AdBlock feature from the browser menu.

## 3. Technical Troubleshooting

If you encounter technical issues, please check the following before submitting a bug report:

- **ERR_CONNECTION_TIMED_OUT:** The destination server might be down, or it is actively blocking proxy IP ranges. Try accessing a different website to verify if the issue is global or site-specific.
- **Broken Layouts/CSS:** Some websites use strict Cross-Origin Resource Sharing (CORS) policies or rely heavily on third-party JavaScript that may not route perfectly through a web proxy. Using the Blue Proxy Browser app usually resolves these client-side rendering issues.
- **DNS Resolution Failures:** If using the Android app, try switching between standard DNS and DoH/DoQ in the settings.

## 4. Security Disclosures

We actively monitor our Node.js and server environments for vulnerabilities. If you are a security researcher and have found a vulnerability within our web proxy engine or Android application, please do not open a public issue. Instead, contact us directly via our official support email found on the website footer.

---
*For general bug reports, please use the [Issue Tracker](../../issues).*
