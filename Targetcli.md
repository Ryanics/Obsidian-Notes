1. Set up zfs zvol. `sudo zfs create -V 4T tank/iscsi-vol`
	- Some optional tuning you might want: `sudo zfs set volblocksize=4k tank/iscsi-vol` changes the block size to 4kb chunks, (may help with performance may not)
	- `sudo zfs set compression=lz4 tank/iscsi-vol` which tells zfs to use lz4 compression.
2. `sudo targetcli` opens targetcli for configuring the connection for iscsi.
3. `/backstores/block create tank_games /dev/zvol/tank/iscs-vol` Creates a block storage device named tank_games and points it toward the zvol that got set up
4. `/iscsi create iqn.2025-08.com.example:games` Make an IQN, it can be in any format that you'd like, but this format is good practice. 
5. ``/iscsi/iqn.2025-08.com.example:games/tpg1 set attribute authentication=0`` and ``