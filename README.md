# transmission-cli for download_torrent using command line

## __TRANSMISSION CLI USER GUIDE__

When it comes to BitTorrent clients, there are a lot to choose from. After using uTorrent for a while I found myself looking for a lightweight (and ad-free) alternative. In some cases, you will find that a heavy desktop app can be replaced by a simple command line alternative and Transmission CLI offers just that.
Transmission is a popular cross-platform BitTorrent client that comes in a variety of flavours, including native Mac and GTK+ versions with a desktop GUI familiar to anyone who has used uTorrent.
There is also a command line interface for Transmission which turned out to be perfect for my occasional BitTorrent requirements.
This guide will run you through the basic usage of the terminal client.

### __INSTALLATION__
Transmission is the default BitTorrent client in many Linux distributions and __transmission-cli__ can be found in most official repositories. For OSX, Transmission CLI can be installed with the excellent package manager [Homebrew](https://brew.sh):
```
>_ brew install transmission
```
The installation will include a set of command line utilities but for the scope of this tutorial we will cover just two of these: __transmission-daemon__ and __transmission-remote__.

- transmission-daemon
This is the Transmission client itself, when a Transmission session is started it will run quietly as a background process and can be controlled with the remote utility.

- transmission-remote
This is the control utility used for adding and removing torrents.

### __CONFIGURATION__
Out of the box, the default settings should be fine for simple use. Although one thing you may want to update is the download directory for completed torrents. This can be set with the following command:
```
>_ transmission-daemon --download-dir "your-download-directory-path"
```
To confirm the directory location you can run this command which will print out the current settings:
```
>_ transmission-daemon --dump-settings
```
For a full list of available configuration options, check out the manual page.
```
>_ man transmission-daemon
```
### __START__
The first thing you will want to do is start the Transmission session, you can do this by simply running the daemon:
```
>_ transmission-daemon
```
### __ADDING A TORRENT__
To add a torrent you will use __transmission-remote__ and pass the torrent file location as a parameter with the __-a__ option. The file location can either be a local path to a downloaded torrent file or a direct URL to the online location.
```
>_ transmission-remote -a "http://releases.ubuntu.com/16.10/ubuntu-16.10-desktop-amd64.iso.torrent"
```
Magnet links are also supported and can be added in exactly the same way.
```
>_ transmission-remote -a "magnet:?xt=urn:btih:9f9165d9a281a9b8e782cd5176bbcc8256fd1871&dn=Ubuntu+16.04.1+LTS+Desktop+64-bit&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969&tr=udp%3A%2F%2Fzer0day.ch%3A1337&tr=udp%3A%2F%2Fopen.demonii.com%3A1337&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969&tr=udp%3A%2F%2Fexodus.desync.com%3A6969"
```
### __DOWNLOAD STATUS__
The status of your downloads can be checked at any time by using the list __-l__ command:
```
>_ transmission-remote -l
```
This will display a list of loaded torrents and the status of each download.

![img](https://cli-ck.io/images/2016-12-05_cli-ck_-_transmission_cli_user_guide_-_download_list.jpg)

### __REMOVING A TORRENT__
It is always good to seed a torrent for as long as possible, but when your housemate is knocking on your door and complaining about the bandwidth, here is how to remove the torrent.

In the download list output you can see that each loaded torrent has an ID in the left-hand column. You can use this ID to select a torrent by using the -t command followed by -r to remove.
```
>_ transmission-remote -t 3 -r
```
You can select multiple torrents by passing comma separated ID’s.
```
>_ transmission-remote -t 3,4 -r
```
Alternatively you can also pass __all__ to remove everything.
```
>_ transmission-remote -t all -r
```

__[Ressource](https://cli-ck.io/transmission-cli-user-guide/)__
