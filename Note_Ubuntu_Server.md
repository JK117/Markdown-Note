# Linux/Ubuntu Server Note

***
## Create Disk Image on MacOS
1. Prepare disk image file. Decompress into `.img` format if necessary.
2. Prepare SD card or other external storage device, check the device number:
```
$ diskutil list
```
Confirm your external storage device number like: `/dev/disk2`
Then unmount the device using: 
```
$ diskutil unmountDisk <device_number>
```
You will see the fopllowing response if success:
```
Unmount of all volumes on disk2 was successful
```
3. Write in disk image using `dd` command:
```
$ sudo dd if=<input_img_file> of=<device_number> bs=1m
```
`bs` suggests block size, you can also add `r` to device number like `/dev/rdisk2` to improve performance. Successful outputs:
```
2502+1 records in
2502+1 records out
2624517120 bytes transferred in 290.728240 secs (9027390 bytes/sec)
```

***
## Configure Wifi
Amend netplan file from terminal:
```
$ sudo nano /etc/netplan/01-netcfg.yaml
```
Edit config info as:
```
network:
  version: 2
  renderer: networkd
  wifis:
    wlan0:
      dhcp4: true
      dhcp6: true
      optional: true
      access-points:
        "network_ssid_name":
          password: "**********"
```
Next, do:
```
$ sudo netplan generate
$ sudo netplan apply
```
Reboot and test:
```
$ ping -c3 8.8.8.8
```
If you get ping returns, you are all set.
Reference: https://netplan.io/examples

***
## SYSTEMCTL
A Linux systems provide a variety of system services such as:
```
process management
login
syslog
cron
...
```
and network services such as:
```
remote login
e-mail
printers
web hosting
data storage
file transfer
domain name resolution (using DNS)
dynamic IP address assignment (using DHCP)
...
```
Technically, a service is a process or group of processes (daemons) running continuously in the background, waiting for requests to come in (especially from clients).

Linux supports different ways to manage (start, stop, restart, enable auto-start at system boot, etc.) services, typically through a process or service manager. Most if not all modern Linux distributions now use the same process manager: `systemd`.

Read Also: The Story Behind `init` and `systemd`: Why `init` Needed to be Replaced with `systemd` in Linux.

Systemd is a system and service manager for Linux; a drop-in replacement for the init process, which is compatible with `SysV` and `LSB` init scripts and the `systemctl` command is the primary tool to manage `systemd`.

To list all loaded services on your system:
```
$ systemctl [list-unit] --type=service
```
To list all active services (both running and exited) on your system:
```
$ systemctl [list-unit] --type=service --state=active
```
To list all running services on your system:
```
$ systemctl [list-unit] --type=service --state=running
```

