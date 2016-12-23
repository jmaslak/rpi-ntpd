# Raspberry Pi Rasbian Jessie NTP Backport

To use this repo:

    wget -O /etc/apt/sources.list.d/rpi-ntpd.list http://jmaslak.github.io/rpi-ntpd/raspbian/rpi-ntpd.list

    wget -O - http://jmaslak.github.io/rpi-ntpd/raspbian/conf/jmaslak.gpg.key | apt-key add -

Then:

    apt-get update

    apt-get install ntpd

