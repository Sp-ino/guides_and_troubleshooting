# installing_vivado_on_arch
A guide to the installation of Vivado on Arch Linux.

### Downloading and running the installer
From AMD-Xilinx webpage download the All-OS Unified Installer tarball for the version you wish to install. Extract the archive and run the xsetup.sh script with the command  
```$ sudo bash xsetup.sh```    

### Troubleshooting
In linux the installation often gets stuck during the final processing phase; more specifically at "Generating installed device list". This issue can be solved by running manually the problematic step and then by killing the process that is preventing installation from completing.

First run the following commands to install required packages from the AUR:   
```$ sudo pacman -S ncurses5-compat-libs```   
```$ sudo pacman -S core/libxcrypt-compat```    
then run the command   
```$ /tools/Xilinx/Vivado/2022.1/bin/vivado -nolog -nojournal -mode batch -source /tools/Xilinx/Vivado/2022.1/scripts/sysgen/tcl/xlpartinfo.tcl -tclargs /tools/Xilinx/Vivado/2022.1/data/parts/installed_devices.txt```   

Finally, run   
```$ ps aux | grep -i xilinx | grep nolog```   
and kill the processes that are found. This will allow the installation process to finish.

### Shortcuts
If no shortcuts are created, you can launch vivado by using the bash script in this repo. In order to be able to launch vivado without specifying the script's full path, you can install the script in the folder /usr/local/bin with the command   
```$ sudo install vivado /usr/local/bin```

