# Integritetspolicy för PastPaths

**Version 1.1 — gäller från PastPaths 1.9.0**

## Sammanfattning

**PastPaths sparar all din släktforskning lokalt på din egen dator. Inget skickas till mig eller någon annan utan att du själv väljer det. Programmet använder bara nätverket när du själv öppnar kartsidan, öppnar sidan Platsbibliotek eller importerar därifrån, eller importerar från WordPress (se avsnitt 3).**

Det här dokumentet förklarar i detalj vad det betyder.

## 1. Vem ansvarar för datan?

PastPaths är ett lokalt program — det körs på din dator, sparar all data på din dator och skickar aldrig din släktdata till mig. Det enda programmet hämtar från en server som drivs av mig är Platsbibliotekets paket (se avsnitt 3.5).

Det innebär att **du själv** är personuppgiftsansvarig för den släktdata du matar in i programmet, inte jag som utvecklat det. Jag hanterar aldrig din släktdata och kan inte komma åt den.

Den här konstruktionen är ett aktivt designval. Den ger dig:

- Full kontroll över din data
- Skydd från policyändringar hos en tjänsteleverantör
- Skydd om utvecklaren av PastPaths skulle försvinna — datan är din och fungerar i andra program via GEDCOM-export

## 2. Vad sparas, var och hur

### 2.1 Vad sparas

PastPaths kan spara:

- Personuppgifter du själv matar in (namn, datum, orter, anteckningar)
- Foton och dokument du laddar upp
- Källhänvisningar
- Blogginlägg och berättelser
- Inställningar för programmet

### 2.2 Var sparas datan

All data lagras lokalt på din dator. För närvarande stöds endast Windows som plattform.

Programmet och din data ligger i samma mapp. Om du inte valde en annan mapp vid installationen är det:

- **Windows:** `C:\Users\DITT_ANVÄNDARNAMN\AppData\Local\PastPaths`

I mappen finns:

