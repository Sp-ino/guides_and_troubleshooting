# Installing official NVIDIA drivers on Arch Linux

- Search for the section "download drivers" on the NVIDIA website. Look for your GPU by specifying Linux as operating system. Download the latest version of the driver, which should be a .run file.

- Grant execution permissions to the .run file with `$ chmod 770 <filename>`, then run the executable with sudo ./<filename>

- In some cases the installer may complain that the kernel module `nvidia-drm` is in use, causing the installation to fail. If that is the case, stop all graphic sessions, then run `systemctl isolate multi-user.target` and `sudo modprobe -r nvidia-drm`. The module should be unloaded.
