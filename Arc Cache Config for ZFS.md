
Arc stands for Adaptive Replacement Cache, which optimizes performance with frequently used data blocks.


Make sure you use Arc cache, and have it be large enough for zfs. 

To get the ARC cache to use a good chunk of the server's memory, what's best is to set it to **193273528320** bytes.

In order to change it, you must run `echo 193273528320 | sudo tee /sys/module/zfs/parameters/zfs_arc_max` which will echo the output of the number of bytes. You can verify that it's been changed in the zfs_arc_max file by using `cat`, and running the command `cat /sys/module/zfs/parameters/zfs_arc_max` which SHOULD echo the number, `193273528320`.

From there, use this command, `sudo nvim /etc/modprobe/zfs.conf` to open the *zfs.conf* file and add the line `options zfs zfs_arc_max=193273528320`.

Once you are saved, run `sudo dracut --regenerate-all --force
`. 
This command overrides the current intramfs image with a new image that is generated. This is used because we added a new line in the zfs.conf file in modprobe.