---
layout: page
title: JavaScript
permalink: /javascript/
---

# JavaScript - Musklene og hjernen til en nettside

For at nettsiden vår skal ha oppførsel og kunne gjøre litt mer interessante ting, trenger vi å gjøre litt programmering.

Der HTML og CSS begge er Markup-språk, hvor man egentlig bare definerer hvordan man vil at ting skal være, 
er JavaScript et vaskeekte programmeringsspråk, som lar oss gjøre veldig mye mer.
Det betyr også at JavaScript er betydelig mer avansert og vanskeligere å lære seg enn HTML og CSS, så ikke fortvil om
dette fort blir veldig vanskelig - det tar lang tid å mestre programmering, og det er et veldig bredt og dypt tema.

Vi har forsøkt å holde dette så enkelt som mulig, men det er veldig lett for å havne ned i kaninhull her.

### Programmering 101
Et programmeringsspråk er noe som lar oss beskrive en rekke operasjoner til en datamaskin, nesten som en kake-oppskrift.

Vi skriver ned en rekke steg, og den pliktoppfyllende datamaskinen vil utføre disse stegene, en etter en.
Dette fører også til at den vil gjøre ting som åpenbart er feil, så lenge det står skrevet i koden at den skal gjøre det - 
det er dette vi gjerne kaller bugs.

For eksempel, kan vi gjøre matematikk med kode:
```javascript
let a = 100;
let b = 200;
let sum = a + b; // vil være lik '300'
```
I kodeblokken over, har vi sagt at vi definerer 2 variabler `a` og `b`, med tall-verdiene `100` og `200`.
Til slutt, lager vi en ny variabel, `sum`, som inneholder verdien `a + b`, eller `100 + 200`.

`//` bruker vi for å angi en kommentar, på samme måte som med HTML.

Vi avslutter linjene våre med `;`.

For å demonstrere hvordan datamaskinen gjør dette steg-for-steg:
```javascript
let a = 100;
let b = 200;
let sum = a + b; // er lik '300'

a = b; // nå har 'a' samme verdi som 'b': '200' (vi overskriver den opprinnelige verdien)
console.log(sum); // vil printe '300' i konsollen
sum = a + b; // vil nå være lik '400'
console.log(sum); // printer nå '400' i konsollen
```
(Merk at vi ikke trengte å skrive `let` de andre gangene, siden vi allerede hadde definert variablene).

Datamaskinen går gjennom hver linje, i tur og orden, og gjør som den får fortalt.
`console.log()` er en spesiell funksjon, som gjør at vi kan printe til konsollen verdien til det vi setter inni parantesene.

På CodePen kan du trykke på 'Console'-knappen for å få opp denne konsollen, eller du kan se i Developer Tools i nettleseren.

Du kan også skrive disse linjene direkte inn i konsollen i nettleseren, slik at de kjøres umiddelbart.

Vi kunne gjort: `console.log(100 + 200);` direkte i konsollen, for eksempel.

#### Oppgave 1:
- Bruk konsollen til å gjøre noen enkle utregninger
  - Bruk `console.log()`, og gjør `+`, `-`, `*`, `/`
  - Prøv å opprett noen variabler (`let someName = 100;`), og logg disse
  - Prøv å bruk variablene i utregningene, og overskriv de

---

### JavaScript
JavaScript er et språk som er laget for å bruke sammen med nettsider, og alle nettlesere støtter JavaScript.
Man kan bruke JavaScript til å gjøre ting direkte på HTML-siden vår, slik at vi får en litt mer interessant nettside.

Det er et veldig populært språk, og det er lett å finne hjelp og guider på nett for å komme i gang med å bruke det. 

For å bruke JavaScript i nettsiden, kan vi gjøre det på noen forskjellige måter:

Vi kan skrive koden vår direkte inn i en `<script>`-tag, i selve HTML-filen:
```html
<html>
  <head>
    <script>
      console.log('hei!');
    </script>
  </head>
  <body>
    <div>
      Hei!
    </div>
  </body>
</html>
```

Vi kan definere en egen `.js`-fil i samme mappe som HTML-filen, og peke på denne filen i HTML-koden:
```html
nettside.html:
<html>
  <head>
    <script src="litt-kode.js"></script>
  </head>
  <body>
    <div>
      Hei!
    </div>
  </body>
</html>

litt-kode.js:
console.log('hei!');
```

Eventuelt, om du bruker CodePen, kan vi skrive koden vår direkte inn i JS-fanen, som er helt til høyre.

Denne koden vil kjøre med en gang vi åpner nettsiden vår.

