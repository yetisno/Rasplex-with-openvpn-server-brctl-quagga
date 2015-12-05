# Rasplex-with-openvpn-server-brctl-quagga(zebra, ripd ...)
## Note! This is for Raspberry Pi 2 (it's tested on Rasplex 0.7.1)

copy files to `/` directory, and will get brctl, openvpn(server), zebra, ripd function.

the  `/` is readonly, you must follow steps below: 

1. copy `/flash/SYSTEM` to your computer and name it `SYSTEM.old`.
2. unsquashfs `SYSTEM.old` to `target` folder.
3. patch file into `target` folder. (not replace, it's add.)
4. mksquashfs `target` to `SYSTEM`.
5. copy `SYSTEM` to Rasplex and place it to `/storage/.update/SYSTEM`.
6. go Rasplex shell and enter follow script.
```bash
# calculate md5 of SYSTEM and write to /storage/.update/SYSTEM.md5
md5sum /storage/.update/SYSTEM > /storage/.update/SYSTEM.md5;
# copy kernel image to /storage/.update/KERNEL
cp /flash/kernel.img /storage/.update/KERNEL;
# calculate md5 of KERNEL and write to /storage/.update/KERNEL.md5
md5sum /storage/.update/KERNEL > /storage/.update/KERNEL.md5;
# reboot for update image
reboot;
```

after reboot, you will get a Rasplex with advance network function.

download <http://rasplex.com>