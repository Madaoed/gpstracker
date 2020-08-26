# gpstracker
Raspberry Pi GPS Tracker

To use different display drivers use ex:
info.py --display sh1106

Installation Steps
sudo raspi-config
->enable serial, i2c, ssh, gpio
disable bluetooth

Edit /etc/fstab
Add to automount usb drive->
/dev/sda1       /mnt                  auto    defaults,auto,users,rw,nofail,umask=000 0 3

sudo apt install python-serial gpsd gpsd-clients chrony exfat-utils exfat-fuse
Copy oled.service, gpsd.service, to /etc/systemd/system
Copy gpsd.service to /etc/systemd/system
Edit /etc/default/gpsd
 -> USBAUTO="false"
 -> DEVICE="/dev/ttyS0"
 -> GPSD_OPTIONS="-n -b"
#sudo chmod 666 /dev/ttyS0 
sudo systemctl daemon-reload
sudo systemctl enable oled
sudo systemctl enable gpsd
sudo reboot

sudo apt install python3-dev python3-pip libfreetype6-dev libjpeg-dev build-essential libopenjp2-7 libtiff5
sudo pip3 install --upgrade luma.oled
sudo pip3 install psutil i2c-tools
