# Scanning eksempler m. forklaring
*nmap -sp 192.168.0.0/24*
Ping scan af netværket, en af de nemmeste måder at finde hosts på et netværk. Hvis ping-svar er slået fra på hosts, så er ARP-request scan at foretrække.

*nmap -PR 192.168.0.0/24*
ARP-request scan.

*nmap -p 80,443 192.168.0.6*
Scanner specifikke porte på hosts.

*nmap -p 80-100 192.68.0.6-50*
Scanner fra port 80 til og med port 100 på IP-adresser fra .6 til .50.

*nmap --top-ports 20 192.168.1.106*
Scanner top 20 porte. Se [[Top 20 TCP & UDP ports]] for de 20 mest populære porte. 20 kan erstattes med f.eks. 35.

*nmap -iL targets.txt*
Scanner alle mål der er listet i targets.txt.

*nmap -oN output.txt homepage.com*
Scanner homepage.com og gemmer resultatet i output.txt.

*nmap -oX output.xml homepage.com*
Samme som ovenover, gemmer bare i .xml-format.

*nmap -p 80 -n 8.8.8.8*
Undlader DNS resolution for scan, det kan spare lidt tid.

*nmap -sV 192.168.0.6*
Angiv service versioner

*nmap -sn -R -v 192.168.0.0/24*
ICMP ping only scan med reverse DNS opslag på ALLE hosts, selv dem der er nede

