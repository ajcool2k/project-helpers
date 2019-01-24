# Process management

> Processes can be easily managed by systemd

## Service config
    sudo nano /lib/systemd/system/myApp.service     # create own service config

## Systemd control
    sudo systemctl daemon-reload                    # system control need to reload service files
    sudo systemctl enable myApp                     # automatically start myApp service after boot sequence
    sudo systemctl start myApp                      # manually start myApp service
    sudo systemctl status myApp                     # show status of myApp service
    sudo systemctl stop myApp                       # manually stop myApp service
    sudo systemctl restart myApp                    # manually restart myApp service
    sudo systemctl disable myApp                    # remove myApp service from auto start