- `pastpaths.db` — SQLite-databas med all din släktdata (personer, händelser, platser, relationer, källor, blogginlägg m.m.). Bredvid den kan filerna `pastpaths.db-wal` och `pastpaths.db-shm` finnas. De hör till databasen.
- `uploads\` — dina uppladdade foton och dokument i originalformat. I undermappen `imports` kan det ligga kopior av filer som du har importerat.
- `webview_data\` — programmets egna inställningar (till exempel valt språk) och en cache där bland annat kartbilder kan sparas.
- `logs\` — programmets loggfiler (se avsnitt 2.4).
- `_internal\` och övriga programfiler från installationen.

Loggfilerna ligger alltid i `C:\Users\DITT_ANVÄNDARNAMN\AppData\Local\PastPaths\logs`, även om du valde en annan mapp vid installationen.

Om du flyttar eller kopierar mappen `PastPaths` följer hela din databas och alla dina filer med. Du kan flytta hela mappen till en annan dator om du vill. Stäng PastPaths först, så att databasen är komplett.

Versioner för Linux och Android är planerade men inte släppta. När de finns kommer denna policy att uppdateras med deras sökvägar.

#### Filer utanför programmappen

Några funktioner sparar filer på andra ställen på din dator. De ligger kvar tills du själv tar bort dem, även om du avinstallerar PastPaths:

- **Säkerhetskopior** som du skapar på sidan Import/Export sparas som ZIP-filer i `Dokument\PastPaths\Backups`. De innehåller databasen och dina uppladdade filer.
- **GEDCOM-export** sparas i `Dokument\PastPaths\GEDCOM`.
- **PDF-rapporter** och släktträdets PDF sparas i `Dokument\PastPaths\Reports`. Rapporter från äldre versioner ligger kvar i `Dokument\PastPaths\Rapporter`.
- **När du återställer en säkerhetskopia** sparas först en kopia av den nuvarande databasen i `Dokument\PastPaths-Backups\pre-restore`.
- **Installationsprogrammets säkerhetskopior** skapas bara när du uppgraderar PastPaths och bara om du har valt det. Säkerhetskopian av databas och uppladdade filer är förvald. En fullständig kopia av hela programmappen görs bara om du kryssar i den. Du väljer själv mapp. Förslaget är `Dokument\PastPaths-Backups`. Varje gång skapas en ny mapp med datum och tid. Gamla kopior rensas aldrig automatiskt.

Mappen Dokument är den som Windows anger. Har Windows flyttat den till OneDrive sparas filerna där och synkas då till OneDrive.

### 2.3 Inloggning

PastPaths har ingen inloggning. Programmet körs lokalt på din dator och alla som har åtkomst till ditt användarkonto i Windows kan starta programmet och se din släktdata.

Om du behöver skydda din data mot andra som har åtkomst till samma dator — använd diskkryptering (se avsnitt 9) eller separata användarkonton i Windows.

En framtida version kan komma att införa valfritt lösenordsskydd, men i nuläget är säkerheten beroende av din dator och ditt Windows-användarkonto.

### 2.4 Loggfiler

PastPaths skriver en teknisk logg som används för felsökning. Den sparas i `C:\Users\DITT_ANVÄNDARNAMN\AppData\Local\PastPaths\logs\pastpaths.log`.

- Loggen innehåller bland annat programversion, sökvägar till programmets mappar (där ditt Windows-användarnamn ingår), antal poster vid import och tekniska felmeddelanden.
- Vid normal användning skrivs inga namn, sökord eller filnamn till loggen. Vid fel kan loggen däremot innehålla sökvägar till filer på din dator.
- Loggen växer inte obegränsat. När filen når 1 MB sparas den undan och en ny fil påbörjas. Högst fem filer sparas, alltså cirka 5 MB.
- Loggen stannar på din dator och skickas aldrig någonstans. Om du rapporterar ett fel kan du själv välja att skicka den till mig.

### 2.5 Avinstallation

När du avinstallerar PastPaths får du först välja om du även vill radera data som programmet har sparat i programmappen:

- **Databasen** — `pastpaths.db` med tillhörande filer
- **Uppladdade filer** — mappen `uploads`
- **Loggfiler och appens inställningar** — mapparna `logs` och `webview_data`

Databasen och de uppladdade filerna är aldrig förvalda. Loggfiler och inställningar är förvalda. Det som inte är ikryssat ligger kvar. Väljer du Avbryt avbryts hela avinstallationen och ingenting tas bort.

Programfilerna tas alltid bort. Filer som PastPaths har sparat utanför programmappen (se avsnitt 2.2) tas aldrig bort av avinstallationen. Vid en tyst avinstallation, till exempel från kommandoraden, raderas ingen data.

## 3. Datan lämnar inte din dator — undantag

PastPaths kommunicerar inte med externa servrar för normal användning.

**Att notera:** Import av GEDCOM-filer från program som Ancestry, MyHeritage, TNG (The Next Generation) och Disgen sker helt lokalt. Du exporterar själv en GEDCOM-fil från det andra programmet och väljer den filen i PastPaths — programmet kontaktar aldrig dessa tjänster direkt.

De enda situationerna där programmet använder nätverket är:

### 3.1 Du importerar från WordPress

Om du importerar en WordPress-export laddar PastPaths ner bilderna från din WordPress-webbplats till din lokala dator. Trafiken sker mellan din dator och din WordPress-server — inte via mig.

### 3.2 Du exporterar och delar manuellt

Om du själv exporterar GEDCOM, skapar PDF-rapporter eller delar bilder så är det din aktiva handling. PastPaths skickar aldrig något automatiskt.

### 3.3 Programuppdatering

PastPaths kontrollerar inte automatiskt om det finns nya versioner av programmet och skickar ingen versionsinformation någonstans. Du behöver själv besöka [pastpaths.se](https://pastpaths.se) för att se om en nyare version finns tillgänglig och i så fall ladda hem den.

Platsbiblioteket visar om det finns nyare versioner av platspaketen, men bara när du själv öppnar sidan Platsbibliotek (se avsnitt 3.5).

### 3.4 Kartfunktion

Om du öppnar sidan **Karta** hämtar programmet kartbilder (s.k. *tiles*) från OpenStreetMaps publika server (`tile.openstreetmap.org`). Trafiken sker mellan din dator och OpenStreetMap — inte via mig. Det som skickas är koordinaterna för den kartruta som visas (alltså vilket geografiskt område du tittar på), din IP-adress och standardiserad webbläsarinformation. Inga uppgifter ur din databas — varken namn, koordinater eller söktermer — skickas vidare. Sökrutan på kartsidan filtrerar enbart bland redan inlästa lokala platser.

PastPaths innehåller **ingen geokodningsfunktion**. Koordinater till platser anges manuellt eller importeras från GEDCOM — inga anrop görs för att slå upp adresser mot externa tjänster. Om du aldrig öppnar kartsidan skickas inga anrop till OpenStreetMap. Behandlingen hos OpenStreetMap regleras av deras egen [integritetspolicy](https://wiki.openstreetmap.org/wiki/Privacy_Policy).

### 3.5 Platsbiblioteket

Platsbiblioteket innehåller färdiga paket med platser, till exempel Sveriges län, som du kan importera. Paketen ligger på pastpaths.se.

- När du öppnar sidan **Platsbibliotek** hämtar programmet en förteckning över tillgängliga paket från pastpaths.se.
- När du importerar ett paket hämtas förteckningen på nytt och därefter själva paketfilen.

Det som skickas är din IP-adress, vilken fil som hämtas och programmets namn (`PastPaths-PlaceLibrary/1`). Inga uppgifter ur din databas skickas. Programmet kontaktar inte pastpaths.se när det startar. Om du aldrig öppnar sidan Platsbibliotek skickas inga anrop.

Webbservern för pastpaths.se sparar, som alla webbservrar, tekniska uppgifter om anropen i serverloggar. Hur det går till beskrivs på [webbplatsens integritetssida](https://pastpaths.se/website-privacy/).

## 4. Telemetri, statistik och analys

**PastPaths samlar inte in användarstatistik, anonym eller annan.** Jag vet inte hur du använder programmet, hur ofta du startar det, eller vilka funktioner du använder. Jag har inga "anonyma användarsiffror" att hänvisa till.

Det här är ett medvetet val. För släktforskning — där datan är personlig och ofta känslig — anser jag att privacy by design är viktigare än produktoptimeringsdata.

## 5. Tredjeparter

PastPaths bygger på open source-bibliotek (lista finns i `THIRD-PARTY-LICENSES.md`). Dessa körs som en del av programmet på din dator och har inte separat åtkomst till din data.

PastPaths integrerar inte med:

- Sociala medier
- Reklamnätverk
- Spårningstjänster
- Externa molntjänster (utöver vad du själv aktivt väljer)

> *Undantag: kartfunktionen kontaktar OpenStreetMap och Platsbiblioteket hämtar paket från pastpaths.se, se avsnitt 3.4 och 3.5.*

## 6. Ditt ansvar för andra personers data

När du lägger in uppgifter om släktingar — särskilt nu levande släktingar — blir **du** ansvarig för den behandlingen enligt GDPR.

PastPaths hjälper dig genom att hålla all data lokalt, vilket ger lägre risk än molntjänster.

PastPaths döljer inte uppgifter om levande personer i rapporter eller i GEDCOM-exporten. Tänk på det innan du delar en rapport eller en exportfil.

Du behöver själv:

- Tänka på om du har laglig grund att behandla uppgifterna
- Informera berörda personer i den utsträckning det är rimligt
- Vara försiktig med vad du delar och med vem
- Respektera släktingars önskemål om de vill bli "borttagna"

## 7. Dina rättigheter under GDPR

Eftersom du själv är personuppgiftsansvarig för din släktdata har du **redan full teknisk kontroll** över dina rättigheter:

- **Rätt till tillgång:** all din data är tillgänglig i programmet och i den lokala mappen
- **Rätt till rättelse:** du kan redigera när som helst
- **Rätt till radering:** du kan radera personer, händelser, hela databasen
- **Rätt till dataportabilitet:** GEDCOM-export ger dig din data i standardformat
- **Rätt till begränsning:** du kontrollerar själv vem som har åtkomst till din dator

Vad gäller utvecklaren av PastPaths — jag har ingen data om dig att radera eller lämna ut.

## 8. Barn

Om din släktforskning inkluderar nu levande barn (under 13 år enligt GDPR-praxis) bör du vara extra försiktig. Sådana uppgifter har särskilt skydd och kräver oftast vårdnadshavares samtycke. PastPaths hindrar dig inte tekniskt från att lägga in uppgifter, men det är ditt ansvar att göra det rätt.

## 9. Säkerhet

Programmets säkerhet beror till stor del på din dators säkerhet. Jag rekommenderar:

- Använd ett tryggt lösenord till din dator
- Håll operativsystemet uppdaterat
- Använd en pålitlig lösning för säkerhetskopiering
- Var försiktig med vem som får fysisk åtkomst till din dator

Programmets databas är inte krypterad i sig. Om någon får åtkomst till din mapp kan de läsa databasen. Om du behöver starkare skydd — använd diskkryptering (BitLocker på Windows är inbyggt i Windows Pro och Enterprise; för Windows Home finns Device Encryption på de flesta moderna datorer).

## 10. Säkerhetskopiering och dataförlust

Eftersom datan ligger lokalt försvinner den om din dator går sönder och du inte har säkerhetskopior. Jag har ingen kopia. Det här är priset för fullständig integritet — du måste själv ta ansvar för säkerhetskopiorna.

PastPaths hjälper dig på två sätt:

- På sidan Import/Export kan du när som helst skapa en säkerhetskopia av databasen och dina uppladdade filer.
- När du uppgraderar PastPaths erbjuder installationsprogrammet att göra en säkerhetskopia innan den nya versionen installeras.

Säkerhetskopiorna sparas på din dator (se avsnitt 2.2). Spara gärna en kopia även på en annan enhet, till exempel en extern hårddisk.

Råd om säkerhetskopiering finns i programmets dokumentation.

## 11. Vad händer om PastPaths upphör?

Om jag som utvecklare en dag försvinner — datan är fortfarande din. Den ligger på din dator i:

- En SQLite-databas (öppet, dokumenterat format som kan läsas av många program)
- En mapp med dina foton och dokument (i originalformat)

Du kan exportera till GEDCOM och läsa in i andra släktforskningsprogram. Bilderna och dokumenten följer i dag inte med i GEDCOM-exporten, men de finns i mappen `uploads` i originalformat. Du blir aldrig "fast" i PastPaths.

## 12. Ändringar av denna policy

När den här policyn uppdateras publiceras den nya versionen på [pastpaths.se](https://pastpaths.se) tillsammans med information om vad som ändrats. Den version av policyn som följde med din installation fortsätter att gälla för den versionen — du binder dig alltså inte till framtida policyändringar bara för att du har programmet installerat.

## 13. Kontakt

Frågor eller funderingar om integritet och PastPaths:

- E-post: **[Support](mailto:support@pastpaths.se)**
- Webb: **[https://pastpaths.se](https://pastpaths.se)**

För frågor om GDPR generellt, eller om du behöver klaga på behandling av dina personuppgifter, kan du vända dig till Integritetsskyddsmyndigheten (IMY): [imy.se](https://www.imy.se).

---

*Senast uppdaterad: 2026-10-10*