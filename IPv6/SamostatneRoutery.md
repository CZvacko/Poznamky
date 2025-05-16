V IPv4 jste mohli mít internetovou linku s více veřejnými adresami. Pak bylo možné dát si na ni více samostatných routerů (aniž by o sobě věděli), každý plnil jinou funkci. Jeden třeba pro svou firemní síť, další třeba pro externí firmu (kantýnu).  
  
V takových routerech se obvykle dělá NAT do vnitřní sítě. Pak když:
- klient 2 odeslal nějaký paket do internetu  
- ten prošel routerem B který udělal NAT - paket tedy odešel s WAN adresou routeru (20.30.40.3)  
- ten doputoval k danému internetovému serveru
- ten se pak v rámci routingu vrátil k danému ISP
- ISP router jej poslal na adresu routeru B, protože je napřímo v jeho podsíti (má záznam v ARP tabulce)  
- router B se pak podívá do své [NAT tabulky](https://www.firewall.cx/networking/network-address-translation/nat-table.html) a vrátí paket klientovi 2
- klient 2 obdržel odpověď

V IPv6 (témeř) vždy dostanete větší rozsah s mnoha veřejnými adresami. Pokud chcete stávající IPv4 infrastrukturu zachovat jak je, nastane problém protože v IPv6 se většinou nedělá NAT (ale může), pak tedy:  
- klient 2 odeslal nějaký paket do internetu  
- ten prošel routerem B který NEudělal NAT - packet tedy odešel s adresou klienta 2 (2001:db8:abcd:1280::1000)  
- ten doputoval k danému internetovému serveru  
- ten se pak v rámci routingu vrátil k danému ISP  
- ISP má ale standardně nastaven routing jen na jeden zákaznický router A, takže tam vrátí každý paket  
- router A ale nemá ve své routovací tabulce takovou adresu (ani NDP tabulka mu nepomůže - to je obdoba ARP v IPv4) takže paket zahodí  
- klient 2 NEDOSTAL odpověď  
![ping selže](/IPv6/Obrazky/TwoIndependentRouters.jpg)
  
To lze vyřešit několika způsoby:  
- před routery A + B dáte další router, který zajistí správné směřování daných adresních rozsahů (to vám ale modifikuje IPv4 infrastrukturu)
- mezi routery A + B přidáte další síťový interface, nastavíte routing a pak router A předá nastavený adresní rozsah routeru B (to vám ale modifikuje IPv4 infrastrukturu)
- v routeru B nastavíte NAT (to by se v IPv6 moc nemělo) a klientům přiřadíte ULA adresy  
- požádáte ISP aby změnil IPv6 routing na svém routeru, musíte si jen domluvit do jaké WAN IP budou jaké adresy směrovány  

