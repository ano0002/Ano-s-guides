# The guide to create your own media server with Plex, Sonarr, Radarr, Prowlarr, qBitTorrent and Overseer
> Music Support soon
> (Lidarr, Deemix, PlexAmp, ...)
> See https://github.com/ano0002/overseerr/tree/overseer-with-lidarr-support

Most of the information in this guide comes from the official documentation of the software and the Trash Guides. Here are the links:
- https://wiki.servarr.com/
- https://support.plex.tv/
- https://trash-guides.info/

## Before you start
- [ ] Have a computer available which will be running 24/7
- [ ] Have a VPN (recommended)

## Index

- [The guide to create your own media server with Plex, Sonarr, Radarr, Prowlarr, qBitTorrent and Overseer](#the-guide-to-create-your-own-media-server-with-plex-sonarr-radarr-prowlarr-qbittorrent-and-overseer)
  - [Before you start](#before-you-start)
  - [Index](#index)
  - [Windows Installation](#windows-installation)
    - [WSL 2 (Windows Subsystem for Linux) and Ubuntu](#wsl-2-windows-subsystem-for-linux-and-ubuntu)
      - [Windows 10 vers 2004 or higher (Build 19041 and higher) or Windows 11](#windows-10-vers-2004-or-higher-build-19041-and-higher-or-windows-11)
      - [Any other Windows version](#any-other-windows-version)
    - [Docker](#docker)
    - [Plex](#plex)
    - [Radarr](#radarr)
    - [Sonarr](#sonarr)
    - [Prowlarr](#prowlarr)
    - [qBitTorrent](#qbittorrent)
    - [Overseer](#overseer)
  - [Ubuntu Installation](#ubuntu-installation)
    - [Plex](#plex-1)
    - [Sonarr](#sonarr-1)
    - [Radarr and Prowlarr](#radarr-and-prowlarr)
      - [Easy way (as described here)](#easy-way-as-described-here)
      - [Hands-on way](#hands-on-way)
    - [qBitTorrent](#qbittorrent-1)
    - [Overseer](#overseer-1)
  - [Configuration](#configuration)
    - [User and Group permissions](#user-and-group-permissions)
    - [Media folders](#media-folders)
    - [qBitTorrent](#qbittorrent-2)
    - [Radarr](#radarr-1)
    - [Sonarr](#sonarr-2)
    - [Prowlarr](#prowlarr-1)
    - [Plex](#plex-2)
    - [Overseer](#overseer-2)
  - [Credits and software used](#credits-and-software-used)

## Windows Installation

![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

> :warning: **This section only deals with the installation of the software on Windows not the configuration.
> For that see [Section 3](#configuration)**  

This is all the software you need to install on your Windows machine to create your own media server :
- WSL 2 (Windows Subsystem for Linux) and Ubuntu
- Docker
- Plex
- Radarr
- Sonarr
- Prowlarr
- qBitTorrent
- Overseer
I also recommend you to install a VPN of your choice on your machine to protect your privacy.

### WSL 2 (Windows Subsystem for Linux) and Ubuntu 

#### [Windows 10 vers 2004 or higher (Build 19041 and higher) or Windows 11](https://learn.microsoft.com/en-us/windows/wsl/install)
Run this command: 
```powershell
wsl --install
```
Then, restart your PC

#### [Any other Windows version](https://learn.microsoft.com/en-us/windows/wsl/install-manual)
1. Run PowerShell as administrator
2. Paste this command:
```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
3. Restart your PC
4. Run PowerShell as administrator again
5. Paste these two commands:
```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
6. Restart your PC Again
7. Download the Linux Kernel Update Package from
https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
8. Then, run powershell as administrator again and paste this command:
```powershell
wsl --set-default-version 2
```
9. Download and install Ubuntu from the Microsoft Store

### Docker

Download and install Docker Desktop from [here](https://docs.docker.com/desktop/install/windows-install/)

### Plex

Download and install Plex Media Server from [here](https://www.plex.tv/media-server-downloads/?cat=computer&plat=windows)

### Radarr

Download and run the Radarr installer from [here](https://radarr.video/#download)

### Sonarr

Download and run the Sonarr installer from [here](https://sonarr.tv/#download)

### Prowlarr

Download and run the Prowlarr installer from [here](https://prowlarr.com/#download)

### qBitTorrent

Download and install qBitTorrent from [here](https://www.qbittorrent.org/download)

### Overseer

1. Start by launching Docker Desktop 
2. Start cmd
3. Then run these commands in the terminal
```bash
docker volume create overseerr-data
docker run -d --name overseerr -e LOG_LEVEL=debug -p 5055:5055 -v "overseerr-data:/app/config" --restart unless-stopped sctx/overseerr:latest
```

**You're done with the installation! Now, you can move on to the [configuration](#configuration) of the software.**

## Ubuntu Installation

![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)

> :warning: **This section only deals with the installation of the software on Ubuntu not the configuration.
> For that see [Section 3](#configuration)**

This is all the software you need to install on your Ubuntu machine to create your own media server :
- Plex
- Radarr
- Sonarr
- Prowlarr
- qBitTorrent
- Overseer
I also recommend you to install a VPN of your choice on your machine to protect your privacy.

### Plex

Download the Plex Media Server .deb package from [here](https://www.plex.tv/media-server-downloads/?cat=server)

Then, run these commands in the terminal:
```bash
sudo dpkg -i <Your file name.deb>
```

If you don't have access to a GUI, you can run these commands in the terminal (you'll need to have `curl` installed):
```bash
curl <Your download link> -o plexmediaserver.deb
sudo dpkg -i plexmediaserver.deb
```
To get the download link, go there : [Linux distributions of plex media server](https://www.plex.tv/media-server-downloads/?cat=computer&plat=linux)

### Sonarr

To install Sonarr, simply run this command in the terminal:
```bash
curl -o- https://raw.githubusercontent.com/Sonarr/Sonarr/develop/distribution/debian/install.sh | sudo bash
```
Or with wget:
```bash
wget -qO- https://raw.githubusercontent.com/Sonarr/Sonarr/develop/distribution/debian/install.sh | sudo bash
```
Leave everything as default and complete the installation

If neither of these commands work, you can follow the instructions on the official download page of Sonarr [here](https://sonarr.tv/#downloads-linux-ubuntu)

### Radarr and Prowlarr

#### Easy way (as described [here](https://wiki.servarr.com/install-script))

Run these commands in the terminal:
```bash
curl -o servarr-install-script.sh https://raw.githubusercontent.com/Servarr/Wiki/master/servarr/servarr-install-script.sh
sudo bash servarr-install-script.sh
```
Once you see 
```
Select the application to install: 
1) lidarr
2) prowlarr
3) radarr
4) readarr
5) whisparr
6) quit
#?
```
Select prowlarr by typing `2` and then press enter
Leave everything as default and complete the installation
Once you see the message `Install complete` you can move on to the next application by restarting the script with `sudo bash servarr-install-script.sh` and selecting the next application.
This time select radarr.

#### Hands-on way

Follow the instructions on the official documentation of the softwares:
https://wiki.servarr.com/radarr/installation/linux
https://wiki.servarr.com/prowlarr/installation/linux

### qBitTorrent

To install qBitTorrent Web-UI, simply run this command in the terminal:
```bash
sudo apt install qbittorrent-nox
```

You'll also need a user to run qBitTorrent, so run these commands in the terminal:
```bash
sudo adduser qbittorrent-nox
sudo adduser qbittorrent-nox media
```

You also want to be part of the media group, now is a good time to add yourself, so run this command in the terminal:
```bash
sudo adduser <Your username> media
```

Then, you need to create a service file for qBitTorrent, so run these commands in the terminal:
```bash
sudo nano /etc/systemd/system/qbittorrent-nox.service
```

Then, paste this in the file:
```ini
[Unit]
Description=qBittorrent Command Line Client
After=network.target

[Service]
Type=forking
User=qbittorrent-nox
Group=media
UMask=007
ExecStart=/usr/bin/qbittorrent-nox -d --webui-port=8080
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

To save and exit, press `Ctrl` + `X`, then `Y`, then `Enter`

Then, you're going to enable and start the service, so run these commands in the terminal:
```bash
# Reload the systemd daemon to be aware of the new service file
sudo systemctl daemon-reload
# Enable the service
sudo systemctl enable qbittorrent-nox
# Start the service
sudo systemctl start qbittorrent-nox
```

Finally, you can check the status of the service by running this command in the terminal:
```bash
sudo systemctl status qbittorrent-nox
```
You should see something like this if everything went well :
```bash
● qbittorrent-nox.service - qBittorrent Command Line Client
     Loaded: loaded (/etc/systemd/system/qbittorrent-nox.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2024-03-02 00:30:35 UTC; 27min ago
   Main PID: 9301 (qbittorrent-nox)
      Tasks: 12 (limit: 1070)
     Memory: 46.6M
        CPU: 7.230s
     CGroup: /system.slice/qbittorrent-nox.service
             └─9301 /usr/bin/qbittorrent-nox -d --webui-port=8080

Mar 02 00:30:34 Overseerr systemd[1]: Starting qBittorrent Command Line Client...
Mar 02 00:30:35 Overseerr systemd[1]: Started qBittorrent Command Line Client.
```

### Overseer

To install Overseer, simply run this one-liner in the terminal as overseer is a snap package:
```bash
sudo snap install overseerr
```

**You're done with the installation! Now, you can move on to the [configuration](#configuration) of the software.**

## Configuration

### User and Group permissions	

Each software needs to have access to your media files. To do so, you need to give the user running the software access to your media files.
By default, here are the users running the softwares:
- Plex: plex
- Radarr: radarr
- Sonarr: sonarr
- Prowlarr: prowlarr
- qBitTorrent: qbittorrent-nox
- Overseer: root (to make sure this is the case, run `systemctl show -pUser,UID snap.overseerr.daemon.service` and check the user is blank and the UID is equal to `[not set]`)

You're going to want all these users to be part of the group `media` so you can more easily give them access to your media files. To know who is part of the group `media`, run this command in the terminal:
```bash
getent group media
```
You should see something like this:
```bash
media:x:1001:prowlarr,radarr,sonarr,qbittorrent-nox,plex,<Your username>
```
(of course, `<Your username>` is replaced by your user account name)

If you don't see all the users, you can add them to the group `media` by running this command in the terminal:
```bash
sudo usermod -a -G media <username>
```
Replace `<username>` with the name of the user you want to add to the group `media`
Once you've added all the users to the group `media`, you can give the group `media` access to your media files by running this command in the terminal:
```bash
sudo chown -R :media /path/to/your/media
sudo chmod -R 775 /path/to/your/media
```

Now, you can move on to the configuration of your media folders.

### Media folders

When it comes to media folders, I **strongly** recommend you to organize your media like this (this is the organization I use and it works perfectly with Plex, Radarr, Sonarr, Prowlarr and Overseer):
```
Media
├── TempDownloads
├── Torrents
├── Movies
│   ├── Movie 1(Year)
│   │  └── Movie 1.(mkv/mp4/...)
│   ├── Movie 2(Year)
│   │  └── Movie 2.(mkv/mp4/...)
│   └── ...
├── Series
│   ├── Series 1
│   │  ├── Season 1
│   │  │  ├── Series 1 - S01E01.(mkv/mp4/...)
│   │  │  └── Series 1 - S01E2.(mkv/mp4/...)
│   │  ├── Season 2
│   │  └── ...
│   ├── Series 2
│   └── ...
└── Music (soon to be supported)
    ├── Artist 1
    │  ├── Album 1
    │  │  ├── Song 1.mp3
    │  │  └── Song 2.mp3
    │  ├── Album 2
    │  └── ...
    ├── Artist 2
    └── ...
```
Of course, you can add more folders like `Documentaries`, `Anime`, `Music Videos`, etc. but this is the basic structure you should have.

> :warning: **You need to make sure your media group has access to all these folders and files** 
> If you don't know how to do that, see [User and Group permissions](#user-and-group-permissions)

Once you've organized your media like this, you can move on to the configuration of the software.

### qBitTorrent

To configure qBitTorrent, you need to go to `http://<your-server-ip>:8080` in your browser. You'll be asked for a username and a password, the default username is `admin` and the default password is `adminadmin`. 
Once you're logged in, go into `Tools` > `Options` > `Web UI` and set the username and password you want. Then,  and set the `Default Save Path:` to the folder where you want your downloads to be saved (If you followed my recommandations it should be `/path/to/your/media/TemDownloads`). I also recommend to check `Copy .torrent files to:` and set it to `/path/to/your/media/Torrents` so you can keep track of the torrents you've downloaded and if you happen to lose one of your file you can find them back easily. When you're done, click on `Save` at the bottom of the page.

To make sure qBitTorrent is working properly, you can download a torrent from a website like [this one](https://archive.org/details/classicpcgames) and add it to qBitTorrent. If the download starts and finishes without any issue, you're good to go.

### Radarr

To start to configure Radarr, visit `http://<your-server-ip>:7878` in your browser. You'll first be asked to enable and configure authentification, choose your preferred method and complete the step.<br>
You can now go in `Settings` > `Media Management` and check the first ckecbox which should be `Rename Movies`, after checking it you should have a new field appear, there you can specify the Movie Name Format you want, I like to be simple and use either : `{Movie Title} ({ReleaseYear}) - {Quality Full}` or even `{Movie Title} ({ReleaseYear})`.<br>
Once this is done, add a Root Folder by clicking the `Add Root Folder` button at the bottom of the page. You can then select the folder you want to add (in our case, the Movies folder). Once you're done, click on `Save` at the bottom of the page. Don't forget to hit save at the top left of the page to save your changes.
Now, it's time to add qBitTorrent as our download client. To do so, click on `Download Clients` in the left sidebar and then click on the `+`. You can then choose the download client you want to add (qBitTorrent) and fill in `Username` and `Password` with the credentials you've set in qBitTorrent. You can leave everything else as is. Once you're done, click on `Test` at the bottom of the form and then `Save`.
Finally, you're gonna want to copy the API key of Radarr to use it in Overseer. To do so, click on `Settings` in the left sidebar and then click on `General`. You can then copy the API key and save it somewhere safe for later.

### Sonarr

To configure Sonarr, visit `http://<your-server-ip>:8989` in your browser. Then, it's pretty much the same process.<br>
Don't forget to hit save at the top left of the page to save your changes.
And don't forget to copy the API key of Sonarr to use it in Overseer.

### Prowlarr

To start to configure Prowlarr, visit `http://<your-server-ip>:9696` in your browser. You'll first be asked to enable and configure authentification, choose your preferred method and complete the step.
Then, the first thing you need to do is to add indexers. To do so, click on `Indexers` in the left sidebar and then click on `Add New Indexer`. You can then choose the indexer you want to add and follow the instructions to add it.
I recommend the following indexers: 
- TheRARBG
- kickasstorrents.ws
- Torrentz2nz
- 1337x (if you have a VPN)
- Nyaa.si (if you watch anime)
- Bangumi Moe (if you watch anime also)
Once you've added the indexers you want, you can move on to the next step which is to add download clients. To do so, click on `Settings` in the left sidebar and then click on `Download Clients`. You can then click on the big `+` button to add a new download client. You can then choose the download client you want to add (qBitTorrent in our case).
Here, fill in the informations such as the username and the password. You can leave the category blank. Once you're done, click on `Save` at the bottom of the page.

Now, let's add Radarr and Sonarr as our Applicatons. To do so, click on `Settings` in the left sidebar and then click on `Apps`. You can then click on the big `+` button to add a new application. You can then choose the application you want to add (Radarr or Sonarr). Here, fill in the API key you've copied from Radarr or Sonarr. Once you're done, click on `Save` at the bottom of the page.

### Plex

To configure Plex, you need to go to `http://<your-server-ip>:32400/web` in your browser, link your Plex account and then click on `Got it` and close the Plex Pass subscription plans proposal.
Give your server a name which allows you to easily identify it and click on `Next`.
Then, you can add your media folders by clicking on `Add Library` and then selecting the type of media you want to add (Movies, Series, Music, etc.). You can then select the folder you want to add (in our case, the Movies folder and then the Series one). Once you're done, click on `Next` at the bottom of the page. 
You can then click on `Next` again and then `Done` at the bottom of the page.<br>
Now, if you want to create multiple local user accounts, click on the wrench on the top right of the page and then click on `Plex Home` and then `Create managed Account`. You can then fill in the informations.

### Overseer

> This is the last step of the configuration, once you've done this, you're done with the configuration of your media server. 

Go to `http://<your-server-ip>:5055` in your browser. You'll be asked to sign-in using your Plex account, once you do so, you'll be asked to setup which Plex server you wanna use.
Click on the refresh arrow and select `Manual Configuration` in the dropdown menu if not already set, then set the IP to be `localhost` and click on `Save Changes`.<br>
Under `Plex Libraries` you should now see the libraries you've added in Plex, you can now check both of them and click on `Start Scan` and `Continue`.<br>
Now, you'll be asked to add your Radarr and Sonarr instances, you can do so by clicking on `Add Radarr Server` and then filling in the following :
- Default Server: 🗹
- 4k Server: ☐
- Server Name: Main Radarr
- Hostname or IP Address: `localhost`
- Port: 7878
- Use SSL: ☐
- API Key: The API key you've copied from Radarr
Once these informations are filled in, click on `Test` and then fill in the following dropdowns :
- Quality Profile : Any
- Root Folder : `/path/to/your/media/Movies`
- Minimum Availability : Released
- Enable Scan : ☑
- Enable Automatic Search : ☑

You can then click on `Add Server` to save your changes.
Then click on `Add Sonarr Server` and then repeat the process with your Sonarr instance.
Just switch the name to Main Sonarr and choose the right API key.
In the dropdowns, you can fill in the following :
- Quality Profile : Any
- Root Folder : `/path/to/your/media/Series`
- Language Profile : Deprecated
- Anime Quality Profile : Any
- Anime Root Folder : `/path/to/your/media/Series`
- Anime Language Profile : Deprecated
- Enable Scan : ☑
- Enable Automatic Search : ☑

You can then click on `Add Server` to save your changes.

Finally, you can click on `Finish Setup` and you're done with the configuration of your media server.

**Congratulations! You've successfully created your own media server! <br> Feel free to explore all the options available to you in Overseerr !!!**

---

## Credits and software used

Made with ❤️ by [Ano0002](https://github.com/ano0002/)

- [Trash Guides](https://trash-guides.info/)
- [Servarr](https://wiki.servarr.com/)
- [Plex](https://support.plex.tv/)
- [Docker](https://docs.docker.com/)
- [Ubuntu](https://ubuntu.com/)
- [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
- [qBitTorrent](https://www.qbittorrent.org/)
- [Overseerr](https://overseerr.dev/)