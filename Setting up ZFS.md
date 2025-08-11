1. Make sure open-zfs is installed. 
		-remove zfs-fuse if it's installed, `rpm -e --nodeps zfs-fuse`
		-Add the repo `sudo dnf install -y https://zfsonlinux.org/fedora/zfs-release-2-8$(rpm --eval "%{?dist}").noarch.rpm`
		-Install kernel headers (if not already installed) `sudo dnf install -y kernel-devel-$(uname -r | awk -F'-' '{print $1}')`
		-Install the zfs packages themselves `sudo dnf install zfs -y `
		-Load the kernel module `modprobe zfs`
2. Check zfs to verify there isn't a zfs pool set up. `sudo zfs list` and check `sudo zpool status` 
3. Check multipath for multipath devices and their drives. Use the multipath devices in the next step. `sudo multipath -ll`
4. Create a zfs pool. `sudo zpool create (name_of_pool) (type_of_raid) /dev/dev1 /dev/dev2 (all devices you want added to the pool` The command used for the current set up is `sudo zpool create tank raidz2 /dev/mapper/mpatha /dev/mapper/mpathb /dev/mapper/mpathc /dev/mapper/mpathd /dev/mapper/mpathf -f`
5. After setting up the pool, it's good to check the status of the pool to see if it got properly set up, if you have all devices apart of the pool, and if there are any errors. You can do this with `sudo zpool status`.
6. 