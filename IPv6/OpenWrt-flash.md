Z dd-wrt na OpenWrt lze udělat flash přes GUI nebo v případě potíží přes konzoli:  
  
V dd-wrt v záložce services povolit službu SSHh  
Přes scp protokol (winscp) do routeru upload firmware openwrt-your-router-FACTORY.bin (factory ne upgrade) do složky /tmp  
Připojím se přes SSH, příkazy:  
cd /tmp  
mtd -f write openwrt-your-router-factory.bin linux  
reboot  
