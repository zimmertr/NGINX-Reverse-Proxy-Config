# NGINX-Reverse-Proxy-Config
This proxy was originally designed to circumvent an Orwellion ISP who was attempting to block incoming traffic on ports 80 & 443. This is accomplished by hosting services locally on non-standard web ports and then using a proxy running on AWS EC2 to redirect traffic to hidden `IP:Port` combinations. Domain DNS is pointed at said proxy, not home server. 

Proxy also yields other benefits such as:
```
- Enhanced Security
- Enhanced Logging
- WhoIs Protection (Not that that matters in my circumstance)
- Automatic SSL Termination for all services
- Better website performance/caching
- Simple password-based authentication
```
