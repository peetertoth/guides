Install Deluge deamon and (web)client to RaspberryPi
=

Install daemon and console
-
1. Update and upgrade
> sudo apt-get update && sudo apt-get upgrade

2. Install deluge daemon and console
> sudo apt-get install deluged && sudo apt-get install deluge-console

Configure authentication
-
1. Start and stop daemon to generate default config file
> deluged && sudo pkill deluged
 
2. Copy original config, then open to edit
> cp ~/.config/deluge/auth ~/.config/deluge/auth.def && nano ~/.config/deluge/auth

3. Add new line to the bottom of the text, with the following convention
> user:password:level

- Example:
pi:V3ryD1fficultP4ssw0rd:10

4. Save changes
  1. WriteOut `Ctrl + O`, `Enter`
  2. Exit `Ctrl + X`

Configure daemon
-
1. Start daemon and open console
> deluged && deluge-console

2.  Set `allow remote`

  1. check status
  > config allow_remote

  2. set status (if needed)
  > config -s allow_remote True

  3. Leave console
  > exit

3. Restart deluge
> sudo pkill deluged && deluged

Connect with deluge client (from your PC)
-
1. Start delgue client
2. Disable classic mode

  1. Go to `Settings(Ctrl + P)` > `Interface` 
  2. Uncheck `Classic mode`
  3. Click on `Apply`
3. Restart client
4. Add connection 

  - Hostname: Raspberry's IP address
  - Username and Password (from _Configure authentication step 3._)

Setup WebUi
-
1. Install WebUi
> sudo apt-get install python-mako  && sudo apt-get install deluge-web

2. Start `deluge-web`
>  deluge-web&

  It will start deluge-web in the background and now you can connect to it, just open your web browser end enter `IP_OF_RASPBERRI_PI:8112`

Set Deluge and WebUi to start at startup
-
1. Open `rc.local`
> sudo nano /etc/rc.local

2.  Insert the following before `exit 0`
> sudo -u pi deluged
> sudo -u pi deluge-web

3. Test: restart device
> sudo init 6