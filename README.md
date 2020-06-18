```
diskutil info disk2 | grep "Disk Size"
184000000
32010928128 - 31306285056 =
704643072
diskutil partitionDisk disk2 MBR fat32 "SWITCH" 704643072 fat32 "EMUMMC" 31306285056

-- output --
/dev/disk2 (external, physical):
#: TYPE NAME SIZE IDENTIFIER
0: FDisk_partition_scheme \*32.0 GB disk2
1: DOS_FAT_32 SWITCH 704.6 MB disk2s1
2: DOS_FAT_32 EMUMMC 31.3 GB disk2s2

diskutil list disk2

diskutil unmount disk2s2

sudo dd if=/dev/zero of=/dev/disk2s2 bs=1m count=1
sudo dd if=/dev/zero of=/dev/disk2s2 seek=29853 bs=1m count=1
```
