(This is for Arch)
## Install Tools
- `sudo pacman -S qemu-img`
- `sudo pacman -S ntfs-3g`
## Load the nbd kernel module
- `sudo modprobe nbd max_part=8`
## Connect the vhdx to an nbd device
- `sudo qemu-nbd --connect=/dev/nbd0 /path/to/your/file.vhdx`
## Check what partition it exposes
- `lsblk /dev/nbd0`
## Mount it
- `sudo mount /dev/nbd0p1 /mnt/vhdx` or `sudo ntfs-3g /dev/nbd0p1 /mnt/vhdx`
## Clean up
```
sudo umount /mnt/vhdx
sudo qemu-nbd --disconnect /dev/nbd0
sudo rmmod nbd
```
