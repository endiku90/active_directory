# Installing the DC

1. User `sconfig` to:
    - Change hostname
    - Change IP Address to static
    - Change the DNS server to our own IP Address

    (Manually https://itluke.online/2018/04/27/how-to-change-a-static-ip-address-with-powershell/)

2. Install the AD Windows Feature

```shell
Install-WindowsFeatureAD-Domain-Services -IncludeManagementTools
import-module ADDSDeployment
install-addsforest
```


3. Setting Mgmt WS01
- Install chocolatey
- install git & vscode
4. Enable PSSession
    - start-service winrm
    - set-item wsman:\\localhost\Client\TrustedHosts -value 192.168.79.155
    - New-PSSession -ComputerName 192.168.79.155 -Credential (get-credential)
    - Enter-PSSession 1

