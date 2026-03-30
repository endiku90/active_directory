# Installing the DC

1. User `sconfig` to:
    - Change hostname
    - Change IP Address to static
    - Change the DNS server to our own IP Address (it is set to loopback address per default)

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

5. Add WS01 to domain
    - Set dns server (to domain)
    ```shell
    Get-DnsClientServerAddress (take interface index)
    Set-DnsClientServerAddress -InterfaceIndex 4 -ServerAddresses 192.168.79.155
    ```
    - Account, Access Work School, Connect, Join Domain
    (add-computer -domainName runge.str -credential runge.str\Administrator -force -Restart)


* Crear session PSSession
```shell
 $dc=New-PSSession 192.168.79.155 -Credential (Get-Credential)
 Enter-PSSession 3
 ```
 
 # mandar a la otra session

  cp .\ad_schema.json -ToSession $dc C:/Windows/Tasks
