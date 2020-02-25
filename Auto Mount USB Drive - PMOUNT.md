### Using PMOUNT  
*** *Works on Debian variants* ***

1. Install pmount if not installed 

   `sudo apt-get install pmount`
2. Create an UDEV rule
   ```
   sudo cat<<-EOF > /etc/udev/rules.d/auto-mount-usb-drives.rules 
   ACTION=="add", KERNEL=="sd[a-z][0-9]", TAG+="systemd", ENV{SYSTEMD_WANTS}="auto-mount-usb-drives-handler@%k
   EOF
   ```
3. Create a SYSTEMD service
   ```
   sudo cat<<-EOF > /lib/systemd/system/auto-mount-usb-drives-handler@.service
   [Unit]
   Description=Auto Mount USB Drives
   BindsTo=dev-%i.device
   After=dev-%i.device

   [Service]
   Type=oneshot
   RemainAfterExit=yes
   ExecStart=/usr/local/bin/auto-mount-usb-drives %I
   ExecStop=/usr/bin/pumount /dev/%I
   EOF
   ```
4. Create a script for auto mounting
   ```
   sudo cat<<-EOF > /usr/local/bin/auto-mount-usb-drives
   #!/bin/bash
   PART=$1
   FS_LABEL=`lsblk -o name,label | grep ${PART} | awk '{print $2}'`
   if [ -z ${FS_LABEL} ]
   then
       /usr/bin/pmount --umask 000 --noatime -w --sync /dev/${PART} /media/${PART}
   else
       /usr/bin/pmount --umask 000 --noatime -w --sync /dev/${PART} /media/${FS_LABEL}_${PART}
   fi
   EOF
   sudo chmod 755 /usr/local/bin/auto-mount-usb-drives
   ```
