# Installing MATLAB on Arch Linux
## Intro
Detailed tips and indications for installing MATLAB on Arch Linux are already present on the official Arch Wiki (see https://wiki.archlinux.org/title/MATLAB). This is just a summary of the most relevant steps. In particular, this file describes how the installation procedure without the `matlab` package from the AUR.

## Procedure
To install MATLAB on Arch without the `matlab` package, follow the steps below:
- Download the MATLAB installer zipfile from the official MathWorks website and extract it.
- Run the `install` script from the extracted folder. Run it as superuser for a system-wide installation, or withouth privileges to install it only for you. **NOTE** The installer may hang when launched with superuser privileges. **NOTE-2** The installer GUI needs Xorg to run (Wayland is not officially supported yet).
 privileges.
- If the `install` script crashes with the error `Failed to launch web window with error: Unable to launch the MATLABWindow application`, you can adopt the workaround described at https://wiki.archlinux.org/title/MATLAB#Unable_to_launch_the_MATLABWindow_application. Basically the workaround involves removing MATLAB's libfreetype.so* by running `$ rm ./bin/glnxa64/libfreetype.so*` (you may also move them to another folder).
- Once the installer is working, follow the steps on the GUI until installation is complete.
- If the matlab executable path is not added to PATH, you may add it manually by running `$ export PATH=$PATH:path_to_matlab_executable`, where `path_to_matlab_executable` is the path where the executable has been installed. To run the export command every time a bash terminal is started, add the command to yout .bashrc file.
- Attempts to launch Simulink may fail with the error `/usr/lib/libcairo.so.2: undefined symbol: FT_Get_Color_Glyph_Layer:`. If that is the case, put aside MATLAB's libfreetype.so* and libstdc++.so* files. You may achieve this by removing them or by placing them into a separate folder with the commands   
```
$ cd matlab_installation_path
$ mkdir exclude
$ mv bin/glnxa64/libfreetype.so* exclude/
$ mv sys/os/glnxa64/libstdc++.so* exclude/
```
where `matlab_installation_path` is where the matlab executable has been installed.
