Ve výchozím stavu má OpenWrt IPv6 funcionalitu aktivní.  
  
V Network-Interfaces je již wan6 interface, kde přes Edit lze přenastavit výchozí DHCPv6 client protokol.  
Už v tuto chvíli dokáže router komunikovat přes IPv6 (ověřím si přes Network-Diagnostics IPv6 Ping openwrt.org).  

Zbývá nastavit toto:  
> Doporučuje se vypnout užití IPv6 ULA adresy, Network-Interfaces-IPv6 ULA-Prefix - smažu dané pole
  
> Volitelně lze upravit IPv6 assignment lenght+hint uvnitř LAN interface

Proces nastavení lze vidět na videu [tady](https://youtu.be/LJPXz8eA3b8?feature=shared)
