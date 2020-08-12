# gpstracker
Raspberry Pi GPS Tracker

To use different display drivers use ex:
info.py --display sh1106

Installation Steps
1. Edit /etc/fstab
Add to automount usb drive->
/dev/sda1       /mnt                  auto    defaults,auto,users,rw,nofail,umask=000 0 3

2. sudo apt install python-serial gpsd gpsd-clients chrony
3. Copy oled.service to /etc/systemd/system
4. Copy gpsd.service to /etc/systemd/system
5. Edit /etc/default/gpsd
 -> USBAUTO="false"
 -> DEVICE="/dev/ttyS0"
 -> GPSD_OPTIONS="-n -b"
6. sudo chmod 666 /dev/ttyS0 
7. sudo systemctl daemon-reload
8. sudo systemctl enable oled
7. sudo systemctl enable gpsd
8. sudo reboot
sudo -H pip install psutil
Python 2
sudo apt install python-dev python-pip libfreetype6-dev libjpeg-dev build-essential libopenjp2-7 libtiff5
sudo -H pip install --upgrade luma.oled

For python3 -Not working currently
sudo apt install python3-dev python3-pip libfreetype6-dev libjpeg-dev build-essential libopenjp2-7 libtiff5
sudo -H pip3 install --upgrade luma.oled
