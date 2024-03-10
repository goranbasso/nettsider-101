---
layout: page
title: JavaScript
permalink: /javascript/
---

# JavaScript - Musklene og hjernen til en nettside

For at nettsiden vår skal ha oppførsel og kunne gjøre litt mer interessante ting, trenger vi å programmere litt.

Mens HTML og CSS begge er Markup-språk, hvor man egentlig bare definerer hvordan man vil at ting skal være, 
er JavaScript et vaskeekte programmeringsspråk, som lar oss gjøre veldig mye mer.
Det betyr også at JavaScript er betydelig mer avansert og vanskeligere å lære seg enn HTML og CSS, så ikke fortvil om
dette fort blir veldig vanskelig - det tar lang tid å mestre programmering, og det er et veldig bredt og dypt tema.

Vi har forsøkt å holde dette så enkelt som mulig, men det er veldig lett for å havne ned i kaninhull her.

### Programmering 101
Et programmeringsspråk er noe som lar oss beskrive en rekke operasjoner til en datamaskin, nesten som en kake-oppskrift.

Vi skriver ned en rekke steg, og den pliktoppfyllende datamaskinen vil utføre disse stegene, én etter én.
Dette fører også til at den vil gjøre ting som åpenbart er feil, så lenge det står skrevet i koden at den skal gjøre det - 
det er dette vi gjerne kaller bugs.

Som et eksempel, kan vi gjøre matematikk med kode:
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

Å printe til konsollen kan være veldig nyttig mens man programmerer, for å se hvordan koden oppfører seg, og om den oppfører
seg sånn som vi forventer - kanskje vi har en bug?

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

Denne koden vil kjøre med en gang vi åpner nettsiden vår (eller når vi refresher).

#### Oppgave 2:
- Print noe til konsollen når man går inn på nettsiden
  - Enten ved å ha det i en `<script>`-tag, eller ved å referere til en fil som er lokalt, eller ved å ha det i JS-fanen i CodePen

---

### HTML + JavaScript

Nå skal vi se litt på hvordan vi kan gjøre endringer på nettsiden vår med JavaScript.
Det vi egentlig gjør nå, er å legge til innhold i HTML-elementer.

Først, må vi få tak i et gitt element med JavaScript - det er flere måter å gjøre dette på, men la oss bruke `id`-attributtet.

`id`-attributtet er spesielt, og må være unik i HTML-dokumentet - dette betyr at verdien vi setter inn i `id`-attributten
bare kan brukes av et element, og kan ikke være lik for 2 forskjellige elementer.

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

I tillegg trenger vi å kjøre denne funksjonen når knappen blir trykket på.

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
    <button onclick="printPlayerNames()">
      Print spillernes navn
    </button>
  </body>
