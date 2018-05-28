# NGINX-Reverse-Proxy-Config

## Summary
This proxy was originally designed to circumvent an Orwellion ISP who was attempting to block incoming traffic on ports 80 & 443. This is accomplished by hosting services locally on non-standard web ports and then using a proxy running on AWS EC2 to redirect traffic to hidden `IP:Port` combinations. Domain DNS is pointed at said proxy, not home server. 

## Instructions for Use:
0) Install all NGINX prerequisites.   
1) Download NGINX, zlib, pcre source code files to the same directory.  
2) Extract all tarballs.  
3) CD into NGINX directory.  

4) Compile NGINX with additional enterprise modules.  
```
./configure --sbin-path=/usr/local/nginx/ --conf-path=/etc/nginx/nginx.conf --pid-path=/usr/local/nginx/nginx.pid --with-pcre=../pcre-8.41/ --with-zlib=../zlib-1.2.11/ --with-http_ssl_module --with-stream --with-http_stub_status_module --with-http_v2_module
```

5) Install NGINX
```
make
sudo make install
```

6) Copy configuration files and systemd modules to their locations
```
sudo cp ./NGINX-Reverse-Proxy-Config/{nginx,status}.conf /etc/nginx/
sudo cp ./NGINX-Reverse-Proxy-Config/nginx{,_health}.service /usr/lib/systemd/system/
```

7) Create symlinks for compiled nginx binary
```
sudo ln -s /usr/local/nginx/nginx /usr/bin/nginx
sudo ln -s /usr/local/nginx/nginx /usr/sbin/nginx
```

8) Create `/etc/nginx/passwords` file and install Netdata

9) Enable & start NGINX
```
sudo systemctl daemon-reload
sudo systemctl enable nginx nginx_health
sudo systemctl start nginx nginx_health
```

## Proxy also yields other benefits such as:
```
- Enhanced Security
- Enhanced Logging
- WhoIs Protection (Not that that matters in my circumstance)
- Automatic SSL Termination for all services
- Better website performance/caching
- Simple password-based authentication
```

## NGINX is currently proxying the following services for my domain:
```
- Apache
- Plex Media Server
- Deluge Web Interface
- Grafana
- NetData
- OpenVPN
- Tautulli
- Sonarr
- Radarr
- & More!
```
