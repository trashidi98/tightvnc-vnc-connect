# Using TightVNC 

TightVNC is a fast easy to use VNC application to launch on any sort of linux machine. 

## How to set up? 

Follow this guide to launch on a local network: https://serverspace.io/support/help/install-tightvnc-server-on-ubuntu-20-04/

Although the article is written as though it is plug and play (it might be) it did not work on my system when connecting a Windows PC (client) to a Linux Mint PC running TightVNC (server). 

The fix however, was to do the following 

1) After installing tightvnc, and running the steps, stop at the step where you are editing the config file ~/.vnc/xstartup 

```
nano ~/.vnc/xstartup
```

2) Paste this xstartup file instead

```
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
startxfce4 &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
```

This will work with xfce desktop environments but feel free to use gnome or kde if needed. 


