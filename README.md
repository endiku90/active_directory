# Installing the DC

1. User `sconfig` to:
    - Change hostname
    - Change IP Address to static
    - Change the DNS server to our own IP Address

2. Install the AD Windows Feature

```shell
Install-WindowsFeatureAD-Domain-Services -IncludeManagementTools
```
