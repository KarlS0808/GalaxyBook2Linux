# GalaxyBook2Linux
Issues and possible solutions to the galaxy book 2 NP750XED-KC1SE
Keep in mind that this isn't a 100% fix only a bypass to kernel issues, and I wouldn't recommend using this as your main operating system if you have important data, it might be bricked or fixed in the future with kernel patches. Hopefully the sleep issues will get fixed.
[Prerequistes]
Be sure to switch to your preferred power mode BEFORE installing linux. It's not possible to use the switch after the installation of linux, and I've made the mistake of putting mine in totally quiet mode leading to it overheating. Also note that you might lose all of your data doing this, so take a backup. 
[Issues]
Lid sleep sensor is borked, if not disabled logind will make the system will go into a sleep loop. 
Note about the sleep issue, it works partially in kde plasma, but ONLY when in the de, it still goes into a permanent sleep loop if you get logged out, so it's not recommended to skip the sleep patching step.
Everything else works, on my i3-1215u without backlight and without the fingerprint scanner nothing else is currently broken.

[Installing]
I installed Arch. I've heard success with other distros like Ubuntu, and debian, but not done much testing personally on these distros (debian 12 a while back, and it had the same functionality as Arch had). Installing arch should go smooth (make sure to select grub for boot-manager, and create a root password)
After installation hiy yes to chroot into the installed partition.

[Patching]
You will have to change 2 config files now, using your prefered text editor. Change the following line in /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
To GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_dc=0 intel_idle.max_cstate=2". 
Save and exit

Now you will want to fix the sleep issue.
Edit /etc/systemd/logind.conf and change the following lines to this:
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore

Now you can save and exit and all you have to do is reboot! 

Written and updated on 14/5-2025, 
Working as of now, the system has been stable over the past two years. 
Good luck!


sources: https://forums.linuxmint.com/viewtopic.php?t=381597
