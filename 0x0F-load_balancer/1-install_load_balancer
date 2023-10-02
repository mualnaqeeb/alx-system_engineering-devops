#!/usr/bin/env bash
# Installs and setup haproxy

# Add HAProxy PPA
apt-get -y update
apt-get -y upgrade
apt-get -y install software-properties-common
add-apt-repository -y ppa:vbernat/haproxy-2.5
apt-get -y update

echo "ENABLED=1" > /etc/default/haproxy

# Listen to web1 and web2 servers                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
echo "
   listen load_balancer
   bind *:80
   mode http
   balance roundrobin
   option httpclose
   option forwardfor
   server 372325-web-01 100.27.13.183:80 check
   server 372325-web-02 54.90.6.206:80 check
" >> /etc/haproxy/haproxy.cfg

service haproxy start
