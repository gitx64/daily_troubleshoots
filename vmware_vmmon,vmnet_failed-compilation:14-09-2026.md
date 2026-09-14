## If you see that after running vmware either from gui or 
## vmware-modconfig --console --install-all is failed to compile
## vmmon and vmnet kernel modules

There will very much chance that Secure Boot is enabled which is preventing the module to be installed. So check it with

```bash
sudo mokutil --sb-state
```
then as per the status turn that off or leave it off.

If on debian 13 there is a known issue of IBT to be enabled and turning it off reportedly fixes the issue. You can check that out on internet.
