## If pressing tab to bash-complete, gives much more info like cur="$3" for curl or something like that.

The most common fix will be setting the verbose mode off globally through 

```bash 
set +v
```
This will disable the verbose mode and will work perfectly.
