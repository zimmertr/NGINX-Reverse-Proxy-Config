# NGINX-Reverse-Proxy-Config
Configuration file used by my NGINX Reverse Proxy.

This proxy was originally designed to circumvent an Orwellion ISP who was attempting to block incoming traffic on ports 80 & 443. This is accomplished by hosting services locally on non-standard web ports and then using a proxy running on AWS EC2 to redirect traffic to hidden IP:Port combinations. Domain DNS is pointed at said proxy, not home server. 

Proxy also yields other benefits such as enhanced security, whois/identity protection (not that that matters for a portfolio website), and automatic SSL termination for all services.
