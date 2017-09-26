Enable full read and write support for NTFS partitions
=

Install `ntfs-3g`
> sudo apt-get install ntfs-3g

List the partition tables
> sudo fdisk -l

List the mounted file systems
> mount -l | grep /dev/sd

Unmount if necessary
> sudo umount /dev/sda1

Mount
> sudo mount /dev/sda1 /media/pi/hdd

Get drive UUID
> lsblk -f

Setup manual mount
-

Open `fstab` with text editor
> sudo nano /etc/fstab

Add new line
> /dev/sda1 /media/pi/hdd ntfs rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,uhelper=udisks2 0 0

Create directory
> sudo mkdir /media/pi/hdd

Mount 
> sudo mount /dev/sda1



