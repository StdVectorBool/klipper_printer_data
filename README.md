Source controlled configs for 3 Aquilas running on one Raspberry Pi 4.  The Yellow instance hosts Crowsnest.

After using Kiauh to setup 3 Klipper instances, change relevant subdirectories to symlinks to this repo.
```
# Setup three instances: red, blue, yellow
cd ~/kiauh
./kiauh.sh

# Use configs from git
cd ~/red_data
rm -rf config systemd
ln -s ~/klipper_printer_data/red_data/config config
ln -s ~/klipper_printer_data/red_data/systemd systemd

# Repeat for blue and yellow
# Use kiauh to restart klipper, moonraker, mainsail, crowsnest, etc
```

NOTES:
* The entire `*_data` directories aren't committed because of device symlinks.
* Mainsail running on `pi.local:81` because there's another web server on 80.  All relative URLs like Crowsnest need this explicit host:port.

TODO:
* Backup Mainsail DB?