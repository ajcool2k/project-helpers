# Useful Linux commands

**Linux OS**

```bash
uname -a                                # print system information
neofetch                                # shows information to linux os & dist
```

**Debug**

```bash
tail -f filename.log                    # follow log file
tail -f /var/log/syslog                 # Network logs
```

**Filter**

```bash
apt list | grep 'rhythmbox'             # Match
apt list | grep -v 'bionic'             # Inverse match shows all packages that are not from bionic store
```

**Packages**

```bash
apt list --installed                    # Installed user packages
dpkg --list | grep firefox              # Installed packages from debian installer

ls /var/cache/apt/archives/             # Install cache packages
```

**Print**

```bash
lpq -a                                  # Show all pending print jobs
lprm [id]                               # Cancel print job
```

**Secure Copy**

```bash
scp filename.txt user@host:/myPath      # Copy file from local filesystem to target fs
scp -r foldername user@host:/myPath     # Copy folder from local filesystem to target fs
```

**Networking**

```bash
ifconfig								# show network information
iwconfig								# show wireless information
ifup [interface]						# activate network interface
ifdown [interface]						# deactivate network interface
ping [host]								# show connection details to host
traceroute [host]						# show routing to host
netstat -tupl							# show activate listening ports
```

**Processing**

```bash
[cmd] &									# run command in background
[cmdA] ; [cmdB]							# run cmdA then cmdB
[cmdA] | [cmdB]							# run cmdA and use output as input in cmdB
[cmdA] || [cmdB]						# run cmdA and cmdB when cmdA was not successful
[cmdA] && [cmdB]						# run cmdA and cmdB when cmdA was successful
```

