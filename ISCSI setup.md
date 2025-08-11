Before you start: Make sure 2 things are set:

1. Optical/Fiber card's ipv4 address is set using `dhclient ens2f1`  to have DHCP set up for connecting with an IP address lease, subnet mask, default gateway, DNS servers and other network configuration parameters. (not needed.) `ip addr add (ip address)/24 dev ens2f1` sets a static ip address for the interface.
2. And make sure that port 3260(tcp) is open. `sudo firewall-cmd --zone=public --add-port=3260/tcp --permanent` Reload firewalld with `sudo firewall-cmd --reload` and you're good.

Now that the device that you want to use for connecting your desktop to the drive shelf has been set up with an ipv4 address of your choice, and that port 3260 on your server has been opened, you can set up iscsi.

1. Make sure Iscsi is installed on your client, `sudo dnf install iscsi-initiator-utils`.
2. Install targetcli on the server. `sudo dnf install targetcli`, if you haven't done so already. Make sure that targetcli is enabled and started after targetcli has been set up. See the Targetcli section for basic set up of targetcli. 
3. Make sure to check in `/etc/iscsi/initiatorname.iscsi` to verify the client's IQN matches the targetcli configuration on the server. If not added, add this line or change this line to match the client IQN in the server: `InitiatorName=iqn.2025-0`
4. Run **iscsiadm** to discover the target.