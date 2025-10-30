1.`sudo ufw allow in on virbr0` to allow incoming traffic on the virtual bridge
2.`sudo ufw allow out on virbr0` to allow outgoing traffic on the virtual bridge
3.`sudo vim /etc/ufw/sysctl.conf` to modify the config file for UFW (uncomplicated firewall). Uncomment the line that says ``