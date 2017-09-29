Create network share with Samba
=

Update and upgrade
> sudo apt-get update && sudo apt-get upgrade

Install `samba`
> sudo apt-get install samba

Make a backup of the original config file
> sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.def

Edit config
> sudo nano /etc/samba/smb.conf

```
[hdd]
  comment = External hard drive
  path = /media/pi/hdd
  read only = yes
```

Add `smb` user
> sudo smbpasswd -a pi


Restart `samba`
> sudo service smbd restart

Check `smb.conf` for any syntax errors
> testparm

