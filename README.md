# Curator Installation
This repo details how to install all of the various components of a Curator system.

## Prerequisites
We'll need [Nodejs](https://nodejs.org/en/), [Git](https://git-scm.com/), [Android Studio](https://developer.android.com/studio/index.html) and [Atom](https://atom.io/) installed. For Windows, we'll use [Chocolatey](##Chocolatey-Installation) to take care of this. 

### Chocolatey Installation
Run this in an administrative **Powershell** session.
```ps
Set-ExecutionPolicy Bypass; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

```

### The Rest
Close that **Powershell** session and open a new one with administrator priviledges.
```
choco install -y nodejs git androidstudio atom
```

## Get SSH configured for Github
_**Windows Note**: These commands will have to be run in Git Bash, which is installed with Git. Leave the session open as you work through the other installation instructions, as you'll need it from time to time.  
**Git Bash must be run as Administrator**_  



First, we'll need to download the ssh private key file [here](https://drive.google.com/a/sparrowav.com/file/d/0B_MvBkpX7P0mTGhod0hJR0JHeUk/view?usp=sharing). It'll require that you sign into your Spectiv Google account. After the key downloads, we'll start the ssh agent that will handle authentication for us with the following command.  
```
eval "$(ssh-agent -s)"
```

Once that's running, we'll need to add the key file to that agent. It'll ask for a password.  
```
ssh-add /path/to/key/file
```
Open Slack and type `github key file password` to get the password.


## Installation

**Important** - Make sure that you've done everything above before moving on to the installation instructions linked below.

**Install on the server computer**
* [Curator Server](https://github.com/euroclydon37/curator-installation/blob/master/Curator-Server.md) is the hub that controls all of the players running on the network.  
* [Power App](https://github.com/euroclydon37/curator-installation/blob/master/Power-App.md) is written by Adam and is used to cycle the outlets of a smart powerstrip.

**Install on the Sony Monitors**
 * [Android app](https://github.com/euroclydon37/curator-installation/blob/master/Android-Player.md) displays images and streams videos given to it by `Curator Server`.  

**Install on a laptop or other personal computer**
 * [Curator app](https://github.com/euroclydon37/curator-installation/blob/master/Curator-App.md) is the place where users can configure players, content, and playlists.  