#### Oppgave 2:
- Print noe til konsollen når man går inn på nettsiden
  - Enten ved å ha det i en `<script>`-tag, eller ved å referere til en fil som er lokalt, eller ved å ha det i JS-fanen i CodePen

---

### HTML + JavaScript

Nå skal vi se litt på hvordan vi kan gjøre endringer på nettsiden vår med JavaScript.
Det vi egentlig gjør nå, er å legge til innhold i HTML-elementer.

Først, må vi få tak i et gitt element med JavaScript - det er flere måter å gjøre dette på, men la oss bruke `id`-attributtet.

`id`-attributtet er spesielt, og må være unik i HTML-dokumentet - dette betyr at verdien vi setter inn i `id`-attributten
bare kan brukes av et element, og kan ikke være lik for 2 elementer.

(For å gjøre det enkelt, legger jeg koden direkte inn i `<script>`-taggen, men du kan gjøre akkurat som du vil selv)
```html
<html>
  <head>
    <script>
      document.getElementById('player-1-name').innerHTML = '<b>Arne</b>';
      document.getElementById('player-2-name').innerHTML = '<b>Bjarne</b>';
    </script>
  </head>
  <body>
    Navnet til spiller 1 er: <div id="player-1-name"></div>
    <br>
    Navnet til spiller 2 er: <div id="player-2-name"></div>
  </body>
</html>
```
Så, hva gjorde vi her?

Vi brukte `document.getElementById()` til å finne elementet vårt (ved hjelp av `id`-attributten), og så satte vi `innerHTML` til å være et navn.

I tillegg satte vi det til å være en liten bit med HTML - `<b>Navn</b>` - slik at navnet har **fet skrift**.

Dette er et eksempel på hvordan vi kan bruke JavaScript til å endre HTML-en direkte i nettleseren.

Okay, men dette er nok mer nyttig om spilleren selv kan sette sitt eget navn - hva om de ikke heter 'Arne' eller 'Bjarne'?

Da kan vi bruke `<input>`-elementer, gi de `id`-attributter, og hente det ut via `.value` på elementet:
```html
<html>
  <head>
    <script>
      let playerOneName = document.getElementById('player-1-name').value;
      let playerTwoName = document.getElementById('player-2-name').value;
      console.log('player one: ' + playerOneName);
      console.log('player two: ' + playerTwoName);
    </script>
  </head>
  <body>
    Navnet til spiller 1 er: <input id="player-1-name">
    <br>
    Navnet til spiller 2 er: <input id="player-2-name">
  </body>
</html>
```

Men vent, nå logget det bare `"player one: "` i konsollen, selv om vi skrev et navn.
Dette er fordi disse feltene er tomme når vi går inn på siden vår, men koden vår kjører umiddelbart.

Vi trenger en knapp, som forteller oss når navnene er angitt.

For å få dette til, må vi begynne å definere funksjoner.
Funksjoner er små biter med kode som vi kan kjøre når vi trenger de, for eksempel når noen trykker på knappen.

I tillegg trenger vi å kjøre denne når knappen blir trykket på.

```html
<html>
  <head>
    <script>
      function printPlayerNames() {
        let playerOneName = document.getElementById('player-1-name').value;
        let playerTwoName = document.getElementById('player-2-name').value;
        console.log('player one: ' + playerOneName);
        console.log('player two: ' + playerTwoName);
      }
    </script>
  </head>
  <body>
    Navnet til spiller 1 er: <input id="player-1-name">
    <br>
    Navnet til spiller 2 er: <input id="player-2-name">
    <br>
    <button type="button" 
            onclick="printPlayerNames()">
      Print spillernes navn
    </button>
  </body>
</html>
```

Nå ser vi at det blir riktig i konsollen vår.

Vi definerte en funksjon, `printPlayerNames()`, og så sa vi at når knappen blir trykket, så skal den kjøre: `onclick="printPlayerNames()"`.
Merk at vi også skrev `type="button"` - dette er fordi default verdien til `<button>` er `type="submit"`, som har en litt annen oppførsel.

#### Oppgave 3:
- Lag et `<input>`-element hvor man kan skrive inn noe, og vis denne verdien en helt annen plass på nettsiden når man trykker på en knapp
  - Her må du kombinere de 2 eksemplene over, slik at vi endrer HTML'en et helt annet sted basert på denne knappen
  - `id`-attributtet vil være svært nyttig!

---



- Programmering 101
- Byggeklossene våre:
    - Variabler
    - Funksjoner
    - Typer
    - Lister
- HTML spesifikke greier:
    - `EventListener`
    - `document`-objektet
    - `querySelector`
- Hvordan bruke HTML og JavaScript sammen
- Oppgaver