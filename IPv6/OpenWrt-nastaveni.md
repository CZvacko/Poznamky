### Ve výchozím stavu má OpenWrt IPv6 funcionalitu aktivní.  
  
V Network-Interfaces již existuje wan6 interface, kde přes Edit lze přenastavit výchozí DHCPv6 client protokol.  
Už v tuto chvíli dokáže router komunikovat přes IPv6 (ověřím si přes Network-Diagnostics IPv6 Ping openwrt.org).  

Zbývá nastavit toto:  
> Doporučuje se vypnout užití IPv6 ULA adresy (jinak může mít win klient až 5 adres: 2xGUA a 3xULA) , Network-Interfaces-Global network options, IPv6 ULA-Prefix - smažu dané pole
  
> Uvnitř LAN interface upravit IPv6 assignment lenght podle toho jaký rozsah je k dispozici, popř jak byl rozsah rozdělen  

> Pokud je použito více LAN interface (např Guest), tak pro každý upravit IPv6 assignment hint  
  
> V LAN-advanced vypnout Use default gateway, naopak u WAN má být zapnuté  

Detailní proces nastavení lze vidět na videu [tady](https://youtu.be/LJPXz8eA3b8?feature=shared)  

### Statické IPv6   
Před OpenWrt mám jiný router, kde ale beží jen DHCPv6 ale bez PD, takže OpenWrt nedokáže automaticky předat dané adresy do LAN interface.  

Nastavím WAN Protokol na Static address  
![WAN protokol](/IPv6/Obrazky/OpenWrt-WAN-Protocol.jpg)  
A nastavím mu pevnou IP z LAN rozsahu nadřazeného routeru (ale mimo jeho DHCP pool range)  
![WAN](/IPv6/Obrazky/OpenWrt-WAN-Static.jpg)  
  
Dále nastavím LAN interface, jako první musím nastavit Advanced-IPv6 Assignment length na disabled  
![LAN assignment](/IPv6/Obrazky/OpenWrt-LAN-Assing.jpg)  
Až poté se objeví kolonky pro zapsání IPv6 adresy  
![LAN](/IPv6/Obrazky/OpenWrt-LAN-Static.jpg)  
