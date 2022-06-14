# Proces-eksempel
#### Script pre-scanning
Scripts der køres her køres kun 1 gang og ikke per host-machine man prøver at scanne.

#### Target enumeration
Når man starter med at skulle finde en organisations netværksblokke kan det være en god idé at starte med at finde offentligt registrerede servere. Hvert skridt efterfølges af mitigering.

[[1.1 Linux host]] viser hvordan man starter med at sondere terrænet via offentligt tilgængelige DNS opslag.
Mitigering: Kan ikke rigtig mitigeres, det drejer sig om offentligt tilgængelige informationer som er nødvendige.

[[1.2 Linux dig]] kan bruges til at lave en zone-transfer, såfremt DNS-serveren tillader dette.
Mitigering: Sæt DNS til kun at acceptere *dig* requests fra trustede IP-adresser.

Man skal dog være opmærksom på at det ikke er sikkert at alle systemer fundet på denne måde er under organisationens kontrol. De kan have udliciteret det til f.eks. Amazon eller en anden tredjepart.
For at undgå, at man scanner noget man ikke bør kan man gøre brug af nmap's *traceroute* funktion:

*nmap -Pn T4 --traceroute www.example.com

Alternativt kan man bruge Linux' whois funktion:

*whois IP*

Tilhører IP'en ikke organisationen, skal man nok undlade at scanne den.

#### Host discovery (ping scanning)
[[Host discovery teknikker]] viser de forskellige teknikker Nmap kan bruge. De kan bruges på kryds og tværs, f.eks. kan man både scanne efter åbne TCP og UDP porte på samme tid.
Hvis en almindelig scan ikke kan finde nogle hosts kan det være netværksadministratoren har slået svar fra på hosts og enheder. I sådan et tilfælde vil ARP scan være en god mulighed. Den virker selvfølgelig kun på lokalnetværket.
Det kan også være nødvendigt at sende fra en specifik port, f.eks. port 53. Det får det til at se ud som om pakken kommer fra en DNS server.
For at skippe dette trin kan man tilføje *-Pn* til sin scan. For at stoppe efter host discovery kan man tilføje *-sn -n*.


#### Reverse-DNS resolution
Under denne fase forsøger Nmap at finde navne til de hosts man har fundet. Navnet kan være med til at afsløre hvilken service eller hvilken maskine man har fundet.
Kan skippes med *-n* eller udvides med *-R*.

#### Port scan
Hvis man skipper denne fase med *-sn* kan man stadig bede Nmap om at køre nogle af de funktioner som *-sn* skipper. F.eks. med *--traceroute* eller køre et specifikt script med 
*--script*.
Det er under denne fase, at Nmap finder ud af hvilke porte der er åbne, lukkede eller filtrerede.

#### Version detection
Hvis der er porte der er åbne kan Nmap ofte finde ud af hvilken tjeneste der kører bag en port. Det enables med *-sV*.

#### OS detection
*-O* bruges til at finde styresystemet på de systemer man scanner.

#### Traceroute
*--traceroute*, Nmap kører som regel en ekstra reverse DNS lookup for hvert system der er mellem målet og Nmap-maskinen.

#### Script scanning
Kræver *-sC* eller *--script* flagene.
NSE (Nmap Scripting Engine) bruger Lua sproget og her er bliver hver host som regel scannet flere gange med scripts'ne. Scipts kan f.eks. finde service vulnerabilities, finde malware, samle mere information fra databaser og andre netværkstjenester.

#### Output
Det er her Nmap enten printer resultatet til skærmen eller, hvis man har angivet det, skriver det til en fil.
Scanner man store netværk, kan Nmap køre hver fase flere gange og skrive resultaterne ud til forskellige filer.

#### Script post-scanning
Scripts i denne fase er som regel scripts der behandler den data man har samlet og laver statistisk analyse på det. Der er ingen Nmap scripts i denne fase, så man skal selv skrive sine egne scripts.