# SSL/TLS
![[Pasted image 20220613160953.png]]
Under TLS handshake sker der flg.:  
TLS version aftales.  
Hvilken cipher suite der bruges.  
Serverens authenticity verificeres vha. serverens public key og certificate authority’ens digitale signatur.  
Sessionsnøgler aftales til brug af symmetrisk kryptering efter handshake

  
TLS trin:  
1. Client hello msg, bliver sendt af klienten, indeholder understøttede TLS versioner, cipher suites og en string af random bytes (”client random”).  
2. Server hello msg, er svar på client hello msg, indeholder serverens TLS certifikat, serverens valgte cipher suite og en string af random bytes (”server random”)  
3. Authentication trinnet, her verificerer klienten serverens cert hos den CA der har udskrevet det. Så ved klienten at serveren er den, den siger den er og at klienten har at gøre med den faktiske ejer af domænet.  
4. Premaster secret, klienten sender endnu en random string af bytes (premaster secret), som bliver krypteret med serverens public key, som klienten har fået gennem serverens cert. Kun serveren kan dekryptere pakker sendt med dens public key.  
5. Serveren dekrypterer premaster secret.  
6. Sessionsnøgler bliver lavet ud fra client- og server-random og premaster secret. Både klient og server skulle gerne nå frem til det samme.  
7. Klienten sender en ”finished” besked til serveren som er krypteret med sessionsnøglen.  
8. Serveren sender en ”finished” besked til klienten som er krypteret med sessionsnøglen.  
9. Handshake er færdig og fremtidige pakker sendes krypteret med sessionsnøglen.

CIA (confidentiality, integrity og availability) opnås på flg. måder:  
Confidentiality sikres ved en kombination af symmetrisk og asymmetrisk kryptering, først bruges asymmetrisk kryptering til at dele en _shared secret key_.