# Curator Server
`Curator server` is the hub that controls all of the Curator players that exist on your network.

# Installation

### Download Curator Server
In the **Git Bash** session you opened, Create and navigate to the directory that `Curator Server` will live in.

_Windows_  
```
cd C:
mkdir Curator-Server && cd Curator-Server
```

_Linux and MacOS_  
```
mkdir ~/Curator-Server && cd ~/Curator-Server
```

Initialize the directory for Git and download `Curator Server`
```
git init
git pull git@github.com:euroclydon37/Curator-Server.git master
```

# Configuration

We need to configure the environment before starting the server. On Windows, we need to finish the rest of this document in **Powershell**. Let's start with installing all of the dependencies.
```
npm install
```
Next, we need to create the site-specific `.json` file.  

_Powershell_
```
echo $null >> data/site-config.json
```
_MacOS or Linux_
```
touch data/site-config.json
```

Open `data/site-config.json` with Atom.
```
atom data/site-config.json
```

Delete anything that's there (Powershell likes to put unknown characters) and paste the following into it. Replace `LocationName` with the actual name that you want to show up in the app.
```json
{
	"name":"LocationName",
	"autostart":true
}
```

# Running the server
We're going to use a process manager to run the server. This will make it easier to check on the status of the server and still give us the ability to view its output if we choose. It'll also restart it if it crashes for whatever reason.  

### Install PM2

_If working in **Powershell**, run this command in a separate Administrator session and omit `sudo`_
```
sudo npm install -g pm2
```

### Start the Processes.  
_**Powershell Note**: Run this command in the original Powershell session you opened._
```
pm2 start content-server.js
pm2 start main.js
```

### Surviving Reboots
First, we need to save the process list.
```
pm2 save
```
Next, we'll handle the auto start functionality.

_Powershell - You'll need to open an **Administrator** session for this command._
```
npm install pm2-windows-startup -g
pm2-startup install
```

_MacOS and Linux_
```
pm2 startup
```

Now, let's reboot the computer to make sure that our processes are indeed starting on bootup. Once the computer is up and running, simply type
```
pm2 list
```
Verify that they're running and move on.

### Remote Monitoring
_Skip this section for now. We don't pay for it._
```
pm2 register
```
To get the password, open slack and type `pm2` into any channel. Slackbot will respond with the account information.

Once that's finished, it should launch a browser window where you can sign into PM2 and verify that the process information is showing up.

# Conclusion
You should be up and running and the server should be viewable from the app, now.
