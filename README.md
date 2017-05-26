# VNX-Toolkit
Random Scripts for EMC VNX PowerShell


## VNX-Snaps.PS1
Requires - EMC Storage Integrator Powershell (ESIPSToolkit) Version 5.0.1.3

### Example

    $connectionStringPri = @{
        "Username"="admin";
        "Password"="password";
        "SpaIpAddress"="192.168.50.1";
        "SpbIpAddress"="192.168.50.2";
        "Port"="443";
        "UserFriendlyName"="Primary SAN"
    };

    $connectionStringSec = @{
        "Username"="admin";
        "Password"="password";
        "SpaIpAddress"="192.168.51.1";
        "SpbIpAddress"="192.168.51.2";
        "Port"="443";
        "UserFriendlyName"="Secondary SAN"
    };

    [Array]$sanArray = (
        $connectionStringPri, 
        $connectionStringSec
    )

    [Array]$targetLuns = (
        "LUN1",
        "LUN2",
        "LUN3"
    )

    . .\VNX-Snaps.PS1 -expireDays 3 -targetLuns $targetLuns -sanArray $sanArray
