### Formát adresy  
[IPv6](https://en.wikipedia.org/wiki/IPv6) adresa má 128 bitů a je zobrazena jako osm skupin čtyř hexadecimálních číslic oddělených dvojtečkami (tj. šestnáctková soustava). Prvních 64 bitů adresy je **Síťová část** která se využívá pro směrování síťového provozu. Zbývajících 64 bitů je **Hostitelská část** sloužících k identifikaci konkrétního rozhraní v síti.  

Zápis lze zkrátit tak, že lze v jednotlivých čtveřicích vynechávat počáteční nuly. Pokud se vyskytne několik po sobě jdoucích nulových skupin, lze je nahradit dvojicí dvojteček. Ta se však v zápisu každé adresy smí objevit jen jednou, aby byl jednoznačný. Např:  
2a02:0000:0000:0000:0000:0000:0000:0101  
2a02:0:0:0:0:0:0:101  
2a02::101  


### V IPv6 je více adresních rozsahů (Scopes) ve kterém se může dané zařízení nacházet 

**2000::/3**	Global Unique Address / [GUA](https://www.geeksforgeeks.org/global-unicast-address-in-ccna/) (Internet)  

&nbsp;&nbsp;&nbsp;&nbsp;Adresy začínají na 2xxx a skládají se z těchto částí, např:  
&nbsp;&nbsp;&nbsp;&nbsp; **2001:0db8:abcd:** 0000: **a111:b222:c333:d444**  
&nbsp;&nbsp;&nbsp;&nbsp; **GlobalPrefix** + SubnetID + **Interface ID**

**fc00::/7**	Unique Local Address  / [ULA](https://en.wikipedia.org/wiki/Unique_local_address) (v LAN za internetovou bránou, routovatelné pouze v privátních sítích)  

&nbsp;&nbsp;&nbsp;&nbsp;Lze dělit na fd00::/8 a fc00::/8 (tento se ale v praxi nepoužívá)  
&nbsp;&nbsp;&nbsp;&nbsp;Když se použije NAT, tak je lze routovat do internetu

**fe80::/10**	Link Local Address / [LLA](https://en.wikipedia.org/wiki/Link-local_address) (v daném síťovém segmentu, neroutovatelné)  

&nbsp;&nbsp;&nbsp;&nbsp;Unicast adresy začínají na fe80 a skládají se z těchto částí, např:  
&nbsp;&nbsp;&nbsp;&nbsp; **fe80** &nbsp; :: &nbsp; **9124:9085:90f6:6411** *%5*  
&nbsp;&nbsp;&nbsp;&nbsp; **GlobalPrefix** + SubnetID(nuly) + **Interface ID** + *Zone index*  
&nbsp;&nbsp;&nbsp;&nbsp; *Zone index* označuje danou síťovku, aby OS věděl kam posílat packety.  
&nbsp;&nbsp;&nbsp;&nbsp; Jeho formát se ale může lišit dle OS, ukázka výše platí pro Windows.  

 > :bulb: Každé zařízení si ji vytvoří samo a to i v případě, že ipv6 není v síti nijak konfigurované  

**::1/128**		Loopback Address (localhost)  

  
Zařízení může mít vícero IPv6 adres z různých Scopes, dokonce i několik adres v daném scope na stejném interface (síťovce).  
Běžný windows klient by měl mít GUA nebo ULA a pak vždy LLA + localhost.  

### Délka GUA prefixu (prefix lenght) který "vetšinou" dostanu od ISP
/64 - pro malé sítě, typicky domácnosti s jednou sítí - nejhorší varianta  
/60 - slušný ISP, lze mít 16 podsítí délky /64  
/56 - pro větší sítě (firmy), lze mít 256 podsítí délky /64  
/48 - velmi štedrý ISP  

U firemních linek lze dostat i prefix délky /53 nebo i jiné, záleží na daném ISP.

 > :bulb: Přidělené prefixy lze [rozdělit](https://subnettingpractice.com/ipv6-subnet-calculator.html) např. /56 do /60 čímž získám 16 podsítí (pro více routerů) kde každý může mít 16 podsítí o délce /64  
  
### Metody přiřazení IPv6 Adres
Static - Fixní Adresy  
[SLAAC](https://en.wikipedia.org/wiki/IPv6#Stateless_address_autoconfiguration_(SLAAC)) - Stateless Address Auto-Configuration (Adresa je generovaná hostem)  
&nbsp;&nbsp;&nbsp;&nbsp;Kroky:  
&nbsp;&nbsp;&nbsp;&nbsp;Zařízení vygeneruje Link Local adresu - dříve dle MAC ale od toho se upouští  
&nbsp;&nbsp;&nbsp;&nbsp;Zařízení přes protokol ICMPv6 odešle Router Solicitation (RS)     
&nbsp;&nbsp;&nbsp;&nbsp;Router odpoví Router Advertisement (RA) obsahující informaci o síťovém prefixu (jak GUA tak i ULA)  
&nbsp;&nbsp;&nbsp;&nbsp;Zařízení zkombinuje tento prefix s indentifikátorem jeho interface a získá tak plnou IPv6 adresu.  

 > Vyžaduje /64 adresní blok  
 
[DHCPv6](https://en.wikipedia.org/wiki/DHCPv6) - Dynamic Host Configuration Protocol (Adresa je přiřazená DHCP serverem) 
 - Stateful DHCPv6: DHCP server svým klientům přiřadí IPv6 adresu, ~~bránu~~ ale i ostatní info jako: dns, ntp, netboot.
 - Stateless DHCPv6: Klienti si pomocí SLAAC sami získají IPv6 adresu, ~~bránu~~ ale ostatní jim dopošle DHCP server. Toto ale musí být oznámeno v rámci RA.

 > :bulb: Bránu DHCPv6 nesděluje, to dělá router sám v rámci funkce Router Advertisement 

 > :warning:Toto nepodporují Chrome/Android zařízení

 > :warning:Pozor při pokusech s routerem a použitím windows 11 klienta, ten když dostane IP přes SLAAC a pak přepnete Router Advertisement mode, tak může DHCP ignorovat, pomůže restart.  
 
Pomocí funkce Prefix delegation / [DHCPv6-PD](https://en.wikipedia.org/wiki/Prefix_delegation) umí ISP router předat informaci o síťovém prefixu do routeru zákazníka, který jej pak přidělí zařízením ve své síti (buď přes SLAAC a nebo DHCPv6).


### Testování
[www.nebezi.cz](http://www.nebezi.cz) je server, který je dostupný pouze po IPv6  
[ipv6-test.com](http://test-ipv6.com) další testy IPv6 konektivity, umí i opingovat zařízení zpět a ověřit tak funkci firewalu (přes IPv4 only někdy blbne)    

### IPv6 adresy veřejných DNS serverů
[cloudflare](https://developers.cloudflare.com/1.1.1.1/ip-addresses/) - mají i varianty které umí blokovat malware   
[quad9](https://www.quad9.net/service/service-addresses-and-features) - mají i varianty které umí blokovat malware   
[opendns](https://support.opendns.com/hc/en-us/articles/227986667-Does-OpenDNS-Support-IPv6)  

### Odlišnosti oproti IPv4
NAT už není důvod používat, kromě sítí kde router využívá Multi-WAN, je zde více variant:  
&nbsp;&nbsp;&nbsp;&nbsp; [NPTv6](https://en.wikipedia.org/wiki/IPv6-to-IPv6_Network_Prefix_Translation)  Obdoba IPv4 1:1 NAT, [překládá](https://docs.netgate.com/pfsense/en/latest/nat/npt.html) prefix na jiný.  
&nbsp;&nbsp;&nbsp;&nbsp; [NAT66](https://blog.apnic.net/2018/02/02/nat66-good-bad-ugly/)   
ARP v IPv6 nahrazuje [Neighbor Discovery Protocol (NDP)](https://cs.wikipedia.org/wiki/Neighbor_Discovery_Protocol)  
&nbsp;&nbsp;&nbsp;&nbsp; Ve windows zle zobrazit seznam pomocí *netsh interface ipv6 show neighbors* nebo [Get-NetNeighbour](https://learn.microsoft.com/en-us/powershell/module/nettcpip/get-netneighbor?view=windowsserver2025-ps)  
&nbsp;&nbsp;&nbsp;&nbsp; Pokud je na routeru správně nakonfigurované RA, tak na začátku seznamu bude vypsán (Router) a může mít 2 adresy.  
&nbsp;&nbsp;&nbsp;&nbsp; Pokud zrovna probíhala komunikace do internetu (např. ping) pak State má být [Reachable](https://www.rfc-editor.org/rfc/rfc4861.html#section-7.3.2), jestli je *Stale* nebo jiné, tak to znamená problém.  
