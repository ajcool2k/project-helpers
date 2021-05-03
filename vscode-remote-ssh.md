# Remote development with vscode

Guide to connect to a Windows VM using vscode where git is used to manage repository contents.

## Server-side (Remote/VM)

**Setup Open-SSH**

- Install Optional Feature OpenSSH-Server (needed for accepting client requests)
- Install Optional Feature OpenSSH-Client (needed for VM to Azure/GitHub)

```bash
Start-Service sshd
# OPTIONAL but recommended:
Set-Service -Name sshd -StartupType 'Automatic'
# Confirm the firewall rule is configured. It should be created automatically by setup.
Get-NetFirewallRule -Name *ssh*
# There should be a firewall rule named "OpenSSH-Server-In-TCP", which should be enabled
# If the firewall does not exist, create one
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

- Create ssh keys

```bash
ssh-keygen
```

- Copy public key to user settings of the repository provider (Azure/GitHub)

![image](https://user-images.githubusercontent.com/23473452/116811846-b2776c80-ab4b-11eb-9e2b-827cc6add8d3.png)


**Activate ssh-agent to avoid passphrase for git**

1. Start the ssh-agent from Windows Services:
2. Find the OpenSSH Authentication Agent in the list and double click on it
  - open Properties
  - choose Automatic
  - choose start (if not already running)

```bash
# Make sure you're running as an Administrator
Start-Service ssh-agent

# This should return a status of Running
Get-Service ssh-agent

# Now load your key files into ssh-agent
ssh-add ~\.ssh\id_rsa
```

**Let git use OpenSSH feature (Windows Only)**

- `git config --global core.sshCommand C:/Windows/System32/OpenSSH/ssh.exe`

**Make sure git repository uses ssh url instead of https to avoid user/password**

- research for ssh-cloning address

![image](https://user-images.githubusercontent.com/23473452/116811483-ece00a00-ab49-11eb-8a64-62dec81e15e3.png)

- go to cloned repository and open .git folder
- edit `config` file and replace https address with ssh addresses


## Client

**Open-SSH**

- Install Optional Feature OpenSSH-Client
- Create ssh keys using PowerShell

```bash
Start-Service sshd
# OPTIONAL but recommended:
Set-Service -Name sshd -StartupType 'Automatic'
# Confirm the firewall rule is configured. It should be created automatically by setup.
Get-NetFirewallRule -Name *ssh*
# There should be a firewall rule named "OpenSSH-Server-In-TCP", which should be enabled
# If the firewall does not exist, create one
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

- copy public key to server using scp or manually into: `C:\Users\username\.ssh\authorized_keys`
- try connecting to server using ssh

```bash
ssh username@servername
```
- (optional) when username at server is admin user
  - open `C:\ProgramData\ssh\sshd_config`
  - comment out lines:
    
    ```txt
    #Match Group administrators
    #AuthorizedKeysFile __PROGRAMDATA__/ssh/administrators_authorized_keys
    ```
  - Restart sshd service using powershell

    ```bash
    Restart-Service sshd
    ```
    
- Install vscode development extension: https://aka.ms/vscode-remote/download/extension
- Open ssh host `ssh username@servername`
