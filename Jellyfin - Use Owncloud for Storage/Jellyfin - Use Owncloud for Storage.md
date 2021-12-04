# Jellyfin - Use Owncloud for Storage

### Simply serve media from Owncloud

1. Install Webdav pacakge<br/>
   On Ubuntu you can use the following command to install Webdav package  
   
       sudo apt-get install davfs2
1. Mount Owncloud  
   You will be prompted to enter user name & password. Provider Owncloud user name & password.

       sudo mount -t davfs -o noexec http://OWNCLOUD_HOST:PORT/remote.php/webdav MOUNT_POINT
1. In Jellyfin, add media folders from the MOUNT_POINT folder 



### Keep media & NFO files in separate directories

**Suppose:**  
- Owncloud songs folder: MOUNT_POINT/Media/Songs/  
- Owncloud metadata folder: MOUNT_POINT/Media/Metadata/Songs  
- Jellyfin local songs folder: /jellyfin-repo/Songs   
*NOTE: Jelyfin folder must be empty*

1. Install **unionfs-fuse** package  
   On Ubuntu you can use the following command to install unionfs-fuse package  
   
       sudo apt-get install unionfs-fuse
3. Follow the instructions under **_Simply serve media from Owncloud_** to mount Owncloud 
4. Using "unionfs" mount Owncloud songs folder as readonly and Owncloud metadata folder with write permission under Jellyfin folder

       UPPER_DIR=MOUNT_POINT/Media/Metadata/Songs
       LOWER_DIR=MOUNT_POINT/Media/Songs/
       OVERLAY_DIR=/jellyfin-repo/Songs
       unionfs -o cow,max_files=32768 \
        -o allow_other,use_ino,suid,dev,nonempty \
         $UPPER_DIR=RW:$LOWER_DIR=RO \
         $OVERLAY_DIR
 5. In Jellyfin, add media folders from the OVERLAY_DIR folder 
 
 
