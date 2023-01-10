## Operating System/Kernel

#### `uname -r ; uname -a` | Show OS/kernel information.
#### `dmesg` | Show OS/kernel log.
#### `df -h` | Show information about your partitions/filesystems.
#### `free -m` | Show memory information.

## Hardware

#### `lscpu` | Show CPU information.
#### `cat /proc/meminfo` | Advanced memory information.

## Graphics

#### `startx` | Start X.Org from terminal (the command on .xinitrc will run).
#### `glxinfo | grep OpenGL` | Show your OpenGL driver name/version.
#### `vulkaninfo | grep Vulkan` | Show your Vulkan driver name/version.

## User

#### `su -` | Become root with echo.
#### `whoami` | Current active user on terminal shell/$PATH.
#### `$HOME` | Environment variable for user folder.
#### `echo $SHELL` | Show your default terminal shell.
#### `echo $0` | Show your current terminal shell.
#### `cat /etc/shells` | Show your installed terminal shells (active on $PATH).
#### `chsh -s /path/of/your/shell` | Change your default terminal shell permanently (common path is /usr/bin).
#### `alias name='command'` | Add an alias/abbreviation for a command on your terminal shell (add this command on your shell configuration file to be permanent, generally a file named `.nameofyourshellrc` on your user folder).
#### `Ctrl+C` | This keyboard shortcut cancel any command process.
#### `clear` | Clean your terminal content/output.

## Programs

#### `echo $PATH` | Show the directories in $PATH environment variable.
#### `export PATH=$PATH:your_directory` | Add a new PATH to your terminal shell.
#### `WINEPREFIX=~/.newprefix ./wine` | Example command for custom Wine Prefixes.
#### `--appimage-extract` | Option to extract AppImage files.
#### `name*` | On some programs the * symbol apply an action to all files with that name.
#### `./` | This operator will launch any program from terminal.

## Files/Folders

#### `cd -` | Change active directory with echo.
#### `cd $HOME` | Change the active directory to your user folder.
#### `echo "text" >> /directory/file` | Example command to add text on any file.
#### `cat /directory/file` | Show the contents of any text file.
#### `mkdir nameofthefolder` | Create a new folder on the active directory.
#### `rm -rf /name/of/the/folder or nameofthefile` | Remove/delete any folder/file (use with caution if you called the command with su/sudo/doas).
#### `.nameofthefile or .nameofthefolder` | A dot before the name of a file/folder make it hidden.
#### `ls -a` | Show all folders/files from a directory, including the hidden ones.
#### `ls -A` | Show almost all files/folders, excluding the hidden . and .. Unix tree files.
#### `ls *` | Show the files/folders inside all the folders of the directory.
#### `ls -a *` | Show all files/folders inside all the folders of the directory, inclusing hidden ones.
#### `ls -l` | Show advanced information about the files/folders of the directory.
