# Windows Utils

**Clean all USB partitions**

run `cmd` as administrator


    $ diskpart
    $ diskpart list
    $ dispark select [number]   # select disk number of the usb
    $ clean
    $ exit
    
    
**Windows 10 Update manual installation**

- download MediaCreationTool
- install Windows 10 on USB


**Use Resource Monitor to find processes that lock files**

- run resourse monitor as administrator
- select tab CPU
- select Associated handles and input filename.ext into textfield


**Find text liken grep for Windows**

```bash
# using findstr like grep
netstat -a -n | findstr 80
```

**Find files containing text**

```bash
# find files recursivly that contain string "foo"
findstr /s /i /p /m foo *

# shows content matches and line numbers
findstr /s /i /p /n foo *
```
