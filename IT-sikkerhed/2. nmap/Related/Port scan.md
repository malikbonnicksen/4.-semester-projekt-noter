# Port scan
nmap skelner mellem 6 forskellige port-tilstande:

**open**
En host accepterer TCP eller UDP forbindelser på denne port. Hver åben port er en potentiel angrebsvektor. Desuden viser de også de slags services der er tilgængelig på netværket.
En åben port kan dog stadig være beskyttet af en TCP-wrapper (tcpd) eller applikationen bag porten er sat til kun at servicere bestemte IP-adresser. Det er stadig potentielle angrebsvektorer.

**closed**
Lukkede porte modtager og svarer på nmap probes, men der er ikke nødvendigvis en applikation der lytter bag porten. Kan bruges til at vise at en host er online og at den bruger en IP adresse og ikke mindst som en del af OS detection.
Det kan være en god idé at scanne lukkede porte igen på et senere tidspunkt i tilfælde af den er blevet åbnet.

**filtered**
Nmap kan ikke sige om porten er åben, da pakken enten er blevet droppet af en firewall, router pga. regler eller host-based firewall. Nmap prøver at sende en probe af flere omgange i tilfælde af, at pakken blev droppet pga. network congestion og ikke blev filtreret. Dette resulterer i meget langsommere scan.

**unfiltered**
Porten kan nåes, men Nmap kan ikke fortælle om porten er åben eller lukket. ACK scan er den eneste form for scan der klassificerer en port som *unfiltered*. Window scan, SYN scan eller FIN scan kan i disse tilfælde bruges til at finde ud af om en port er åben.

**open|filtered**
Når Nmap ikke kan finde ud af om en port er åben eller pakken bliver filtreret klassificeres en port som open|filtered.
UDP, IP protocol, FIN, NULL og Xmas scans klassificerer porte på denne måde.

**closed|filtered**
Når Nmap ikke kan finde ud af om en port er lukket eller filtreret klassificeres porten sådan. Bruges kun ved IP ID Idle scan (-sI)

## Nmap fortolkninger ift. bestemte teknikker
### -sS/-sT
TCP SYN/ACK svar:                                                                 open
TCP RST svar:                                                                          closed
Ingen svar, selv efter retransmission:                                    filtered
ICMP unreachable (type 3, kode 1,2,3,9,10 eller 13):            filtered

### -sN/-sF/-sX
Ingen svar, selv efter retransmission:                                    open|filtered
TCP RST pakke:                                                                       closed
ICMP unreachable (type 3, kode 1,2,3,9,10 eller 13):            filtered

### -sU
Ethvert UDP svar fra en port (er ualmindeligt):                     open
Ingen svar, selv efter retransmission:                                    open|filtered
ICMP port unreachable (type 3, kode 3):                              closed
ICMP unreachable (type 3, kode 1,2,9, 10 eller 13):              filtered

### -sA
TCP RST svar:                                                                         unfiltered
Ingen svar modtaget, selv efter retransmission:                  filtered
ICMP unreachable (type 3, kode 1,2,3,9,10 eller 13):            filtered

### -sW
TCP RST svar med non-zero window field:                          open
TCP RST svar med zero window field:                                  closed
Ingen svar, selv efter retransmission:                                   filtered
ICMP unreachable (type 3, kode 1,2,3,9,10 eller 13):           filtered

### -sM
Ingen svar, selv efter retransmission:                                  open|filtered
TCP RST svar:                                                                        closed
ICMP unreachable (type 3, kode 1,2,3,9,10 eller 13):          filtered

### -sO
Ethvert svar i hvilken som helst protokol fra host:              open
ICMP protocol unreachable (type 3, kode 2):                     closed
Andre ICMP unreachable (type 3, kode 1,3,8,10 eller 13):  filtered
Ingen svar, selv efter retransmission:                                  open|filtered
