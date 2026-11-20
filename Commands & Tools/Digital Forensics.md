## Installs (Arch)
| **Package** | **Command**                |
| ----------- | -------------------------- |
| sleuthkit   | `sudo pacman -S sleuthkit` |
| ftkimager   | `yay -S ftkimager`         |
| sha256sum   | `sudo pacman -S sha256sum` |
## Clone image
`ftkimager /dev/sdx /path/drive.img`
## Hash the image 
`sha256sum evidence-drive.img > evidence-drive.img.sha256`
## Check partition layout
`mmls evidence-drive.img `
## Get partition information
`fsstat -o <partion> evidence-drive.img `
## List files/directory
`fls -o ? -r -p evidence-drive.img | less`
## Recover images from bin (win)
`icat -r -o ? evidence-drive.img ? > file_name `