# main

Create touchpad.sh file and write these and put it on /usr/bin

#!/bin/bash

rmmod i2c_hid
modprobe i2c_hid

Than do chmod +x touchpad.sh on terminal

Now, we need to create service file for execute bash file when boot the pc.

Create file to /etc/systemd/system named touchpad.service and write these:
[Unit]
Description=Enable touchpad
Before=graphical.target

[Service]
Type=oneshot
ExecStart=/usr/bin/enable_touchpad
User=root

[Install]
WantedBy=multi-user.target

Now we need to enable and start the service so enter these commands to terminal:
sudo systemctl daemon-reload
sudo systemctl enable touchpad.service
sudo systemctl start touchpad.service

than reboot your pc, you can check logs with this command if you want to see service executed properly:
sudo systemctl status touchpad.service

good luck! 
