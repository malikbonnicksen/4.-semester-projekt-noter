# MAC flooding
MAC-flooding er når en switch bliver flooded med nye MAC adresser. Målet er at fylde CAM tabellen, som indeholder MAC adresserne der er forbundet til switchen. Når CAM tabellen bliver fyldt, så vil switchen gå i fail-open mode, hvor den reelt set ender som en gammeldags hub, dvs. alle indkommende pakker bliver sendt ud af alle porte.  

#### Beskyttelse mod MAC flooding:  
AAA (authentication, authorization, accounting) server kan bruges til at sikre bestemte MAC adresser kan forbinde til netværket.  
Port security kan bruges på switchen til at begrænse antallet af MAC adresser der kan forbinde til porte. En lille tabel af ’sikre’ MAC adresser kan også tilføjes til switchen.