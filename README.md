# BeredskAppen

BeredskAppen er en lokal-først PWA som hjelper norske husstander med å forberede seg på å klare seg i én uke. Appen samler sjekkliste, vannbeholdning, utstyr, utløpsdatoer, oppbevaringssteder, husstandsplan og kortfattet veiledning for vanlige situasjoner.

Appen er tilgjengelig på norsk bokmål og engelsk, og kan brukes uten nett etter første innlasting.

## Lokal lagring og personvern

- Ingen konto, server eller analyseverktøy brukes.
- Data om husstand, kontakter, plan og beholdning lagres kun lokalt i nettleseren med IndexedDB.
- QR-etiketter inneholder bare en tilfeldig, lokal stedstoken – ikke adresse, personopplysninger eller beholdningsdata.

Lokale data følger nettleseren og den aktuelle nettstedsadressen. Data fra én adresse eller enhet overføres ikke automatisk til en annen.

## Ansvarsfraskrivelse

BeredskAppen er et hjelpemiddel for egenberedskap. Den er ikke en tjeneste for nødvarsling, medisinske råd eller løpende myndighetsinformasjon. Følg alltid råd fra myndighetene i en reell hendelse.

## Kilder og tredjepartsprogramvare

Sjekklisten og den generelle veiledningen bygger på materiale fra Direktoratet for samfunnssikkerhet og beredskap (DSB). Gjennomgangsdato vises i appen. Referanse-PDF-er ligger i [`docs/reference/`](docs/reference/) og skal ikke endres.

QR-generering bruker den medfølgende `qrcode-generator` 1.4.4-biblioteket under MIT-lisens. Se [`vendor/LICENSE-qrcode-generator.txt`](vendor/LICENSE-qrcode-generator.txt).
