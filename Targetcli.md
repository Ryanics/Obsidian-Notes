1. Set up zfs zvol. `sudo zfs create -V 4T tank/iscsi-vol`
	- Some optional tuning you might want: `sudo zfs set volblocksize=4k tank/iscsi-vol` changes the block size to 4kb chunks, (may help with performance may not)
	- `sudo zfs set compression=lz4 tank/iscsi-vol` which tells zfs to use lz4 compression.
2. `sudo targetcli` opens targetcli for 