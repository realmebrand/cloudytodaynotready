# Cloudready notes

## Disable Auto-Updates on Home edition

Some times our users of the free-edition come across use cases or scenarios where they would like to prevent updates.  

Home edition only - The following instructions are to block updates for the Home edition only. 

Warning: These instructions are for advanced users only and may lead to unexpected behavior. Please proceed with caution.

 
First, make sure you are installed with the CloudReady version you want to stay on
 
Log in, and then press ```Ctrl+Alt+T``` to bring up a cmd line - you should see a yellow prompt like this:
 
Now run the cmd 

```shell```
 

Now run 

```sudo disable_verity```
 
When that returns, run

```sudo reboot```
 
After your system starts, repeat steps 2, 3, and 4
 
Next you need to make the file system write-able so you can make an edit. To do so, run the cmd

```sudo mount -o rw,remount /```

(You will be prompted for a password - the default is "chrome")
 
Next we'll make a backup copy of the file we're about to change:

```sudo cp /etc/lsb-release /etc/lsb-release.bak ```
 
Finally, we can edit the URL that CloudReady looks for updates from, so that there'll be no response for an update check. To do this:
Confirm you've disabled verity as mentioned above

```sudo vim /etc/lsb-release```

(You might need to enter your password here when prompted)
 
Edit the lines

```CHROMEOS_AUSERVER..." and "...CHROMEOS_DEVSERVER..." ```

Assuming nothing went wrong above, now reboot
 
Those changes should now prevent updates. If you want to re-enable updates you just need to take your backup copy and copy it back into place, replacing the edited version:

```sudo cp /etc/lsb-release.bak /etc/lsb-release```
 
