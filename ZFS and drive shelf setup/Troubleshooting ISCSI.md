
When you are trying to get the connection set up, you do not need to have iscsi-initiator-utils on your host machine. You just need to have those tools on the client machine. 

If you have having issues with ISCSI not finding the iqn, and by extension the raid drive, there are a few things you can check.
1. Check physical connections, try not to unplug if you dont have to but if they were loose or unplugged for some reason, make sure to check and verify before you do anything else.
2. Verify the host machine's targetcli configuration. If it is empty, make sure to load the configuration, then restart targetcli. 
3. Verify the client iqn that is set up in targetcli is properly set up on the client machine. You can verify this by opening a terminal and going to /etc/iscsi `cd /etc/iscsi`. Now, use open the initiator file, with  `sudo nvim initiator.iscsi`. Once nvim, or your chosen terminal based text editor opens the file, you can then check the IQN and change it if needbe. 
4. Sometimes the answer to what may be going on is as simple as an incorrect iface configuration. Open a terminal and type `ip a`, and observe the devices with ip addresses here that you had previously set up. If you have a specfic network scheme, like using a 172.28.0.0 ip address for example, check to see if one of those devices is displaying the ip address. If not, change the IP 