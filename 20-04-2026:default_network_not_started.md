## What to do if default network not started error shows?
- After every reboot default network in qemu or the NAT device is going todisabled. To fix this issue:

First run this command:
```bash 
virsh net-autostart default
```

if this runs well then good, if not:
```bash
virsh net-list --all
```
if default is there (probably not) then good, if not:

```bash
virsh net-define /usr/share/libvirt/networks/default.xml
```
if successful: run step01 again, and **sudo virsh net-start default**

