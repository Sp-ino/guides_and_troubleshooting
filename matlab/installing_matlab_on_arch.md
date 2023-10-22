# Installing MATLAB on Arch Linux
## Intro
Detailed tips and indications for installing MATLAB on Arch Linux are already present on the official Arch Wiki (see https://wiki.archlinux.org/title/MATLAB). This is just a summary of the most relevant steps. In particular, this file describes how the installation procedure without the `matlab` package from the AUR.

## Procedure
To install MATLAB on Arch without the `matlab` package, follow the steps below:
- Download the MATLAB installer zipfile from the official MathWorks website and extract it.
- Run the `install` script from the extracted folder. Run it as superuser for a system-wide installation, or withouth privileges to install it only for you. **NOTE** The installer may hang when launched with superuser privileges.
 privileges.
- If the `install` script crashes with the error `Failed to launch web window with error: Unable to launch the MATLABWindow application`, you can adopt the workaround described at https://wiki.archlinux.org/title/MATLAB#Unable_to_launch_the_MATLABWindow_application. Basically the workaround involves removing MATLAB's libfreetype.so* by running `$ rm ./bin/glnxa64/libfreetype.so*` (you may also move them in another folder).
-  
