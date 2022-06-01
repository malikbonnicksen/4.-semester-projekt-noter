# Host discovery teknikker
For at finde hosts kan man bruge forskellige teknikker. Da ikke alle hosts f.eks. svarer på ping pakker, kan man bruge nogle af disse teknikker til at finde ud af om der er en host på en given adresse.
[[TCP]] for 3-way handshake.

## Default nmap scan
Angiver man ikke nogen scan-teknik, så bruger nmap en scan tilsvarende:
*nmap -PE -PS443 -PA80 -PP*
Det svarer til en ICMP echo requests, TCP SYN, TCP ACK og en ICMP timestamp.
Sidder nmap og scanner på samme lokalnet, så bruges ARP scan per default.

## TCP-SYN Ping
*nmap -PS22-25,80,113,180,2045,56421 192.168.0.6*
SYN er den første pakke der sendes og bruges til at initiere en TCP-forbindelse mellem 2 hosts. Default destination er port 80.
Hvis porten er lukket vil host'en svare med en RST (reset) pakke.
Hvis porten er åben vil host'en svare med en SYN/ACK som er 2. trin i 3-way handshake.

## TCP-ACK Ping
*nmap -PA 192.168.0.6*
Tager flere porte på samme måde som SYN-ping.
ACK er afslutningen af TCP 3-way handshake og hvis der ikke har været de 2 tidligere trin i handshaket, så vil modtageren svare med RST og dermed vise at den eksisterer.
Porte angives ligesom ved TCP-SYN Ping.

En grund til at bruge denne form for scan er for at omgås firewalls

# UDP Ping
*nmap -PU 192.168.0.6*
Tager flere porte på samme måde som SYN og ACK ping. Default port er 40125.
Denne port er brugt som default fordi lige netop ved UDP ping scan er det bedst at gå efter potentielt lukkede porte.
Pakken vil oftest være tom, men for nogle porte vil der være protokol-specifik payload som er mere sandsynligt at få et svar.
Ved at ramme en lukket port vil host'en svare med en ICMP port unreachable pakke. Dette viser at der er en maskine på IP-adressen.
TTL overskredet, host/network unreachable fortæller nmap at host'en enten er nede eller ikke kan nås.
UDP ping er god til når firewalls kun tjekker TCP-forbindelser.

## ICMP ping typer
-PE, -PP og -PM
*nmap -PM 192.168.0.6*
nmap sender per default en ICMP echo request *-PE* (type 8) og forventer en echo reply (type 0) retur. Mange firewalls blokerer nu disse pakker i stedet for at svare som [RFC'en](https://www.rfc-editor.org/rfc/rfc1122.txt) angiver.
nmap understøtter også timestamp request *-PP* (type 13), information request (type 15) og address mask request *-PM* (type 17).
En timestamp reply (type 14) eller address mask reply (type 18) fortæller at en host er oppe. Kan bruges når en admin glemmer at andre en echo request kan bruges.


## IP protocol ping
*nmap -PO 192.168.0.6*
En liste af IP protokoller kan ses her: [IP-protokoller](https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml)
En liste af protokoller angives på samme måde som porte.
Default protokoller er ICMP, IGMP og IP-in-IP.
ICMP, IGMP, TCP og UDP pakker sendes med rigtige protocol headers, andre protokoller sendes uden ekstra data udover IP headeren.

## ARP Scan
*nmap -PR 192.168.0.0/24*
Sender man såkaldte raw IP ping-pakker på et lokalt netværk, så skal modtageren først til at finde ud af hvad afsenderens MAC-adresse er. Og jo flere hosts der er på et netværk jo længere tid kommer sådan en scan til at tage. Ca. 2 sekunder per host. Skal man scanne et stort netværk giver det ret meget ventetid.
Et andet problem med dette er at ARP-tabeller har en begrænset størrelse. Når nmap så har fyldt ARP-tabellen skal den vente et par minutter på at tabellen bliver tømt før den kan fortsætte med host discovery.
ARP scan giver nmap kontrollen over dette og bypasser dermed systemets ARP cache. Man skærer dermed over en tiende-del af tilsvarende scan med IP.
ARP scan er standard scan hvis nmap kan se, at man scanner fra samme netværk.

Nedenstående tabel viser de mest effektive ping probes:
![[Pasted image 20220529194229.png]]

Bedste probe kombinationer:
![[Pasted image 20220529194308.png]]

## Ekstra informationer
Mange dårligt opstillede firewalls har kun default-deny på porte under port 1024 og går man efter en port i den højere ende kan man i de tilfælde have nemmere ved at finde hosts.
*--source-port 53* kan være god at tilføje til sin scan.