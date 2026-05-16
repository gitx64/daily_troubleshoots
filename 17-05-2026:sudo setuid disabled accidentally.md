## If any critical program like sudo, accidentally the setuid disabled on the program, how to recover it

-> 

1. first fetch a liveiso with a bootable iso of linux.
2. boot into the liveiso and mount the actual root partition of the system.
3. after mounting use the command **chroot**, and change the login to the root:

```bash
sudo chown root:root -R /desired/directory/path
sudo chmod 4755 /desired/programmed/where/setuid/needed
```
4. After verifying everything you can exit from the chroot and boot into your pc.

Thats it ;)
