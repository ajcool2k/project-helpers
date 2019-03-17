# Process management

> Processes can be easily managed by systemd



## Create service config

```bash
sudo nano /lib/systemd/system/myApp.service        # create own service config
```



### Example

```properties
[Unit]
Description=My Great API
Documentation=https://example.com
After=network.target                                            # start service after network boot

[Service]
Type=simple                                                     # normal start
User=noRootUser                                                 # user that should run the Exec command
ExecStart=/path-to-nodejs/node /path/myApp.js --port 3002       # command that the User should run
Restart=on-failure                                              # restart only when application did not got safely shutdown

[Install]
WantedBy=multi-user.target
```



## systemd control

```bash
systemctl                                   # lists all services
systemctl status myApp                      # show status of myApp service

sudo systemctl daemon-reload                # system control need to reload service files
sudo systemctl enable myApp                 # automatically start myApp service after boot
sudo systemctl start myApp                  # manually start myApp service
sudo systemctl stop myApp                   # manually stop myApp service
sudo systemctl restart myApp                # manually restart myApp service
sudo systemctl disable myApp                # remove myApp service from auto start
```