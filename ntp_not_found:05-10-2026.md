# ntp_not_found
**Date:** 05-10-2026
**System:** "Debian GNU/Linux 13 (trixie)"
**Status:** solved

---

## Problem
<!-- What happened? What isn't working? -->
After a boot, My system time was incorrect and way past. And the region was also right which I selected previously manually. But something got wrong which I don't know what.


## Investigation
<!-- Commands executed and what their output revealed. -->
After careful investigation I found out there was no timesync client installed 
at all like any ntp-client, chrony or systemd-timesyncd. I tried to see if NTP itself was working or not but it was showing N/A.


## Attempts
<!-- What did you try? What happened after each attempt? -->

```bash
sudo timedatectl status
```
shown NTP : n/a


## Solution
<!-- What fixed the issue? Leave pending if unresolved. -->
Because Time wasn't correct and my sources in debian were set to https explicitly.I couldn't install anything also because it was restricting to establish a secure
SSL/TLS cert between the transaction. So first I manually check the network from another device and set it with

```bash
sudo date -s "<current year YY-MM-DD><space><current time HH:MM:SS>"
```
Then I installed an ntp client (systemd-timesyncd) and enabled it. And did a reboot. The issue was successfully resolved.

## What I Learned
<!-- What Linux concept or diagnostic technique did I learn? -->

Nothing special but learnt about the work of NTP or automatic network time syncing and why its important for modern networking.


## Next Time
<!-- What would I check first if this happened again? -->

I would check if the NTP is working well. If not then i will reload the daemon of the ntp client to make sure it works okay. If that doesn't work well i make the manual changes temporarily and look for the possible reasons of malfunctioning.

