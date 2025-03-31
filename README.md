# Workshop_3a
Workshop dle §3a - vzorová data a materiály

Workshop je zaměřen na evaluaci informační hodnoty datových setů / množin dat popř. celých informačních systémů veřejné správy. V sadě §3a_vzor1 1 se nachází pdf, kde je vyznačena datová sada KML ke stažení z Národního katalogu otevřených dat, prosíme stáhněte si ji pro praktickou činnost. Velikost této sady překračuje limit Github repozitáře.

Možné podoby balíků SIP dle §3a:
1)	Pro dlouhodobé uložení exportů databází upřednostňuje Národní archiv formát SIARD (pomocí open source nástroje DBPTK, který má podporu pro materializované view), Možno i v podobě JAR. K archivaci do formátu SIARD vyžadujeme přiložit dokumentaci informační systému vytvořenou dodavatelem, manuály, datové modely, popisy dat atp. a soubor selects.txt (popsáno níže), který musí obsahovat minimálně základní relace, které vrací seznam entit a detail entity. 

2)	Pokud výstup do SIARD není možný, lze použít formát CSV, kódovaný v UTF8. Data ve formátu CSV budou strojově validována a kontrolována. Balík takového to exportu musí vedle tabulkových dat obsahovat i potřebná metadata, číselníky (detailně dále), které umožní zobrazená data správně pochopit. A to v této podobě:
Balík by měl mít tuto podobu: 
/System_nazev (kořenový adresář)
                        /data (adresář s datovými tabulkami, včetně těch číselníkových)
                        /metadata (adresář s pomocnými soubory:  
info.txt, list.txt, createdb.sql, query.txt
                        /dokumentace (adresář s dokumentací, manuály, printscreeny atd.)
Popis obsahu pomocných metadatových souborů:
•	Info.txt, soubor obsahuje stručný popis extrakce ze systému, jméno osoby, která archivaci/export provedla, název orig. databázového prostředí (Např.: „Systém byl založen na prostředí MS SQL, , Archivaci provedl administrátor     systému, jméno, příjmení, v roce 2021 formou prostého exportu do sestavy tabulek ve formátu CSV o celkovém počtu X.

•	description.txt popis vlastního systému: např. sloužil k evidenci rozličných entit

•	list.txt, který obsahuje seznam tabulek, kódování, oddělovače atd. (šablonu lze v případě zájmu vyžádat)

•	createdb.sql, je soubor kterým se vytvoří databáze, a tu bude možné tabulkami strojově naplnit. Tedy soubor createdb.sql bude obsahovat příkazy pro vytvoření všech tabulek, jejich sloupců vč. datových typů.

•	selects.txt, kde bude uveden příkaz SELECT, který se data spojí do požadovaného náhledu na data (tzv. view). Selecty mohou, ale nemusí být vždy uchovány pouze v aplikaci. Pokud jsou známé, pak prosíme přiložit.
Takový balíček bude strojově validován, a to včetně testu importu nástroje pro prohlížení

3)	Ve vhodný případech (databáze spravují velká data, která se hodně proměňují v rámci provozu) se akceptuje archivace např. ve formě statistických výstupů, datových souhrnů (agregací) nejlépe s co největší podrobností v podobě atributů atp. Archivace je možná v podobě SIARD (srv. Bod 1)), CSV (srv. Bod 2)), ale také jako XML nebo JSON, v obou případech je nezbytná přítomnost schématu z důvodu datové validace a pro potřeby zpracování dat v budoucnu.
