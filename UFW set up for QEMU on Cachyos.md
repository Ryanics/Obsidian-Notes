1.`sudo ufw allow in on virbr0` to allow incoming traffic on the virtual bridge
2.`sudo ufw allow out on virbr0` to allow outgoing traffic on the virtual bridge
3.`sudo vim /etc/ufw/sysctl.conf` to modify the config file for UFW (uncomplicated firewall). Uncomment the line that says `net\ipv4\ip_forward=1`. This is for network variables.
4.`sudo vim /etc/defaults/ufw` to modify the default config for specific rules to follow. Find the line that says `DEFAULT_FORWARD_POLICY="DROP"` and change this to say, `DEFAULT_FORWARD_POLICY="ACCEPT"` 
5.`sudo ufw reload`. This will reload UFW with the configs that you set and should then allow for qemu to be connected online (for cachy installs and whatnot)