</html>
```

Nå ser vi at det blir riktig i konsollen vår.

Vi definerte en funksjon, `printPlayerNames()`, og så sa vi at når knappen blir trykket, så skal den kjøre: `onclick="printPlayerNames()"`.

#### Oppgave 3:
- Lag et `<input>`-element hvor man kan skrive inn noe, og vis denne verdien en helt annen plass på nettsiden når man trykker på en knapp
  - Her må du kombinere de 2 eksemplene over, slik at vi endrer HTML'en et helt annet sted basert på denne knappen
  - `id`-attributtet vil være svært nyttig!

---
### Fleip eller fakta?

Når vi skriver kode, ønsker vi ofte å gjøre en ting dersom noe er sant, og noe helt annet dersom det ikke er sant.

Dette blir representert med verdiene `true` (sant) og `false` (ikke-sant) i JavaScript.

Man kan bruke dette for å sjekke om 2 verdier er like, eller om et tall er større enn et annet.

I JavaScript kan man bruke dobbelt-er-lik: 
- `a == b` (`a` er lik `b`)
- `a != b` (`a` er _ikke_ lik `b`)

Eller krokodille-gap: 
- `a > b` (`a` er større enn `b`) 
- `a < b` (`a` er mindre enn `b`)

Eller en kombinasjon:
- `a >= b` (`a` er _minst_ like stor som `b`)
- `a <= b` (`a` er lik eller mindre enn `b`)

```javascript
console.log(10 == 10); // true
console.log(10 == 9);  // false
console.log(10 != 9);  // true
console.log(10 > 0);   // true
console.log(10 < 9);   // false
console.log(9 < 9);    // false
console.log(9 <= 9);   // true
```

Man kan også bruke er-lik (`==`) på tekst:
```javascript
console.log('hei' == 'hei');   // true
console.log('hei' == 'hallo'); // false
console.log('hei' != 'hallo'); // true
```
Merk, det finnes også en trippel-er-lik (`===`),  som er litt strengere, og fungerer ved at de bare er like dersom 
de er av akkurat samme _type_ (tall kontra tekst):
```javascript
console.log('10' == 10);    // true
console.log('10' === 10);   // false
console.log('10' === '10'); // true
console.log(10 === 10);     // true
```
I denne workshopen begrenser vi oss til dobbelt-er-lik `==`, bare fordi det er enklere - men det ansett som dårlig skikk å bruke `==`,
og helst bør man alltid bruke `===`, da `==` kan føre til rare bugs som er vanskelige å finne.

Man kan bruke disse sammen med `if`-setninger, som gir oss en måte å bestemme hva som skal skje dersom noe er `true`, 
og hva som skal skje når det er `false` - med andre ord, litt som en enten-eller setning.

```javascript
let a = 1;
let b = 2;

// her sier vi: dersom a < b, så dette; else, noe annet
if (a < b) {
    console.log('a var større enn b!');
} else {
    console.log('a var mindre enn b!');
}
```

Men dette er ikke helt riktig, hva med det tilfellet der `a` har samme verdi som `b`?

Da må vi skrive dette litt om, og bruke en `else if`:
```javascript
let a = 101;
let b = 201;

if (a < b) {
    console.log('a var større enn b!');
} else if (a > b) {
    console.log('a var mindre enn b!');
} else {
    console.log('a var like stor som b!')
}
```

Ved hjelp av denne, kan vi sette opp logikk for å styre hva koden vår skal gjøre, så det er et veldig viktig og sentralt konsept i programmering. 

#### Oppgave 4:
- Ved å bruke det du har lært hittil, kan du lage en enkel nettside der man prøver å gjette hvilket tall datamaskinen tenker på?
  - La nettsiden gi beskjed om tallet man gjettet var lavere, høyere, eller like stort som det maskinen valgte 
  - La datamaskinen velge et tall (ved hjelp av funksjonen under), og la brukeren angi sitt til i et `<input>`-element
  - Så kan man ha en knapp for å gjøre selve sjekken - la beskjeden komme frem på selve nettsiden, og ikke bare logg den i konsollen
  - En enkel hjelpefunksjon, som gir et tilfeldig tall mellom 1 og 6 (som å rulle en terning):

```javascript
function rollDice() {
    let randomNumber = Math.floor((Math.random() * 6) + 1); // litt hokus pokus 
    return randomNumber;
}
```

Eksempel på hvordan du bruker denne funksjonen:
```javascript
let diceRoll = rollDice();
console.log('rullet en terning, og fikk: ' + diceRoll);
```
Merk at siden vi i `rollDice()`-funksjonen sier `return randomNumber`, så betyr det at funksjonen gir fra seg verdien som er i
`randomNumber`, og på den måten kan vi ta verdien rett i en variabel (`diceRoll` i eksemplet over).

#### Oppgave 5:
- Ved å bruke det du har lært hittil, kan du lage en enkel nettside hvor man kan spille stein-saks-papir mot datamaskinen?
  - Det blir fort mange `if`-setninger her, så holdt tungen beint i munnen - kan man forenkle dette?
  - En enkel hjelpefunksjon, sånn at datamaskinen tilfeldig velger stein, saks, eller papir:

```javascript
function rockPaperOrScissors() {
    let randomNumber = Math.floor((Math.random() * 10) % 3); // litt hokus pokus
    if (randomNumber === 0) {
        return 'stein';
    } else if (randomNumber === 1) {
        return 'saks';
    } else {
        return 'papir'; 
    }
}
```

---

### CSS + JavaScript

Vi kan også bruke JavaScript til å endre på CSS, slik at utseendet også kan endre seg basert på hva brukeren gjør.

På samme måte som at vi brukte `id`-attributtet til å velge elementer, kan vi bruke `class`-attributtet til å velge *flere* elementer.
Da vil vi få en liste av alle elementene som har denne klassen.

Ved hjelp av såkalte `for`-løkker (også kalt loops), så kan vi gjøre den samme handlingen på flere elementer rett etterhverandre,
slik at vi slipper å skrive de samme linjene om og om igjen.

```html
<html>
  <body>
    <div class="our-div">Vår første div</div>
    <div class="our-div">Vår andre div</div>
    <div class="our-div">Vår tredje div</div>
    <div class="our-div">Vår fjerde div</div>
    
    <br>
    <button onclick="changeColor('blue')">Blå</button>
    <button onclick="changeColor('red')">Rød</button>
    <button onclick="changeColor('green')">Grønn</button>
  </body>
