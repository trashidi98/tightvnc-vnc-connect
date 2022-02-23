# Using TightVNC 

TightVNC is a fast easy to use VNC application to launch on any sort of linux machine. 

## How to set up? (Serverside) 

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

Here's your final product ![](https://github.com/trashidi98/tightvnc-vnc-connect/blob/master/connected-xfce.png)

## Extend the concepts

- The second part to the original guide explains how to actually use VNC through SSH tunnel: https://serverspace.io/support/help/vnc-connection-ssh-tunnel-ubuntu-20-04/

- Linode has a lot of guides on Remote Desktops: https://www.linode.com/docs/guides/applications/remote-desktop/

- Try a different VNC Server: x11vnc which David Dombal shows in his two step video

1) https://www.youtube.com/watch?v=mIdF7K3Nmlw

2) https://www.youtube.com/watch?v=3K1hUwxxYek

3) The original guide he references is here https://www.crazy-logic.co.uk/projects/computing/how-to-install-x11vnc-vnc-server-as-a-service-on-ubuntu-20-04-for-remote-access-or-screen-sharing

This is what I thought VNC should look like initially since it actually allows you to remote in and control the desktop as is

- My next probable steps would be to install Apache Guacamole, VNC through Docker on the Web: https://www.linode.com/docs/guides/installing-apache-guacamole-through-docker/

- Figure out how to VNC in over maybe VPN connection, access your computer from anywhere

