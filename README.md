# nvoc
Nvidia overclocking script for Linux (useful for autostarting!)

Because I didn't want tools like GWE to launch on autostart and be on the background just to apply my overclock.  
This just applies the clocks and exits. It's useful in that there is no way to save overclocks on Linux/Nvidia and they are
lost on every reboot, so nvoc fills in that gap.

Needs the proprietary Nvidia drivers to work.
Doesn't use root (so don't expect nvidia-smi functionality such as watt power limits on the future)

Grab the zip, unzip it and have a look at the files.  
Edit the gpu0.conf file and set your preferred clocks in the Options section.  
Now, we copy the configuration file to a special folder: `sudo mkdir /etc/nvoc.d; sudo cp gpu0.conf /etc/nvoc.d/`
Make the script executable: run `chmod +x nvoc`  
Then place the script in `/usr/bin`. Then, run `nvoc` to have it apply your settings.  

The whole point of nvoc is to have it autostart with the desktop session.
To have it autostart with the desktop, open a terminal and run:  
`nano ~/.config/autostart/nvoc.desktop`

Then, paste in the following and save (Ctrl+X)
```
Exec=nvoc
Icon=system-run
Name=nvoc
OnlyShowIn=
Path=
Terminal=False
Type=Application
```
All done. Overclocks will now be applied as soon as you log into your desktop.  
If you don't use a desktop (say, on a coin mining headless box) you could have the script run on boot via cron.
