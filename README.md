# Commands Bible

- [Operating System/Kernel](#operating-systemkernel)
- [Hardware](#hardware)
- [Graphics](#graphics)
- [Networking](#networking)
- [User](#user)
- [Programs](#programs)
- [Files/Folders](#filesfolders)

## Operating System/Kernel

#### Show OS/kernel information
```sh
uname -r ; uname -a
```
#### Show memory information
```sh
free -h
```
#### Show OS/kernel log
```sh
dmesg
```
#### Show rc init active services (BSD)
```sh
cat /etc/rc.conf
```
#### Show all normal users on the system
```sh
ls /home
```
#### Show all your storage devices
```sh
sudo fdisk -l
```
#### Show all your configured mountpoints
```sh
cat /etc/fstab
```
#### Show information about your partitions/filesystems
```sh
df -h
```
#### Show the active modules on the kernel
```sh
ls /lib/modules/$(uname -r)
```
#### Show all available modules on the kernel
```sh
ls /lib/modules/$(uname -r)/kernel/drivers/
```
#### Show status of the modules on the kernel
```sh
lsmod
```
#### Load a module to the kernel (Linux)
```sh
sudo modprobe module-name
```
#### Load a module to the kernel (BSD)
```sh
kldload module-name
```
#### Remove a module from the kernel
```sh
sudo modprobe -r module-name
```
#### Remove a module from the kernel
```sh
sudo rmmod module-name
```
#### Unmount one filesystem
```sh
sudo umount /your/path
```
#### Unmount all filesystems except root filesystem
```sh
sudo umount -a
```
#### Restart the system (systemd)
```sh
sudo systemctl reboot
```
#### Show active swap partition/file
```sh
sudo swapon
```
#### Enable mounted swap (on /etc/fstab or swapfile)
```sh
sudo swapon -a
```
#### Disable swap
```sh
sudo swapoff -a
```
#### Show the available/active I/O schedulers for your disk (X is your disk letter)
```sh
cat /sys/block/sdX/queue/scheduler
```
#### Show all available I/O schedulers for all disks
```sh
grep "" /sys/block/*/queue/scheduler
```
#### Change your active disk I/O scheduler
```sh
echo scheduler_name > /sys/block/sdX/queue/scheduler
```

## Hardware

#### Show CPU information
```sh
lscpu
```
#### Show your USB device tree (motherboard ports/bandwidth)
```sh
lsusb -t
```
#### Show your PCI device tree (same as above)
```sh
lspci -tv
```
#### Advanced memory information
```sh
cat /proc/meminfo
```
#### Advanced memory information (dmidecode)
```sh
sudo dmidecode -t memory
```
#### Show how fast your hard disk read the data (X is the letter of your disk, use fdisk -l to check)
```sh
hdparm -t /dev/sdX
```
#### Show all active network interfaces
```sh
ifconfig
```
#### Show all active wireless network interfaces
```sh
iwconfig
```
#### Show available CPU governors
```sh
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
#### Show current CPU governor
```sh
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
#### Activate a CPU governor (most used are "powersave","performance" and "ondemand")
```sh
echo governor_name | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

## Graphics

#### Start X11 from terminal (the command on .xinitrc will run)
```sh
startx
```
#### Show active program on X11 init config file ("startx" read this file)
```sh
cat ~/.xinitrc
```
#### Show your OpenGL driver name/version
```sh
glxinfo | grep OpenGL
```
#### Show your Vulkan driver name/version
```sh
vulkaninfo | grep Vulkan
```
#### Show if you have direct rendering enabled for GPU-oriented software
```sh
glxinfo | grep "direct rendering"
```
#### Environment variable to make a program use a different [Mesa3D](https://mesa3d.org/) driver
```
MESA_LOADER_DRIVER_OVERRIDE=driver_name program
```
#### Environment variable to force a program to use [LLVMpipe](https://docs.mesa3d.org/drivers/llvmpipe.html) (OpenGL CPU emulation)
```
LIBGL_ALWAYS_SOFTWARE=true
```
(if you want to force all programs of the system to use LLVMpipe add this `export LIBGL_ALWAYS_SOFTWARE=true` command to your `.bashrc` file on your user folder or your shell configuration file, it's useful when the OpenGL version of your GPU is too low because your GPU is very old, it will make all games run but you can get very bad FPS if the game is vertex intensive)

## Networking

#### Show system DNS name
```sh
hostname
```
#### Show all network addresses of your system
```sh
hostname -I
```
#### Ping any website or IP to see if it's online or measure your connection latency
```sh
ping website-link or ip-address
```
#### Show website registration information
```sh
whois https://websitename.com
```

## User

#### `Ctrl+C` | This keyboard shortcut cancel any command process

#### Clean your terminal content/output
```sh
clear
```
#### Run previous command
```sh
!!
```
#### Ask root password to switch user for root with echo
```sh
su -
```
#### Ask current user password to become root
```sh
sudo -i
```
#### Run as root per-command with root environment variables
```sh
doas command
```
#### Run any command with temporary root privileges and current user environment variables
```sh
sudo command
```
#### Run previous command as root temporarily
```sh
sudo !!
```
#### Exit root privileges or exit terminal session
```sh
exit
```
#### Current active user on terminal shell/$PATH
```sh
whoami
```
#### Environment variable for user folder
```sh
$HOME
```
#### Show your default terminal shell
```sh
echo $SHELL
```
#### Show your current terminal shell
```sh
echo $0
```
#### Show your installed terminal shells (active on $PATH)
```sh
cat /etc/shells
```
#### Change your default terminal shell permanently (common path is /usr/bin)
```sh
chsh -s /path/of/your/shell
```
#### Add an alias/abbreviation for a command on your terminal shell (add this command on your shell configuration file to be permanent, generally a file named `.name-of-your-shell-rc` on your user folder)
```sh
alias name='command'
```
#### Change the user password
```sh
passwd name-of-the-user
```
#### Show the commands history
```sh
history
```
#### Show the commands with the name specified in history
```sh
history name
```
#### Change the ownership of a file/folder/device/mounted partition (recursively)
```sh
sudo chown -R user_name:group-name directory-name
```
Or
```sh
chown username file-name
```

## Programs

#### Show all system-wide common programs
```sh
ls /bin
```
#### Show all system programs
```sh
ls /sbin
```
#### Show the specified text on terminal
```sh
echo text
```
#### Show the directories in $PATH environment variable
```sh
echo $PATH
```
#### Show the dependencies (shared libraries) used by a program
```sh
ldd program_name
```
#### Add a new PATH to your terminal shell
```sh
export PATH=$PATH:/your/directory
```
#### Restore the terminal variables to their default values
```sh
reset
```
#### Count the time taken for a program to run the command
```sh
time command
```
#### `name*` | In some programs the * symbol apply an action to all files with that name

#### This operator will launch any executable file from the terminal
```sh
./
```
#### The "&" operator is used for multitasking on terminal (it don't start the program process as a child of the terminal, but independent from it, so you can close the terminal, similar of what "exec" command does, replacing the shell process by the called program)
```sh
program &
```
#### Replace the shell by the called program (similar to "&" or "exit")
```sh
exec program
```
#### Run a non-executable sh script
```sh
sh your-script-name
```
#### Run a non-executable Bash script
```sh
bash your-script-name
```
#### Kill all processes with the specified name
```sh
pkill process-name
```
#### Kill all instances of a running program
```sh
killall process-name
```
#### Kill all processes of an user
```sh
killall -u user-name
```
#### This operator store the output of a task on some file (example: `task > file.txt`)
```sh
>
```
#### This operator store the output of a task on some file but don't overwrite it's contents (example: `task > file.txt`)
```sh
>>
```
#### This operator apply a command above the output of other program (example: `glxinfo | grep OpenGL`, this command will search for "OpenGL" inside the output of "glxinfo") - this method is technically known as "Unix pipe"
```sh
|
```
#### Download any GitHub repository to the active directory
```sh
git clone https://github.com/name-of-the-user/name-of-the-repository.git
```
#### Download any remote Git repository
```sh
git clone https://website-name.com/name-of-the-repository.git
```
#### Download a Git repository to the specified directory
```sh
git clone https://website-name.com/name-of-the-repository.git /name/of/your/folder
```
#### Download any file (as the HTTP protocol headers are flexible, it can download the wrong file, so try to specify the exact file without header problems, generally an exposed extension of the file in the URL "https://website.com/nameofthefile.extension")
```sh
wget https://website-name.com/name-of-the-file
```
#### Resume an incomplete download
```sh
wget -c https://website-name.com/name-of-the-file
```
#### Download any file and try again from where it stopped if the connection failed (by default wget tries 20 times)
```sh
wget --tries=anynumber https://website-name.com/name-of-the-file
```
#### Download from multiple links of a file
```sh
wget -i file.txt
```
#### Download the entire website and convert it to work locally (offline)
```sh
wget --recursive --page-requisites --html-extension --convert-links --no-parent https://website-name.com
```
#### Download any file
```sh
curl -O https://website-name.com
```
#### Resume an incomplete download
```sh
wget -C - -O https://website-name.com/name-of-the-file
```
#### Download files from multiple websites at once
```sh
curl -O https://website-name.com -O https://website2-name.com
```
#### Example command for custom [Wine](https://www.winehq.org/) Prefixes
```sh
WINEPREFIX=~/.yourprefixname ./wine
```
#### Run Wine Explorer from the specified Wine Prefix
```sh
WINEPREFIX=~/.yourprefixname ./wine explorer
```
#### Option to extract [AppImage](https://appimage.org/) files
```sh
--appimage-extract
```
#### Download a torrent with [webtorrent-cli](https://github.com/webtorrent/webtorrent-cli) and open [VLC](https://www.videolan.org/vlc/) media player
```sh
webtorrent download "magnet:..." --vlc
```
#### Choose how many threads will be used for compilation
```sh
make -j1
```
#### Install a locally compiled program on the system
```sh
sudo make install
```
#### Show configuration files of all programs installed on the system
```sh
ls /etc
```
#### Show the user configuration files of programs
```sh
ls ~/.local
```
#### Show files stored by [XDG-compliant](https://www.freedesktop.org/wiki/Specifications/) programs (FreeDesktop standard)
```sh
ls ~/.config
```
#### Clean systemd journal logs older than x days ("--vacuum-time=1d" means older than 1 day)
```sh
sudo journalctl --vacuum-time=1d
```
#### Clean thumbnails cache
```sh
rm -rf ~/.cache/thumbnails/*
```

## Package Management

#### This common argument remove unused dependencies on some package managers
```sh
autoremove
```
#### This common argument remove packages cache
```sh
autoclean
```
#### This symbol applies an action to all packagess with that name
```sh
package_name*
```
#### Fix a incomplete package install on Debian systems
```sh
dpkg --configure -a
```
#### Remove all packages on FreeBSD systems
```sh
pkg delete -a
```

## Files/Folders

#### Show the current active directory
```sh
pwd
```
#### Change the active directory to the specified folder
```sh
cd /name/of/your/folder
```
#### Change to the previous directory with echo
```sh
cd -
```
#### Change to the parent directory/folder
```sh
cd ..
```
#### Change the active directory to your user folder
```sh
cd ~
```
#### Show normal folders/files of the directory
```sh
ls
```
#### Show all folders/files from a directory, including the hidden ones
```sh
ls -a
```
#### Show almost all files/folders, excluding the hidden . and .. Unix tree files
```sh
ls -A
```
#### Show the files/folders inside all the folders of the directory
```sh
ls *
```
#### Show all files/folders inside all the folders of the directory, inclusing hidden ones
```sh
ls -a *
```
#### Show advanced information about the files/folders of the directory
```sh
ls -l
```
#### Show the contents of any text file
```sh
cat /directory/file
```
#### Search for a text in the specified file format (recursively)
```sh
grep -nr "text" --include "*.format"
```
#### Search for a text in the specified file name (recursively)
```sh
grep -nr "text" --include "file-name.type"
```
#### Create a new folder on the active directory
```sh
mkdir name-of-the-folder
```
#### Copy a file to other folder and overwrite on destination
```sh
cp name-of-your-file /destination/folder
```
#### Copy a file to other folder, overwrite on destination and maintain the file permissions and timestamps
```sh
cp -p name-of-your-file /destination/folder
```
#### Show the files that are being copied (verbose mode)
```sh
cp -v name-of-your-file /destination/folder
```
#### Ask if you want to overwrite the file
```sh
cp -i name-of-your-file /destination/folder
```
#### Copy a file to other folder, maintain permissions/timestamps, show the file being copied, ask permission to overwrite and make a backup
```sh
cp -pvib name-of-your-file /destination/folder
```
#### Copy/overwrite/backup a file to other folder with backup
```sh
cp -b name-of-your-file /destination/folder
```
#### Copy multiple files to other folder and overwrite on destination
```sh
cp file1 file2 /destination/folder
```
#### Copy a folder to other folder and overwrite on destination
```sh
cp -r /name-of-your-folder /destination/folder
```
#### Copy only the things inside the folder and overwrite on destination
```sh
cp -r name-of-your-folder/. /destination/folder
```
#### Copy a folder to other folder, maintain permissions/timestamps, show the files being copied, ask permission to overwrite and make a backup
```sh
cp -rpvib name-of-your-folder /destination/folder
```
#### Copy multiple folders to other folder and overwrite on destination
```sh
cp -r folder1 folder2 /destination/folder
```
#### Move a file/folder to other folder and overwrite on destination
```sh
mv /name-of-your-folder /destination/folder
```
Or
```sh
mv name-of-your-file /destination/folder
```
#### Ask if you want to overwrite the folder
```sh
mv -i name-of-your-file /destination/folder
```
#### Move all files with the specified type to the destination folder
```sh
mv *.type /destination/folder
```
#### Move/rename a folder
```sh
mv /name-of-your-folder /new-folder-name
```
#### Remove/delete a file
```sh
rm name-of-the-file
```
#### Remove/delete any folder recursively without asking for permission (use with caution if you called the command with su/sudo/doas)
```sh
rm -rf /your/folder
```
#### Remove an empty directory
```sh
rmdir /your/folder
```
#### Example command to add text on any file
```sh
echo "text" >> /directory/file
```
#### `.nameofthefile or .nameofthefolder` | A dot before the name of a file/folder make it hidden

#### Search for files on the directory/subdirectories (run with "sudo" or "su" if these directories are under root permissions)
```sh
find . -type f -name file-name
```
#### Search for folders on the directory/subdirectories (run with "sudo" or "su" if the directories are under root permissions)
```sh
find . -type d -name folder-name
```
#### Show all folders/files/subfolders/subfiles in a tree
```sh
tree /name-of-the-folder
```
