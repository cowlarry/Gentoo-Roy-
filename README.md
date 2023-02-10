# Gentoo-Roy-
---------------------------------------------------------------
  - lsblk - to display how much partition you have before configure it -
 - now you should not see the mountpoints 
if desired, run these:
 - umount -f -l /mnt/gentoo/boot/efi &
 - umount -f -l /mnt/gentoo/boot/ &
 - swapoff /dev/{SWAP} &
 - umount /mnt/gentoo/home 
-------------------
lets configure the disk
cfdisk /dev/nvme0n1
lsblk:
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
nvme0n1     259:0    0 476.9G  0 disk 
├─nvme0n1p1 259:1    0   512M  0 part
├─nvme0n1p2 259:2    0     8G  0 part
└─nvme0n1p3 259:3    0   256G  0 part
-------------------
now create /mnt/gentoo :
mkdir -p /mnt/gentoo/boot/efi 
mkdir -p /mnt/gentoo 
mkfs.vfat -F 32 /dev/nvme0n1p1 
mkswap /dev/nvme0n1p2
mkfs.ext4 /dev/nvme0n1p3 
mount /dev/nvme0n1p1 /mnt/gentoo/boot/efi
swapon /dev/nvme0n1p2 
mount /dev/nvme0n1p3 /mnt/gentoo
cd /mnt/gentoo 
lets take a deep breath,we are getting closer to larry and tux(again)!
-----------------------------------------------------------------
