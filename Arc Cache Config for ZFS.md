
Arc stands for Adaptive Replacement Cache, which optimizes performance with frequently used data blocks.


Make sure you use Arc cache, and have it be large enough for zfs. 

To get the ARC cache to use a good chunk of the server's memory, what's best is to set it to **193273528320** bytes.

In order to change it, you must run 