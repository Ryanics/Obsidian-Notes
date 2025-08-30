Before you start: Make sure 2 things are set:

1. Optical/Fiber card's ipv4 address is set using `dhclient ens2f1`  to have DHCP set up for connecting with an IP address lease, subnet mask, default gateway, DNS servers and other network configuration parameters. (not needed.) `ip addr add (ip address)/24 dev ens2f1` sets a static ip address for the interface.
2. And make sure that port 3260(tcp) is open. `sudo firewall-cmd --zone=public --add-port=3260/tcp --permanent` Reload firewalld with `sudo firewall-cmd --reload` and you're good.

Now that the device that you want to use for connecting your desktop to the drive shelf has been set up with an ipv4 address of your choice, and that port 3260 on your server has been opened, you can set up iscsi.

1. Make sure Iscsi is installed on your client, `sudo dnf install iscsi-initiator-utils`.
2. Install targetcli on the server. `sudo dnf install targetcli`, if you haven't done so already. Make sure that targetcli is enabled and started after targetcli has been set up. See the Targetcli section for basic set up of targetcli. 
3. Make sure to check in `/etc/iscsi/initiatorname.iscsi` to verify the client's IQN matches the targetcli configuration on the server. If not added, add this line or change this line to match the client IQN in the server: `InitiatorName=iqn.2025-08.com.fedora:client`
4. Run **iscsiadm** to discover the target. `sudo iscsidam -m discovery -t sendtargets -p (ip that was setup in targetcli)`. If the target is not found, verify physical connections. Also check to make sure the network device you want to use is set up on the server and verify that port 3260 is open on the server. If you find the target, you can go forward to the next step.
5. Log into the target. `sudo iscsiadm -m node -T iqn.2025-08.com.example:tank -p (target_ip_from_targetcli) --login`. If you have an authentication error, check to verify that you have the correct IQN in the initiatorname.iscsi file in `/etc/iscsi`. 
6. Once you have the connection up and know the configs aren't going to be changed any more, you can make the login persistent. `sudo iscsiadm -m node -T iqn.2025-08.com.example:tank -p (target_ip_from_before) --op update -n node.startup -v automatic`.

Regardless of if you are on step 5 or step 6, verify the drive/zvol is showing correctly with lsblk. 

If you need to clear the config for some reason, use `sudo targetcli` and then type 'clearconfig' to do so