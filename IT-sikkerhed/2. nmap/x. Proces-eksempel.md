# Proces-eksempel

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

#### Host discovery



#### Port scan
