#### Using USBMOUNT
1. Install USBMOUNT for auto-mounting 
   
   `sudo apt-get install usbmount`
2. If Apple file system then install HFS+ file system

   `sudo apt-get install hfsplus hfsutils hfsprogs gdisk`
3. If NTFS file system then install NTFS-3G file system

   `sudo apt-get install ntfs-3g fuseblk`
   
   Add NTFS & FUSEBLK to "*/etc/usbmount/usbmount.conf*" file:

   `FILESYSTEMS="vfat ... ntfs fuseblk"`
4. Set private mount to no in "*/lib/systemd/system/systemd-udevd.service*" file

   `PrivateMounts=no`
5. Reboot 


If the foregoing doesn't work then additional modification maybe necessary:

1. 
	 1. Set mount flag to shared in "*/lib/systemd/system/systemd-udevd.service*" file
      
       `MountFlags=shared`
	 2) Reboot

2. Set FS_MOUNTOPTIONS to read write in "*/etc/usbmount/usbmount.conf*" file:
   ```
   FS_MOUNTOPTIONS="-fstype=[FILE SYSTEM TYPE],umask=0000"
   FILE SYSTEM TYPE=vfat|ext2|ext3|ext4|hfsplus|ntfs fuseblk
   ```
