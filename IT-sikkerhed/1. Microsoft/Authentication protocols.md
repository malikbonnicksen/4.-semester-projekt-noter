## NTLM
![[Pasted image 20220613135358.png]]
NTLM giver ikke data integritet eller data confidentiality, dvs. data er ikke sikret at være pålideligt eller troværdigt i dens livscyklus (integrity) og manglende confidentiality betyder at dataene ikke bliver krypteret.

## LDAP/LDAPS
![[Pasted image 20220613135438.png]]
Lightweight Directory Access Protocol.
LDAPS er mere sikkert, da credentials ikke sende i plain text over netværket.

## Kerberos
![[Pasted image 20220613135729.png]]
KERBEROS bruger en symmetric key kryptografisk protokol og kræver en trusted 3rd-party til at authorize users.

## AD
AD indeholder en NTIDS.dit fil, der indeholder alle informationerne om AD’et og password hashes for domain users. Bliver per default gemt i %SystemRoot%\NTDS og er kun tilgængelig gennem domain controlleren.

Et ”forest” er skoven af domæner, forskellige ”træer” udgør de forskellige domæner inde i AD-netværket.  
Trees – et hierarki af domæner i ADDS (active directory domain services)  
Domains – brugt til at gruppere styre objekter i domænet  
Organizational units – containere for grupper, computere, brugere, printere og andre OU’er  
Trusts – Tillader brugere at tilgå resurser i andre domæner  
Objects – brugere, grupper, computere, printere, shares  
Domain services – DNS server, LLMNR (protokol baseret på DNS som tillader IPv4 og IPv6 hosts at lave name resolution for hosts på samme lokale netværk), IPv6  
Domain schema – regler for object creation

## AAD
Tjenester som Office 365, Dynamics 365 og Azure gør brug af AAD. AAD kan bruge SAML, OAUTH 2.0 og OpenID Connect som authentication metoder.  
SAML (security assertion markup language) er en slags SSO (Single sign-on) standard som definerer regler og protokoller som tillader brugere at tilgå web applikationer med et enkelt login. Deles op i service providers og identity providers, hvor service providers er de systemer og applikationer som brugere har adgang til og identity providers er de tjenester der foretager bruger authentication.  
OAUTH 2.0 har 4 vigtige regler:  
Der skal være en authorization server, som giver en access token.  
En resource owner der giver adgang til resurser vha. access token.  
En client, som er applikationen der requester en access token og giver den til ressource serveren.  
En resource server som tager imod access token og skal validere token’ens validitet.  
OpenID Connect er en authentication standard som bygger ovenpå OAUTH 2.0, den tilføjer en ekstra token (ID token). Bruger en JSON Web Token (JWT). OAUTH 2.0 omhandler resurse tilgang og deling, OIDC omhandler bruger authentication.

![[Pasted image 20220613141228.png]]