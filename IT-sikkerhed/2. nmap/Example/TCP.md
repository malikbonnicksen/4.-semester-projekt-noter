# TCP

![[Pasted image 20220529164937.png]]
![[Pasted image 20220529165425.png]]

TCP har flere flag som Nmap gør brug af:
**SYN** bruges til at starte en TCP forbindelse.
**ACK** bruges til: sammen med SYN i 2. trin i TCP 3-way handshake, afslutning af 3-Way handshake og ikke mindst som bekræftelse på at en pakke er modtaget efter handshaket.
**FIN** bruges til at lukke en forbindelse.
**RST** bruges til at aborte en forbindelse som svar på en fejl.
**PSH** bruges til at pushe data med det samme. Både når pakken bliver sendt, så bliver pakken sendt med det samme, og når modtageren får pakken og ser den har PSH bit set bliver pakken sendt op til den modtagende applikation med det samme.
**URG** bruges til at fortælle modtageren at noget af dataen i pakken er *urgent* og bør prioriteres. Urgent pointeren, 16 bits, angiver hvor meget af dataen fra først byte er vigtig. Telnet gjorde brug af den.

![[Pasted image 20220602130533.png]]
