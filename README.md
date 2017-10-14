[b] If you find update script useful, please consider to make a donation to support this freeware.

Please keep in mind that donations are welcome, but in no way required to use and distribute update.script.[/b]

[url=https://www.paypal.me/WaelIsa][color=red][b]You can support update.script by PayPal[/b][/color][/url]


[b][color=blue]update.script Version: 1.8.4[/color][/b]

update script tested in this OS 32bit and 64bit.

[list]

[*] RedHat Linux
[*] RedHat Fedora
[*] RedHat Enterprise
[*] CentOS

and update to

[list]
[*] OpenSSL [color=red](You need to build ssh, apache, php, etc after upgrade)[/color]
[*] OpenSSH [color=red](First update OpenSSL then install Webmin control panel to fix openssh if down or error in update.)[/color]
[*] ClamAV
[*] MRTG
[*] SpamAssassin
[*] ImageMagick
[*] GraphicsMagick
[*] Webmin control panel [color=red](You need to open one port 10000 in your firewall)[/color]
[/list][/list]

Just download/chmod
[code]
mkdir /usr/local/updatescript
cd /usr/local/updatescript
wget --no-check-certificate https://github.com/waelisa/update-script-for-DirectAdmin/raw/master/update.script
chmod 755 update.script
[/code]
[color=darkblue]Run this to read how to use.[/color]
[code]
./update.script
[/code]
Run this to update update.script
[code]
./update.script UPDATEME
[/code]
Run this to see release date and version
[code]
./update.script DATE
[/code]
Run this to clean update script folder
[code]
./update.script CLEAN
[/code]

Note:-
1- Run this to clean or update update script before you use
2- Select best mirror for your server mirror.conf , if you want new mirror.conf file just delete old one in update script folder.


*****
*****
*****

[b][color=green]ClamAV[/color][/b]
[code]
nano -w /etc/exim.conf
[/code]
before
[code]primary_hostname =[/code]
add
[code]av_scanner = clamd:127.0.0.1 3310[/code]
after
[code]check_message:[/code]
add
[code]deny message = This message contains malformed MIME ($demime_reason)
demime = *
condition = ${if >{$demime_errorlevel}{2}{1}{0}}
deny message = This message contains a virus or other harmful content ($malware_name)
demime = *
malware = *
deny message = This message contains an attachment of a type which we do not accept (.$found_extension)
demime = bat:com:pif:prf:scr:vbs
warn message = X-Antivirus-Scanner: Clean mail though you should still use an Antivirus[/code]
save then restart exim
[code]/sbin/service exim restart[/code]


*****
*****
*****

[b][color=green]ImageMagick[/color][/b]
Install ImageMagick then run add this to your php configure file
[code]--with-imagick=/usr/local \[/code]
after
[code]--with-freetype-dir=/usr/local/lib \[/code]
save then run
[code]./build php n[/code]

*****
*****
*****

[b][color=green]GraphicsMagick[/color][/b]
Install GraphicsMagick then run add this to your php configure file
[code]--with-gmagick=/usr/local \[/code]
after
[code]--with-freetype-dir=/usr/local/lib \[/code]
save then run
[code]./build php n[/code]

*****
*****
*****


[B]Thanks for [COLOR="Red"]smtalk[/COLOR], [COLOR="Red"]SeLLeRoNe[/COLOR] and [COLOR="Red"]ReN[/COLOR][/B]

*****
*****
*****

[b][i]Best Regards,
Wael Isa[/i][/b]
