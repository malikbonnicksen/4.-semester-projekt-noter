# ARP poisoning
Det er når en angriber lykkes med at overtage et mål’s ARP opslag i ARP tabellen. Når angriberen lykkes med ARP spoofingen, så bliver målets IP adresse og angriberens MAC adresse en entry i ARP tabellen. Med andre ord erstattes målets entry’s MAC adresse med angriberens MAC adresse. Dermed kan angriberen opsnappe, modificere eller helt blokere pakker designet til målets enhed. Det er muligt fordi ARP beskeder bliver gemt i ARP tabellen uden at authenticate afsenderen. Både routere og endpoints kan snydes til at modtage ARP beskeder og gemme dens indhold i ARP tabellen.

#### Beskyttelse mod ARP spoofing/poisoning:  
LAN switches med 1 host per port.
Port security kan begrænse source MAC adresserne.
802.1x (port based network access control) port authentication.
Monitorering af LAN switch address tables.
Monitorering af ARP router tables.
