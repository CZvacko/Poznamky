### Windows klient s GUA adresou (dual stack včetně IPv4)  
```console
Ethernet adapter Ethernet:  

    Connection-specific DNS Suffix  . : MyNet  
    Description . . . . . . . . . . . : Realtek(R) PCI(e) Ethernet Controller  
    Physical Address. . . . . . . . . : 40-16-7E-A9-97-CA  
    DHCP Enabled. . . . . . . . . . . : Yes  
    Autoconfiguration Enabled . . . . : Yes  
GUA>IPv6 Address. . . . . . . . . . . : 2a02:1070:100f:2100::5000(Preferred)  
    Lease Obtained. . . . . . . . . . : 03 March 2025 10:45:06  
    Lease Expires . . . . . . . . . . : 03 March 2025 12:45:06  
LLA>Link-local IPv6 Address . . . . . : fe80::9124:9085:90f6:6411%5(Preferred)  
    IPv4 Address. . . . . . . . . . . : 10.90.1.11(Preferred)  
    Subnet Mask . . . . . . . . . . . : 255.255.255.0  
    Lease Obtained. . . . . . . . . . : 03 March 2025 10:45:05  
    Lease Expires . . . . . . . . . . : 03 March 2025 12:45:05  
    Default Gateway . . . . . . . . . : fe80::f6ec:38ff:fe80:e074%5  
                                        10.90.1.1  
    DHCP Server . . . . . . . . . . . : 10.90.1.1  
    DHCPv6 IAID . . . . . . . . . . . : 88086142  
    DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-2B-C8-8B-9F-40-16-7E-A9-97-CA  
    DNS Servers . . . . . . . . . . . : 2a02:1070:100f:2100::1  
                                        10.90.1.1  
    NetBIOS over Tcpip. . . . . . . . : Enabled  
```
### Windows klient s ULA adresou (dual stack včetně IPv4)  
```console
Ethernet adapter Ethernet:  

    Connection-specific DNS Suffix  . : MyNet2  
    Description . . . . . . . . . . . : Realtek(R) PCI(e) Ethernet Controller  
    Physical Address. . . . . . . . . : 40-16-7E-A9-97-CA  
    DHCP Enabled. . . . . . . . . . . : Yes  
    Autoconfiguration Enabled . . . . : Yes  
ULA>IPv6 Address. . . . . . . . . . . : fd01:8070:10ad:ab77:5002(Preferred)  
    Lease Obtained. . . . . . . . . . : 03 March 2025 10:40:17  
    Lease Expires . . . . . . . . . . : 03 March 2025 12:40:18  
LLA>Link-local IPv6 Address . . . . . : fe80::9124:9085:90f6:6411%5(Preferred)  
    IPv4 Address. . . . . . . . . . . : 10.90.2.20(Preferred)  
    Subnet Mask . . . . . . . . . . . : 255.255.255.0  
    Lease Obtained. . . . . . . . . . : 03 March 2025 10:40:16  
    Lease Expires . . . . . . . . . . : 03 March 2025 12:40:16  
    Default Gateway . . . . . . . . . : fe80::213:3bff:fe2f:3a4b%5  
                                        10.90.2.1  
    DHCP Server . . . . . . . . . . . : 10.90.2.1  
    DHCPv6 IAID . . . . . . . . . . . : 88086142  
    DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-2B-C8-8B-9F-40-16-7E-A9-97-CA  
    DNS Servers . . . . . . . . . . . : fd01:8070:10ad:ab77::1  
                                        10.90.2.1  
    NetBIOS over Tcpip. . . . . . . . : Enabled  
```  
:bulb: Localhost adresa se standardně neukazuje, lze ji zobrazit přes příkaz **route print**  
