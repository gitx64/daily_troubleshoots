# wifi-device-unavailable-networkmanager
**Date:** 27-09-2026
**System:** "Debian GNU/Linux 13 (trixie)"
**Status:** Solved

---

## Problem
<!-- What happened? What isn't working? -->

wlo1 interface showing unavailable. After proper investigation what we found is ifupdown was the culprit which was managing the wifi with its own wpa_supplicant and dhcp. So when NetworkManager trying to grab wifi interface it cant because there is an already existing supplicant managing the wifi. 

## Investigation
<!-- Commands executed and what their output revealed. -->

```bash
rfkill list
cat /etc/network/interfaces
ip link show wlo1
nmcli device status
iw dev wlo1 info

nmcli -f GENERAL.STATE,GENERAL.REASON,GENERAL.NM-MANAGED,GENERAL.AUTOCONNECT,GENERAL.CONNECTION device show wlo1

systemctl is-active NetworkManager
systemctl is-active wpa_supplicant
systemctl is-active iwd

ps aux | grep -E '[w]pa_supplicant|[i]wd'


systemctl status wpa_supplicant
systemctl status wpa_supplicant@wlo1
systemctl status NetworkManager

systemctl --no-pager status NetworkManager
systemctl --no-pager status wpa_supplicant@wlo1

ps -o pid,ppid,stat,args -p 1136,1213
sudo cat /proc/1213/cgroup
sudo journalctl -b -u NetworkManager --no-pager -n 100
```

## Attempts
<!-- What did you try? What happened after each attempt? -->

- First if its blocked by `rfkill` hard or soft. -> wasn't  
- Tried to see if kernel modules and drivers are properly installed or not. -> installed properly and was in use.
- if ip command is showing linking status to the interface. -> showing properly
- if networkmanager recognizing it. -> recognized but was showing unavailable

## Solution
<!-- What fixed the issue? Leave pending if unresolved. -->
- Turnedout the wireless interface was also managed by ifupdown. And the NetworkManager unable to capture the inteface supplicant was 
ifupdown had already captured the interface with its own spawned wpa-applicant. 

- in /etc/NetworkManager/NetworkManager.conf make sure [ifupdown] section is set to managed=true if the interface in nmcli showing unmanaged.
- in /etc/network/interfaces remove the wifi interface to prevent ifupdown to take over the interface before networkmanager even get a chance.
- stop ifup@<interface-name> service.1
- Networkmanager then spawns its own supplicant to capture the interface and then create new connection with nmcli.

## What I Learned
<!-- What Linux concept or diagnostic technique did I learn? -->
Sometimes its not necessary that the module or the network management has some bug, but it may happen that two similar services are conflicting with each other for being run at the same time. with ps command we can determine if such things are happening or not.

## Next Time
<!-- What would I check first if this happened again? -->

If this kind of situation happens that the interface is not blocked by rfkill, wpa_supplicant is running as system service. 
Interface is there but the networkmanager is showing unavailable, I will at first check if ifupdown is again taking control over the interface and making it unavailable.


