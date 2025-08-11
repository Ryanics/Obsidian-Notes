Before you start: Make sure 2 things are set:

1. Optical/Fiber card's ipv4 address is set using `dhclient ens2f1`  to have DHCP set up for connecting with an IP address lease, subnet mask, default gateway, DNS servers and other network configuration parameters. (not needed.) `ip addr add (ip address)/24 dev ens2f1` sets a static ip address for the interface.
2. And make sure that port 3260(tcp) is open. `sudo firewall-cmd --zone=public --add-port=3260/tcp --permanent` Reload firewalld with `sudo firewall-cmd --reload` and you're good.