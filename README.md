** End of life  2015**

If you find update script useful, please consider to make a donation to support this freeware.

Please keep in mind that donations are welcome, but in no way required to use and distribute update.script.

[Donate link – PayPal](https://www.paypal.me/WaelIsa)


update.script Version: 1.8.4

update script tested in this OS 32bit and 64bit.

*RedHat Linux

*RedHat Fedora

*RedHat Enterprise

*CentOS

## and update to

*OpenSSL (You need to build ssh, apache, php, etc after upgrade)

*OpenSSH (First update OpenSSL then install Webmin control panel to fix openssh if down or error in update.)

*ClamAV

*MRTG

*SpamAssassin

*ImageMagick

*GraphicsMagick

*Webmin control panel (You need to open one port 10000 in your firewall)

## Just download/chmod

mkdir /usr/local/updatescript

cd /usr/local/updatescript

wget --no-check-certificate https://github.com/waelisa/update-script-for-DirectAdmin/raw/master/update.script

chmod 755 update.script

Run this to read how to use.

./update.script

Run this to update update.script

./update.script UPDATEME

Run this to see release date and version

./update.script DATE

Run this to clean update script folder

./update.script CLEAN


## Note:-

1- Run this to clean or update update script before you use

2- Select best mirror for your server mirror.conf , if you want new mirror.conf file just delete old one in update script folder.


## ClamAV

nano -w /etc/exim.conf

before

primary_hostname =

add

av_scanner = clamd:127.0.0.1 3310

after

check_message:

add

deny message = This message contains malformed MIME ($demime_reason)

demime = *

condition = ${if >{$demime_errorlevel}{2}{1}{0}}

deny message = This message contains a virus or other harmful content ($malware_name)

demime = *

malware = *

deny message = This message contains an attachment of a type which we do not accept (.$found_extension)

demime = bat:com:pif:prf:scr:vbs

warn message = X-Antivirus-Scanner: Clean mail though you should still use an Antivirus

save then restart exim

/sbin/service exim restart


## ImageMagick

Install ImageMagick then run add this to your php configure file

--with-imagick=/usr/local \

after

--with-freetype-dir=/usr/local/lib \

save then run

./build php n

## GraphicsMagick

Install GraphicsMagick then run add this to your php configure file

--with-gmagick=/usr/local \

after

--with-freetype-dir=/usr/local/lib \

save then run

./build php n


Best Regards,
Wael Isa
