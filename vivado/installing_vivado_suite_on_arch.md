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
If no shortcuts are created, you can launch vivado by using the bash script `vivado` contained in this folder. In order to be able to launch vivado without specifying the script's full path, you can install the script in the folder /usr/local/bin with the command   
```$ sudo install vivado /usr/local/bin```
You may use the same approach to create a link for the model composer by using the `model_composer` script.

### Model Composer issues
When using Xilinx Model Composer, simulations with Xilinx blocks may fail with an error log similar to the following:
```
    /opt/xilinx/Vivado/2021.1/tps/lnx64/binutils-2.26/bin/ld: /lib64/libm.so.6: don't know how to handle section `.relr.dyn' [0x     13]
    /opt/xilinx/Vivado/2021.1/tps/lnx64/binutils-2.26/bin/ld: skipping incompatible /lib64/libm.so.6 when searching for /lib64/libm.so.6
    /opt/xilinx/Vivado/2021.1/tps/lnx64/binutils-2.26/bin/ld: cannot find /lib64/libm.so.6
    /opt/xilinx/Vivado/2021.1/tps/lnx64/binutils-2.26/bin/ld: /lib64/libmvec.so.1: don't know how to handle section `.relr.dyn' [0x      13]
    /opt/xilinx/Vivado/2021.1/tps/lnx64/binutils-2.26/bin/ld: skipping incompatible /lib64/libmvec.so.1 when searching for /lib64/libmvec.so.1
    /opt/xilinx/Vivado/2021.1/tps/lnx64/binutils-2.26/bin/ld: cannot find /lib64/libmvec.so.1
    clang++: error: linker command failed with exit code 1 (use -v to see invocation)
```
In this case, remove the linker (the file `/opt/xilinx/Vivado/2021.1/tps/lnx64/binutils-2.26/bin/ld`), for example by backing it up in another folder, to force the Model Composer to use the system linker.

