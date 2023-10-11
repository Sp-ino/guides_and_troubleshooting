# docker post-installation tasks

## Checks
Check that everything works by running ```$ docker info```. If it fails run sudo docker info. If this does not raise errors 
then it is sufficient to run post-installation tasks to enable docker usage without using sudo.

## Post-installation tasks to use docker without sudo
```$ sudo chown root:docker /var/run/docker.sock
$ sudo usermod -Ag docker $USER
$ sudo chown root:docker /home/$USER/.docker/*
$ sudo chmod 660 .docker/*```

Then, logout and login again into docker restart user session on pc


## Useful notes
In order to use nvidia drivers in docker containers on Arch, install nvidia-container-toolkit by using the PKGBUILD in this folder (credit to Alice Knag @AskAlice). To install run ```makepkg -Acs``` and then ```sudo pacman -U *.tar.zst```

