1. Set up zfs zvol. `sudo zfs create -V 4T tank/iscsi-vol`
	- Some optional tuning you might want: `sudo zfs set volblocksize=4k tank/iscsi-vol` changes the block size to 4kb chunks, (may help with performance may not)
	- `sudo zfs set compression=lz4 tank/iscsi-vol` which tells zfs to use lz4 compression.
2. `sudo targetcli` opens targetcli for configuring the connection for iscsi.
3. `/backstores/block create tank_games /dev/zvol/tank/iscs-vol` Creates a block storage device named tank_games and points it toward the zvol that got set up
4. `/iscsi create iqn.2025-08.com.example:games` Make an IQN, it can be in any format that you'd like, but this format is good practice. 
5. ``/iscsi/iqn.2025-08.com.example:games/tpg1 set attribute authentication=0`` and `/iscsi/iqn.2025-08.com.example:games/tpg1 set attribute generate_node_acls=0` Disables CHAP and automatic ACL generation, for manual control, especially since this drive will not be pushed over the internet.
6. `/iscsi/iqn.2025-08.com.example:games/tpg1/portals delete 0.0.0.0 3260` then `/iscsi/iqn.2025-08.com.example:games/tpg1/portals create (ip address here) 3260` This adds the ip address that you previously set up and has it ready to broadcast and listen on tcp port 3260.
7. ``/iscsi/iqn.2025-08.com.example:games/tpg1/luns create /backstores/block/tank_games`` Sets up a LUN, a Logic Unit Number, a logical number with a specific numerical identifier 