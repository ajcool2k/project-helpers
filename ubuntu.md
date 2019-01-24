# Useful Linux commands

## Linux OS

    uname -a                                # print system information

## Debug

    tail -f filename.log                    # follow log file
    tail -f /var/log/syslog                 # Network logs

## Filter
    apt list | grep 'rhythmbox'             # Match
    apt list | grep -v 'bionic'             # Inverse match shows all packages that are not from bionic store
    
## Packages

    apt list --installed                    # Installed user packages
    dpkg --list | grep firefox              # Installed packages from debian installer
    
    ls /var/cache/apt/archives/             # Install cache packages
    
## Print

    lpq -a                                  # Show all pending print jobs
    lprm [id]                               # Cancel print job

## Copy

    scp filename.txt user@host:/myPath      # Copy file from local filesystem to target filesystem
    scp -r foldername user@host:/myPath     # Copy folder from local filesystem to target filesystem

# Process management

> Processes can be easily managed by systemd

    sudo nano /lib/systemd/system/myApp.service     # create own service config
    sudo systemctl daemon-reload                    # system control need to reload service files
    sudo systemtl enable myApp                      # automatically start myApp service after boot sequence
    sudo systemctl start myApp                      # manually start myApp service
    sudo systemctl status myApp                     # show status of myApp service
    sudo systemctl stop myApp                       # manually stop myApp service
    sudo systemctl restart myApp                    # manually restart myApp service
    sudo systemctl disable myApp                    # remove myApp service from auto start
