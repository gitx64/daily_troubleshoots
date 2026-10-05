# Looking for a network application is running or not properly.

We will use different tools to test it : 

- ss(socket statistics): Modern alternative to netstat which searches specific socket and tells about the listening sockets or ports.
    **-t** : TCP sockets
    **-l** : Listening sockets
    **-n** : Show numerical addresses (dont try to resolve names)
    **-p** : Listening sockets


- nc(netcat): Swiss army knife of modern networking observation. To establish connection with a port and see if the port is listening.

    **-v** : Verbose mode
    **-z** : Zero I/O actions, means no need to send data just establish the connection

- grep: to extract the data from raw info.


# Process Begins:

```bash
python3 -m http.server 8081 &
```


## ss command: 

```bash
ss -tlnp | grep 8081 # shows the tcp listening sockets
```

after looking for the running socket is active,


