# Useful Linux commands

## Linux OS

    uname -a                          # print system information

## Debug

    tail -f filename.log              # follow log file
    tail -f /var/log/syslog           # Network logs


## Packages

    apt list --installed              # Installed user packages
    dpkg --list | grep firefox        # Installed packages from debian installer
    
    ls /var/cache/apt/archives/       # Install cache packages
    
## Print

    lpq -a                            # Show all pending print jobs
    lprm [id]                         # Cancel print job
