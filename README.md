# Windows OpenSSH Setup

Setting up OpenSSH on Windows

## Setup

Add OpenSSH to Windows

```powershell
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'
```

Should Output:

```powershell
Name  : OpenSSH.Client~~~~0.0.1.0
State : Installed

Name  : OpenSSH.Server~~~~0.0.1.0
State : NotPresent
```

Enable OpenSSH

```powershell
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```

Start the Service as a Windows Service

```powershell
Start-Service sshd
Get-Service sshd
```

Automatically start the service on boot

```powershell
Set-Service -Name sshd -StartupType 'Automatic'
```

Set default shell (by default it is CMD 🤮)

```powershell
# Gotta find an up to date command
```

## VScode Remote SSH Setup

Edit your VSCode SSH config and add the following:

```.ssh
Host <No Spaces Name to Identify Host>
  HostName <name of your pc>.local
  User <your windows username>
  IdentityFile <path to a pem file or skip to let VSCode prompt password input>
```

Follow Remote Window usage instructions.

Enjoy!
