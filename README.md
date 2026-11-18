# BeredskAppen

BeredskAppen er en lokal-først PWA som hjelper norske husstander med å forberede seg på å klare seg i én uke. Den samler sjekkliste, vannbeholdning, utstyr, utløpsdatoer, oppbevaringssteder, husstandsplan og kortfattet veiledning for vanlige situasjoner.

Appen er et hjelpemiddel for egenberedskap, ikke en tjeneste for nødvarsling, medisinske råd eller løpende myndighetsinformasjon. Følg alltid råd fra myndighetene i en reell hendelse.

## Personvern og lagring

- Ingen konto, server eller analyseverktøy brukes.
- Data om husstand, kontakter, plan og beholdning lagres kun lokalt i nettleseren med IndexedDB.
- Appen kan brukes uten nett etter at den er åpnet første gang.
- QR-etiketter inneholder bare en tilfeldig, lokal stedstoken – ikke adresse, personopplysninger eller beholdningsdata.

Lokale data følger nettleseren og den aktuelle nettstedsadressen. Data fra en lokal utviklingsadresse overføres derfor ikke automatisk til GitHub Pages-adressen.

## Kjør lokalt

Appen har ingen avhengigheter eller byggesteg. Start en lokal statisk webserver fra prosjektroten, for eksempel:

```sh
python3 -m http.server 8000
```

Åpne deretter <http://localhost:8000>. En webserver (ikke `file://`) kreves for at service workeren og offline-funksjonaliteten skal virke.

## Publisering med GitHub Pages

Prosjektet publiseres av [`.github/workflows/deploy-pages.yml`](.github/workflows/deploy-pages.yml). Arbeidsflyten publiserer rotmappen som en statisk GitHub Pages-artifakt når det pushes til `main` eller `master`, eller når den startes manuelt.

Første gang repository-eieren publiserer:

1. Push repositoryet til GitHub.
2. Åpne **Settings → Pages** i repositoryet.
3. Velg **GitHub Actions** under *Build and deployment → Source*.
4. Push til `main` eller `master`, eller velg **Run workflow** i fanen **Actions**.

Siden blir normalt tilgjengelig på `https://<eier>.github.io/<repository>/`. Relative ressursstier er brukt slik at PWA-en, manifestet og service workeren også virker på denne prosjektadressen.

Ved oppdateringer kan en installert app trenge å lukkes og åpnes på nytt før ny service worker er aktiv. Endre cache-versjonen i `service-worker.js` når appens cachede ressurser endres.

## Kontroll før publisering

- Åpne appen, fyll inn litt testdata og last siden på nytt for å kontrollere lokal lagring.
- Når appen er lastet én gang, slå av nettverkstilgang og kontroller at de sentrale sidene fortsatt åpner.
- Kontroller tastaturnavigasjon og layout på liten skjerm.
- Test den publiserte Pages-adressen separat; den har sin egen lokale datalagring.

## Kilder og tredjepartsprogramvare

Sjekklisten og den generelle veiledningen bygger på materiale fra Direktoratet for samfunnssikkerhet og beredskap (DSB). Gjennomgangsdato vises i appen. Referanse-PDF-er ligger i [`docs/reference/`](docs/reference/) og skal ikke endres.

QR-generering bruker den medfølgende `qrcode-generator` 1.4.4-biblioteket under MIT-lisens. Se [`vendor/LICENSE-qrcode-generator.txt`](vendor/LICENSE-qrcode-generator.txt).
