# GalaxyBook2Linux
Issues and possible solutions to the galaxy book 2 NP750XED-KC1SE
Keep in mind that this process is not the simplest, and if you don't know what you are doing this is my friendly reminder that I don't take any responsibilty for what could happen to your system YOU HAVE BEEN WARNED! 

[Issues]
Lid sleep sensor is borked, if not disabled system will put the device into sleep all the time. 
Everything else works, on my i3-1215u without backlight and without the fingerprint scanner nothing else is currently broken.

[Installing]
I installed arch. I've heard success with other distros like Ubuntu, and debian, but not done testing personally on theese distros. Installing arch should go smooth (make sure to select grub for boot-manager, and create a root password)
[Caution] when rebooting be sure to hit e over the arch boot option, and edit the GRUB_CMDLINE_LINUX_DEFAULT to add the word single to boot into single user mode. When booting enter the root password you added and hit enter.
[Patching]
You will have to change 2 config files now, use your prefered text editor. Change the followin line in /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
To GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_dc=0 intel_idle.max_cstate=2". 
Save and exit
Now you will have to fix the sleep issue.
Edit /etc/systemd/logind.conf and change the following lines to this:
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
Now you can save and exit and all you have to do is reboot! 

Written and updated on 28/12-2023
Sorry if my english is broken.
Good luck!
