# Setup and usage of tigervnc on arch - notes

- After installing vncserver, make sure to have followed the configuration instructions from the arch wiki (create the config file and the vnc password) NOTE: each user must be associated to a port in the file /etc/tigervnc/vncserver.users, see the arch wiki for that as well.

- It may be necessary to stop gdm before starting the vncserver: ssh to the remote machine and run 
	$ systemctl stop gdm

- Launch a vnc session on the display associated with your account. For example,
	$ sudo vncsession _username_ :2 
  if your user is associated to display 2 in the file /etc/tigervnc/vncserver.users)

- Start the vnc server with 
	$ systemctl start vncserver@:_display_number_ 
  For example, if you have opened a session on display 2 run
	$ systemctl start vncserver@:2

- Now the session should be up and running. Connect with vncviewer from your local machine. For example, if using ssh tunnel, run
	$ ssh -L 9901:127.0.0.1:5902 _username_@_remote_machine_ip_
  where 9901 is the port on your local machine and 5902 corresponds to 590_remote_display_. Then, without closing the terminal
  on which ssh has been launched, run
	$ vncviewer localhost:9901
  on a new terminal. After typing the password, you should gain access to the remote desktop.