</html>
```
Om vi så definerer funksjonen `changeColor()`:
```javascript
function changeColor(color) {
    let elements = document.getElementsByClassName('our-div');
    for (let i = 0; i < elements.length; i++) {
        elements[i].style.color = color;
    }
}
```

Så ser vi at alle `div`-ene våre vil endre farge samtidig, og vi trengte bare å skrive `.style.color = color;` en gang. 

Men her er det veldig mye som skjer, og en del nye konsepter - så la oss ta det linje for linje:

**Første linje:**
```javascript
function changeColor() {
```
På denne linjen definerer vi vår funksjon, `changeColor()`, men i tillegg, så sier vi at den tar et parameter, en verdi som 
man kan angi når man bruker den.
Det er derfor vi i HTML-en sier:
```html
<button onclick="changeColor('blue')">Blå</button>
```
Da har vi sagt at vi kaller funksjonen `changeColor()`, med `'blue'` som parameter.
Når vi da bruker `color`-variabelen inne i funksjonen, så har den verdien `'blue'`. Gjerne sjekk dette med `console.log()` inne i funksjonen! 

**Andre linje:**
```javascript
let elements = document.getElementsByClassName('our-div');
```
Dette ligner veldig på `document.getElementById()`, som vi har brukt før, men forskjellen er at denne sjekker `class`-attributten,
og at vi får en _liste_ tilbake (siden det er flere elementer som kan klassen `our-div`).

Lister er litt spesielle, og er sitt helt eget kapittel i programmering. Det er et veldig viktig konsept i programmering,
og det lar oss gjøre mange veldig nyttige ting.
I dette tilfellet, vil vi få en liste som ser noe slikt ut, der listen vår er satt til å befinne seg i variabelen `elements`:
```
elements = [
    0: <div class="our-div">Vår første div</div>,
    1: <div class="our-div">Vår andre div</div>,
    2: <div class="our-div">Vår tredje div</div>,
    3: <div class="our-div">Vår fjerde div</div>
]
```
Vi kan da hente ut det tredje elementet i listen, ved å gjøre: `elements[2]`.
En snedig ting, er at datamaskiner teller fra 0 - så derfor er det første elementet i listen i _indeks_ `0`, mens det tredje er i indeks `2`.
Det kan være litt forvirrende, men etter nok øving, blir man vant til dette.

**Tredje linje:**
```javascript
for (let i = 0; i < elements.length; i++) {
```
Her foregår det en hel del ting - dette er måten man definerer en `for`-løkke på, og det ser nok litt avansert ut, ved første øyekast.
For å bryte den ned enda mer:
- `for ()` - forteller oss at vi har tenkt å definere en `for`-løkke
- `let i = 0;` - forteller oss at vi har en telle-variabel, som vi kaller for `i`, og den skal begynne med verdien `0`
- `i < elements.length;` - forteller oss at vi skal fortsette å kjøre `for`-løkken _så lenge_ `i` _er mindre enn antall elementer i_ `elements` 
- `i++` - forteller oss at for hver runde løkken kjører, skal vi øke verdien av `i` med `1`

Siden verdien i `i` øker hver runde, vil den etterhvert få verdien `3`, som er det samme som `elements.length`, 
og da vil setningen `i < elements.length` returnere `false`, og løkken stopper å kjøre.

Dette er litt avansert, men etterhvert blir man vant til dette også.

**Fjerde linje:**
```javascript
elements[i].style.color = color;
```
Dette er koden som vi har inne i `for`-løkken vår, inni disse 2 krøllparantesene: `{ }`.

Denne koden skal kjøre for _hver runde_ av `for`-løkken vår, og det vi gjør, er at vi setter `style.color` 
(som er litt som å sette `color`-verdien i CSS direkte) til å være lik `color`-variabelen som vi tok inn i funksjonen.

Vi bruker `i` for å si hvilket element i listen vi ønsker å gjøre det på (og husk at denne listen begynner med `0`!).

For å se litt nærmere på hvordan `for`-løkken oppfører seg, kan du prøve å kjøre følgende kode:
```javascript
for (let i = 0; i < 10; i++) {
    console.log('i har verdien: ' + i);
}
```
Prøv å lek litt med verdiene du setter i de forskjellige plassene der man definerer `for`-løkken.
Hva skjer om du begynner med et høyere tall enn `0` ? Hva skjer om du endrer sjekken vi gjør hver runde (`i < 10`)? Hva skjer om du gjør `i--` ? 
Hva skjer om du gjør `i += 2` (istedet for `i++`) ?

Merk at det er lett å havne i en uendelig løkke her! Hvorfor skjer det?

#### Oppgave 6:
- Det finnes en spesiell type man kan sette på `<input>`:
  - `<input type="color">`
  - Dette gjør `<input>`-elementet om til en farge-velger.
- Skrive om koden over, slik at man selv kan velge nøyaktig hvilken farge `div`-ene skal få, ved å hente ut denne verdien fra `<input>`-elementet
  - Tips: Kan hente ut verdien via `.value`, på samme måte som vi gjorde når vi printet navnene til spillerne tidligere.
  - Tips: Hvilken verdi er det som ligger inni `.value` ? Print denne ut for å se hvordan det ser ut

---
### Veien videre
Om du har kommet så langt, gratulerer! Dette er ikke lett, og det er veldig mye å lære seg, men så er også mulighetene enorme.

Bare med de tingene du har lært hittil, kan du lage veldig mye forskjellig, og det er nesten bare fantasien som setter grenser.

Noen forslag på mer avanserte oppgaver du kan bryne deg på, som ikke er i noen spesiell rekkefølge:
- Med alt du har lært, lag en enkel **kalkulator**, som kan gjøre pluss, minus, ganging, og deling
- Lag en nettside med en **tabell**, hvor brukere kan legge til, slette, og redigere rader i tabellen
  - Tabellen bør ha flere kolonner, med forskjellige verdier inni seg
- Lag en **profil-side**, der brukere kan legge inn tekst om seg selv, bilder, og velge mellom flere farger
- **Hva som helst**, så lenge du bruker både HTML, CSS, og JavaScript sammen 

Et eksempel på en nettside som bruker HTML, CSS, og JavaScript sammen:
[Tic-tac-toe]({{site.baseurl}}/eksempler/tic-tac-toe)

Denne kan utvides, eller endres, eller brukes som eksempel.
Den har for eksempel veldig simplistisk CSS - kan vi få den til å se bedre ut?

### Oppsummering:
- JavaScript er et programmeringsspråk, som man kan bruke sammen med HTML og CSS, for å lage nettsider med oppførsel
- Programmering er et dypt og bredt tema, men mulighetene er enorme
- Man kan gjøre uregninger med tall, og vi kan angi verdier til variabler
- Man kan printe ting ut til konsollen underveis
- Man kan bruke `true` og `false` sammen med `if`-setninger for å bestemme hva som skal skje i gitte tilfeller
- Man kan jobbe med lister, og kjøre gjennom disse med `for`-løkker for å gjøre samme operasjon flere ganger
- Man kan endre på HTML'en direkte med JavaScript, ved å få tak i elementene via `document`