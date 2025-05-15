### Windows klient s GUA adresou
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
### Windows klient s vícero GUA adres (výchozí nastavení v OpenWrt)  
První GUA přiřadí OpenWrt v rámci DHCPv6 metody, další v rámci SLAAC metody a "Temporary" si vygeneruje OS dle jeho aktuálního nastavení (viz popis níže).  
```console
Ethernet adapter Ethernet:  

    Connection-specific DNS Suffix  . : MyNet  
    Description . . . . . . . . . . . : Realtek(R) PCI(e) Ethernet Controller  
    Physical Address. . . . . . . . . : 40-16-7E-A9-97-CA  
    DHCP Enabled. . . . . . . . . . . : Yes  
    Autoconfiguration Enabled . . . . : Yes  
GUA>IPv6 Address. . . . . . . . . . . : 2a02:570:90f:181::eb7(Preferred)
    Lease Obtained. . . . . . . . . . : 03 March 2025 10:45:06  
    Lease Expires . . . . . . . . . . : 03 March 2025 12:45:06  
GUA>IPv6 Address. . . . . . . . . . . : 2a02:570:90f:181:e253:a522:fa76:d5bf(Preferred)
GUA>Temporary IPv6 Address. . . . . . : 2a02:570:90f:181:5da0:4215:467d:672d(Preferred)
LLA>Link-local IPv6 Address . . . . . : fe80::9124:9085:90f6:6411%5(Preferred)
    IPv4 Address. . . . . . . . . . . : 10.90.1.11(Preferred)  
    Subnet Mask . . . . . . . . . . . : 255.255.255.0  
    Lease Obtained. . . . . . . . . . : 03 March 2025 10:45:05  
    Lease Expires . . . . . . . . . . : 03 March 2025 12:45:05  
    Default Gateway . . . . . . . . . : fe80::f6ec:38ff:fef3:72f2%5 
                                        10.90.1.1  
    DHCP Server . . . . . . . . . . . : 10.90.1.1  
    DHCPv6 IAID . . . . . . . . . . . : 88086142  
    DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-2B-C8-8B-9F-40-16-7E-A9-97-CA  
    DNS Servers . . . . . . . . . . . : 2a02:570:90f:181::1
                                        10.90.1.1  
    NetBIOS over Tcpip. . . . . . . . : Enabled  
```
### Windows klient s ULA adresou
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

### Dočasná GUA adresa  
Ve windows je funkce která k trvalé GUA adrese generuje i dočasnou GUA, která má sloužit jako ochrana soukromí uživatele. Taková adresa má životnost standadně 7 dní, pak se vygeneruje nová (pak nelze uživatele na webu sledovat dle jeho adresy). Ta se označuje jako "Temporary IPv6 Address" a měla by se používat jen pro odchozí spojení. 
Toto bývá standardně zapnuto a stav lze ověřit pomocí příkazu *netsh interface ipv6 show privacy* nebo *get-netipv6protocol*
```console
Querying active state...  
  
Temporary Address Parameters  
---------------------------------------------  
Use Temporary Addresses             : enabled  
Duplicate Address Detection Attempts: 3  
Maximum Valid Lifetime              : 7d  
Maximum Preferred Lifetime          : 7d  
Regenerate Time                     : 5s  
Maximum Random Time                 : 10m  
Random Time                         : 4m11s  
```
Lze měnit dané hodnoty a nebo toto úplně vypnout:  
*netsh interface ipv6 set privacy state=disabled store=active*  
*netsh interface ipv6 set privacy state=disabled store=persistent*  

Nebo pomocí příkazu *Set-NetIPv6Protocol -UseTemporaryAddresses Enabled*  
Zároveň by se mělo vypnout toto:  

### Způsob generování GUA adresy ve SLAAC metodě  
Dříve se hostitelská část GUA adresy (Interface ID) generovalo dle MAC adresy síťovky [EUI-64 metoda](https://www.geeksforgeeks.org/ipv6-eui-64-extended-unique-identifier/), to ovšem taky mohlo přispět k identifikaci uživatele. Zavedl se tedy Random Interface Identifier, toto lze v případě vypnout:  
*netsh interface ipv6 set global randomizeidentifiers=disabled store=active*  
*netsh interface ipv6 set global randomizeidentifiers=disabled store=persistent*  
  
Nebo pomocí příkazu *Set-NetIPv6Protocol -RandomizeIdentifiers Disabled*  
