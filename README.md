# Raspberry Pi Rasbian Jessie NTP Backport

This includes two major packages (and the associated tools that are part
of the Debian source package) compiled from the Raspbian testing
repository on a Raspbian Jessie system.

The newer version of gpsd with the testing repo includes support for
Linux kernel PPS drivers.

The newer version of NTP has support for Linux PPS (the most accurate
way to get time into NTP).  It also includes a patch
(ntpd-gpsd-any-device.patch) that extends the gpsdjson NTP reference
clock driver to allow unit 255 to listen to all devices available to
gpsd. This is important because gpsd needs the PPS device to be named
/dev/pps[0-9]+ while gpsd needs it named /dev/gps[0-9]+ to recognize
it.  This patch bypasses this and allows an unmodified gpsd to be used
as a reference clock with both a PPS and GPS device.  This minimizes
the chance of bad time being reported on initial startup of ntpd.

To use this repo:

    wget -O /etc/apt/sources.list.d/rpi-ntpd.list http://jmaslak.github.io/rpi-ntpd/raspbian/rpi-ntpd.list

    wget -O - http://jmaslak.github.io/rpi-ntpd/raspbian/conf/jmaslak.gpg.key | apt-key add -

Then:

    apt-get update

    apt-get install ntp gpsd`


