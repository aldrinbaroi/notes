## Change Interface Name to ethX - CentOS / RHEL

### Step 1
Edit GRUB to add **net.ifname=0** and **biosdevname=0** to **GRUB_CMDLINE_LINUX**

Example:

```
GRUB_CMDLINE_LINUX="resume=/dev/mapper/cl_vm--manager-swap rd.lvm.lv=cl_vm-manager/root rd.lvm.lv=cl_vm-manager/swap net.ifnames=0 biosdevname=0"
```

### Step 2

```
grub2-mkconfig -o /boot/grub2/grub.cfg
```

### Step 3

Rename interface files from **ifcfg-enpXnX**, **ifcfg-ensX**, etc to **ifcfg-ethX**

Example:

```
mv ifcfg-enp5s0 ifcfg-eth0
```

### Step 4
Edit **ifcfg-ethX** to change **NAME** and **DEVICE** to match changed interface names.  

Example:

Change 

```
NAME=enp5s0
DEVICE=enp5s0
```

to

```
NAME=eth0
DEVICE=eth0
```

### Step 5
Reboot the system
