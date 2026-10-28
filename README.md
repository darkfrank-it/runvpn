# runvpn
Automate start|stop|restart operation for openconnect vpn.

## Installation
Root or sudo permission is needed to install this package.

~~~bash
sudo dpkg -i runvpn_<version>-<revision>_all.deb
~~~

## Configuration
Set the VPN server and your username in `/etc/runvpn.conf`:

~~~bash
sudo nano /etc/runvpn.conf
~~~

~~~
VPN_SERVER=vpn.example.com
VPN_USER=<username>
~~~

The password is read from the clipboard when the VPN is started, and the
clipboard is cleared afterwards. On Wayland `wl-paste` is used when
`wl-clipboard` is installed, otherwise `xclip`.

To not enter the sudo password every time the application is launched, add
your user to the `runvpn` group (the package installs the sudo rule in
`/etc/sudoers.d/runvpn`):

~~~bash
sudo adduser <user> runvpn
~~~

then log out and log in again to apply the new group.


## Manual run:
~~~bash
sudo runvpn start|stop|restart
~~~

## Build
~~~bash
./make-package <version> <revision>
~~~

## Uninstall
~~~bash
sudo apt-get remove --purge runvpn
~~~


## CHANGELOG
See [changelog](changelog).

## Release
Pushing a tag in the form `v<version>-<revision>` (e.g. `v0.1.0-1`) builds the
.deb package and publishes it as a GitHub release. The tag must match the
latest version in `changelog`.
