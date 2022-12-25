# dm-bow userspace command line utility

[Document](https://android.googlesource.com/kernel/common/+/refs/heads/android-4.19-q/Documentation/device-mapper/dm-bow.txt)

# Usage
```
mkfs.ext4 /dev/block/ram15

# create checkpoint
dmctl create test bow <start_sector> <num_sector> /dev/block/ram15
mount /dev/block/mapper/test mnt
busybox fstrim mnt
umount mnt
echo '1' > /sys/block/dm-x/bow/state

# modify the block device
mount /dev/block/mapper/test mnt
echo hello > mnt/a.txt

# commit changes
echo '2' > /sys/block/dm-x/bow/state

# or rollback
umount mnt
dmctl delete test
dm-bow-rollback /dev/block/ram15 0
```
