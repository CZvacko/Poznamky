### V [IPv6](https://en.wikipedia.org/wiki/IPv6) je více adresních rozsahů (Scopes) ve kterém se může dané zařízení (host) nacházet 

2000::/3	Global Unique Address / GUA  (Internet) 
 > - Začínají na 2xxx  

fc00::/7	Unique Local Address  / [ULA](https://en.wikipedia.org/wiki/Unique_local_address) (v LAN za internetovou bránou, routovatelné pouze v privátních sítích)  
 > - Lze dělit na fd00::/8 a fc00::/8 (tento se ale v praxi nepoužívá)  
 > - Když se použije NAT, tak je lze routovat do internetu

fe80::/10	Link Local Address / [LLA](https://en.wikipedia.org/wiki/Link-local_address) (v daném síťovém segmentu, neroutovatelné)  
::1/128		Loopback Address (localhost)  
  
Zařízení může mít několik IPv6 adres z různých Scopes (očekává se že ve všech), dokonce i na stejném interface (síťovce).  
  

### Délka GUA prefixu (prefix lenght) který dostanu od ISP
/64 - pro malé sítě, typicky domácnosti s jednou sítí  
/56 - pro větší sítě (firmy), lze mít 256 podsítí.   
 > Taky lze rozdělit do /60s čímž získám 16 podsítí (např pro více samostatných routerů) kde každá bude mít 16 podsítí o délce /64 
  

### Metody přiřazení globálních IPv6 Adres
Static  
DHCPv6-PD  
DHCPv6 PD over PPPoE  

  
### Metody přiřazení lokálních IPv6 Adres
Static - Fixní Adresy  
[SLAAC](https://en.wikipedia.org/wiki/IPv6#Stateless_address_autoconfiguration_(SLAAC)) - Stateless Address Auto-Configuration (Adresa je generovaná hostem)  
 > Vyžaduje /64 adresní blok  
 
[DHCPv6](https://en.wikipedia.org/wiki/DHCPv6) - Dynamic Host Configuration Protocol (Adresa je přiřazená DHCP serverem)  
 > Toto nepodporují Chrome/Android zařízení  
  

You can configure the router advertisements to provide either global or ULA addresses. 
