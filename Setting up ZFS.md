1. Make sure open-zfs is installed. 
		-remove zfs-fuse if it's installed, `rpm -e --nodeps zfs-fuse`
		-Add the repo 'dnf install -y https:'
2. Check zfs to verify there isn't a zfs pool set up. `sudo zfs list` and check `sudo zpool status` 