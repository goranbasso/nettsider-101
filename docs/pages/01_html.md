---
layout: page
title: HTML
permalink: /html/
---

## Skjellettet til en nettside

HTML (HyperText Markup Language) er den fundamentale byggeklossen til en
nettside.

Det er i HTML at vi definerer strukturen som nettsiden skal ha, og det meste av
det tekstlige innholdet.

I denne delen skal vi gå gjennom noen av de viktigste HTML-konseptene, og komme
i gang med noen praktiske oppgaver for å få øvd litt på hvordan man lager en
nettside.

### Innhold

- [Elementer](#elementer)
- [Tekst-elementer](#tekst-elementer)
  - [Oppgave 1](#oppgave-1)
- [Avanserte elementer](#avanserte-elementer)
- [Lister](#lister)
  - [Oppgave 2](#oppgave-2)
- [Tabeller](#tabeller)
  - [Oppgave 3](#oppgave-3)
- [Input](#input)
  - [Oppgave 4](#oppgave-4)
- [Attributter](#attributter)
  - [Oppgave 5](#oppgave-5)
  - [Oppgave 6](#oppgave-6)
  - [Oppgave 7](#oppgave-7)
- [Oppsummering](#oppsummering)

### Elementer {#elementer}

#### Tekst-elementer {#tekst-elementer}

HTML består av et hierarki av ulike tagger (eller elementer), som ser slik ut:

`<div>Hei på deg!</div>`

Vi har et navn på elementet (`div`), som forteller hvilket type element det er,
og de kommer (nesten) alltid som et par: en åpne-tag (`<div>`), og en lukke-tag
(`</div>`). Innholdet finner vi mellom disse 2 taggene: `Hei på deg!`. Det går
an å nøste disse taggene, for å lage mer kompliserte strukturer:

```html
<div>
  Jeg er det ytterste elementet.
  <div>Mens jeg er det innerste elementet.</div>
</div>
```

Merk at vi må alltid lukke taggene våre. Det er god kutyme å bruke indentering
når vi skriver HTML-dokumentet, slik at det er lett å se hvordan strukturen er
lagt opp. Ofte kan vi gjøre store endringer med mellomrom og linjeskift, uten at
det påvirker hvordan nettsiden ender opp med å se ut - så man bruker dette for å
gjøre HTML-filen så lett å lese som mulig.

Ofte får vi hjelp fra verktøyene våre (notepad, CodePen, Visual Studio Code,
etc) til å lage denne indenteringen automatisk, så vi slipper å legge inn alle
mellomrom selv. Det er vanlig å bruke 2 eller 4 mellomrom (eventuelt
tab-karakteren), men er helt opp til deg hvordan du ønsker å gjøre det.

Vi bør alltid starte HTML-dokumentet vårt med en `<html>`-tag, som omfatter hele
siden:

```html
<html>
  <div>Her kommer innholdet.</div>
  Men innholdet trenger ikke være i en div-tag
</html>
```

Ofte legger man innholdet inne i en `<body>`-tag, og har en egen `<head>`-tag
for all metadata (som tittelen), som skal være del av nettsiden. (Med tittel, så
mener vi den lille teksten som dukker opp i fanen på toppen av nettleseren).

Eksempel:

```html
<html>
  <head>
    <title>Min fantastiske nettside</title>
  </head>
  <body>
    Her er den kjempekule nettsiden min.
    <div>Her er noe kult innhold, i en div.</div>
  </body>
</html>
```

Men vi ønsker gjerne å gi litt mer liv til nettsiden vår, slik at den er lettere
å lese, og er litt mer nyttig.

Vi kan for eksempel si gi en overskrift med de forskjellige `h`-elementene:
`<h1>`, `<h2>`, `<h3>`, ..., `<h6>`. Disse definerer overskrifter, som har litt
større tekst, og er litt mer synlige.

Vi kan bruke `<p>`-tagger for å angi paragrafer, som gir oss litt mer mellomrom
i teksten vår.

Vi kan også gjøre skriften vår **fet**: `<b>`, eller _kursiv_: `<i>`, eller med
<u>understrek</u>: `<u>`

Linjeskift kan være nyttig, da du sikkert har lagt merke til at nettleseren
ignorerer store deler av mellomrommene og linjeskiftene vi legger til i vår
HTML-fil. Dette er en spesiell tag, som ikke trenger å lukkes: `<br>`

Vil også nevne kommentarer: `<!-- -->` - disse lar oss skrive tekst inn i
HTML-dokumentet, uten at det blir en del av nettsiden. Dette kan være nyttig for
å kommentere hva som skjer i HTML-koden, slik at det er lettere for noen andre å
forstå.

Brukes slik:

```html
<div>
  <p>Denne paragrafen er synlig</p>
  <!-- <p>Denne paragrafen er usynlig</p> -->

  <!-- Et eksempel på hvordan du bruker linjeskift: -->
  Her har vi en hel del tekst. Men selv om vi bruker linjeskift i teksten, så
  kommer ikke det frem på nettsiden, det blir bare en lang linje.
  <br />
  Med mindre vi legger til et linjeskift!
</div>
```

---

<article class="oppgave">
    <h4 id="oppgave-1">Oppgave 1</h4>

    <p><em>Lag en enkel nettside, med disse forskjellige elementene over, som har noe tekstlig innhold og en tittel.</em></p>

    <ul>
      <li>Forsøk å bruke alle de forskjellige elementene, for å se hvordan de endrer på teksten du legger til.</li>
      <li>Hva skjer når du endrer på måten ting er nøstet på?</li>
      <li>Det er veldig viktig at man er <em>eksakt</em>, og skriver taggene nøyaktig slik de er definert. Husk også å lukke de!</li>
      <li><code class="language-plaintext highlighter-rouge">&lt;div&gt;</code>-taggen er en generisk tag for å samle innhold, og kan være nyttig for å dele opp innholdet på en fornuftig måte.</li>
    </ul>

</article>

---

### Avanserte elementer {#avanserte-elementer}

#### Lister {#lister}

Det finnes en hel bråte av elementer man kan legge til nettsiden sin, og noen
har mer avansert funksjonalitet enn å bare endre på hvordan teksten ser ut.
Disse elementene består gjerne av flere forskjellige typer elementer, som man
bruker samtidig.

Vi kan legge til lister, med en kombinasjon av `<ul>`- og `<li>`-taggene:

```html
<ul>
  <li>Gandalf</li>
  <li>Frodo</li>
  <li>Aragorn</li>
  <li>Gimli</li>
</ul>
```

Vi kan også ha nummererte lister, dersom rekkefølgen er viktig, med `<ol>`- og
`<li>`-taggene:

```html
<ol>
  <li>Liverpool</li>
  <li>Manchester City</li>
  <li>Arsenal</li>
  <li>Aston Villa</li>
</ol>
```

---

<article class="oppgave">
    <h4 id="oppgave-2">Oppgave 2</h4>

    <p><em>Lag noen lister på nettsiden din, både med og uten nummerering.</em></p>

    <ul>
      <li>Ikke glem å være nøye med indenteringen! Det gjør ting mer lesbart</li>
    </ul>

</article>

---

#### Tabeller {#tabeller}

Tabeller er ofte nyttige for å strukturere og presentere innholdet, spesielt om
man har data som kan representeres med rader og kolonner.

De er litt mer finurlige, men defineres slik:

```html
<!-- table-taggen definerer at her starter tabellen vår -->
<table>
  <!-- thead-taggen forteller oss at dette skal være headeren på tabellen -->
  <thead>
    <!-- tr-taggen forteller at dette skal være en rad i tabellen -->
    <tr>
      <!-- th-taggen representerer en kolonne i tabellen -->
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>

  <!-- tbody-taggen forteller oss at dette skal være selve innholdet i tabellen -->
  <tbody>
    <!-- første rad -->
    <tr>
      <!-- td-taggen representerer en enkel celle i tabellen -->
      <!-- merk at det bør være like mange td-elementer som vi hadde th-tagger i headeren -->
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <!-- andre rad -->
    <tr>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <!-- osv osv -->
  </tbody>
</table>
```

Et eksempel med litt innhold:

```html
<table border="1">
  <thead>
    <tr>
      <th>Film</th>
      <th>År</th>
      <th>Regissør</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Star Wars</td>
      <td>1977</td>
      <td>George Lucas</td>
    </tr>
    <tr>
      <td>Jurassic Park</td>
      <td>1993</td>
      <td>Steven Spielberg</td>
    </tr>
  </tbody>
</table>
```

Dette blir fort veldig avansert, så det er viktig at man bruker indentering, for
å gjøre det så lett-leselig som mulig.

Merk denne `border="1"`-greia vi la til - dette er en attributt, som vi skal
snakke litt nærmere om seinere i workshopen, vi legger den til her for å gjøre
tabellen vår litt mer synlig.

---

<article class="oppgave">
    <h4 id="oppgave-3">Oppgave 3</h4>

    <p><em>Legg til en enkel tabell på nettsiden din</em></p>

    <ul>
      <li>Vær obs på strukturen! Det er et samspill mellom <code class="language-plaintext highlighter-rouge">&lt;table&gt;</code>, <code class="language-plaintext highlighter-rouge">&lt;thead</code>, <code class="language-plaintext highlighter-rouge">&lt;tbody&gt;</code>, <code class="language-plaintext highlighter-rouge">&lt;tr&gt;</code>, <code class="language-plaintext highlighter-rouge">&lt;th&gt;</code>, og <code class="language-plaintext highlighter-rouge">&lt;td&gt;</code> - så det kan lett gå i surr, og det er viktig at man lukker de riktig.</li>
    </ul>

</article>

---

#### Input {#input}

Nettsider lar oss gjerne gjøre litt mer enn å bare se på innhold, for eksempel
kan man legge til en kommentar, eller logge inn. Da finnes det litt mer
avanserte elementer vi kan benytte for å la brukeren gjøre slike handlinger.

Litt senere, når vi kommer til JavaScript-delen, skal vi se på hvordan vi kan
bruke disse elementene til å gi oppførsel til siden vår.

Ofte ønsker man at de som bruker nettsiden skal kunne legge inn noe tekst, for
eksempel om de skal logge inn med brukernavn og passord, eller legge til en
kommentar.

`<input>`-elementet gir oss en enkel tekstboks som brukeren kan skrive i. Merk
at dette også er et sånt spesielt element, som man ikke trenger å lukke.

```html
<div>
  Brukernavn:
  <input />
  Passord:
  <input />
</div>
```

Dersom man ønsker at bruker skal kunne skrive litt lengre tekster med
linjeskift, for eksempel en kommentar på en post, kan man bruke
`<textarea>`-elementet:

```html
<div>
  Kommentar:
  <textarea> </textarea>
  <!-- merk at denne må man lukke -->
</div>
```

Vi kan bruke `<button>`-elementet for å lage knapper på nettsiden vår:

```html
<div>
  Kommentar:
  <textarea> </textarea>
  <button>Legg til kommentar</button>
</div>
```

---

<article class="oppgave">
    <h4 id="oppgave-4">Oppgave 4</h4>

    <p><em>Legg til noen tekstfelt og knapper til nettsiden din</em></p>

    <ul>
      <li>Vi kommer seinere til å gå inn på hvordan vi kan få disse til å både se litt bedre ut, og ha faktisk oppførsel, i CSS- og JavaScript-delene</li>
    </ul>

</article>

---

### Attributter {#attributter}

Et veldig viktig konsept som vi må være innom, og som blir veldig relevant for
CSS- og JavaScript-delene, er dette med attributter på HTML-elementene våre.

Attributter er ekstra konfigurering og informasjon vi kan gi til elementene
våre, for å spisse de litt mer.

Dette er noe man legger til inne i selve taggen, og er separat fra innholdet:

```html
<div id="div-1-id">Innhold</div>
```

Merk at man ikke trenger å legge de til i lukke-taggen, og det er viktig at man
starter og slutter attributten med `"`.

`<input>`-elementet er et eksempel på en tag som kan endres ganske mye basert på
hvilke attributter vi gir den.

Vi kan bruke `type="checkbox"` for å lage en checkbox der man kan velge ja /
nei:

```html
<div>
  <h3>Velg topping til pizza:</h3>
  <input type="checkbox" /> Ost <br />
  <input type="checkbox" /> Tomatsaus <br />
  <input type="checkbox" /> Pepperoni <br />
  <input type="checkbox" /> Løk <br />
  <input type="checkbox" /> Ananas <br />
</div>
```

Vi kan bruke `type="number"` for å gjøre det om til et tekstfelt man bare kan
legge til tall i:

```html
<div>
  <label>Antall pizzaer å bestille:</label> <br />
  <input type="number" />
</div>
```

Som default får `<input>`-elementet verdien `type="text"`, men man kan ha flere
attributter samtidig, for eksempel om vi ønsker å begrense hvor mange tegn
brukeren skal kunne skrive inn, og også ha en placeholder tekst:

```html
<div>
  <label>Brukernavn:</label> <br />
  <input type="text" maxlength="20" placeholder="Angi brukernavn..." />

  <br />
  <!-- merk at det er lov ha attributter over flere linjer, som kan gjøre det lettere å lese: -->
  <label>Passord:</label> <br />
  <input
    type="password"
    minlength="8"
    maxlength="50"
    placeholder="Angi passord..."
  />
</div>
```

---

<article class="oppgave">
    <h4 id="oppgave-5">Oppgave 5</h4>

    <p><em>Bruk attributter for å legge til noen mer avanserte <code class="language-plaintext highlighter-rouge">&lt;input&gt;</code>-elementer på nettsiden din</em></p>

    <ul>
      <li>Det finnes mange gyldige <code class="language-plaintext highlighter-rouge">type</code>-attributter for <code class="language-plaintext highlighter-rouge">&lt;input&gt;</code> som f.eks <code class="language-plaintext highlighter-rouge">color</code>, <code class="language-plaintext highlighter-rouge">date</code>, <code class="language-plaintext highlighter-rouge">search</code>, <code class="language-plaintext highlighter-rouge">radio</code>, <code class="language-plaintext highlighter-rouge">file</code> - Eksperimenter gjerne med disse, og legg merke til hvor mye form og funksjon blir påvirket av å endre dette attributtet</li>
    </ul>

</article>

---

<br/>

Attributter er svært viktige for lenker, for eksempel, da det er der vi angir
hvilken adresse lenken skal peke på. Lenker defineres med `<a>`-taggen i HTML,
og må ta en `href`-attributt.

```html
<div>
  <a href="https://www.nrk.no/">NRK.no</a>
  <br />
  <!-- Denne magiske target-attributten vil automatisk åpne lenken i en ny fane i nettleseren -->
  <a href="https://www.google.com/" target="_blank">Google</a>
</div>
```

Nettsider består gjerne også av mange forskjellige lenker, som peker på
forskjellige sider inne på den samme nettsiden, eller til sider som finnes på
helt andre adresser, andre steder på nett. I denne workshopen skal vi bare
fokusere på én enkel nettside, uten lenker til andre sider av samme nettside.

---

<article class="oppgave">
    <h4 id="oppgave-6">Oppgave 6</h4>

    <p><em>Legg til noen lenker til forskjellige nettsider inne på siden din</em></p>

    <ul>
      <li>Merk at på CodePen får man ofte ikke åpne disse sidene, med mindre man åpner de i en ny fane</li>
    </ul>

</article>

---

<br/>
Et annet element som er veldig avhengig av attributter, er `<img>`-taggen, som lar oss legge til bilder på nettsiden.

Denne taggen har en `src`-attributt, hvor vi legger stien / adressen til bildet.

```html
<div>
  Et tilfeldig bilde
  <br />
  <img src="https://picsum.photos/200" />
</div>
```

Merk at det er ikke alltid man får lov til å vise slike bilder direkte fra en
annen side, da de som eier den andre nettsiden har mulighet for å stenge for
dette. Det går an å vise til et bilde som ligger sammen med HTML-filen:

```html
<div>
  Et utvalgt bilde
  <br />
  <img src="bildet-mitt.jpg" />
</div>
```

Dette forutsetter at i samme mappe (lokalt på din maskin), så ligger det en
bilde-fil (.jpg, .png, etc) ved siden av HTML-filen.

---

<article class="oppgave">
    <h4 id="oppgave-7">Oppgave 7</h4>

    <p><em>Legg til et bilde på nettsiden din</em></p>

    <ul>
      <li>Du kan finne et bilde på nett, og enten legge til adressen direkte til bildet - men det er ikke alltid man får lov</li>
      <li>Kan også laste ned et bilde lokalt, og vise til stien direkte (men forutsetter at man ikke bruker CodePen)</li>
      <li>Det finnes noen sider som lar deg hente slike bilder gratis: <a href="https://picsum.photos">https://picsum.photos</a>, <a href="https://placekitten.com/">https://placekitten.com/</a></li>
    </ul>

</article>

---

### Oppsummering {#oppsummering}

- HTML-sider har en struktur, som består av tagger og tekst
- Disse taggene angir hvilket type innhold og hvilken struktur siden skal ha
- Det finnes et mangfold av ulike typer elementer
- Man kan bruke attributter på elementene for å gi de litt mer avansert
  funksjonalitet

### Videre

Det finnes veldig mye mer man kan gjøre i ren HTML, og veldig mange andre
elementer og attributter vi ikke har snakket om.

Her er liste over alle de forskjellige elementene som er definert i
HTML-standarden:
[HTML elements reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

Det finnes veldig mye der ute som man kan utforske, og en moderne nettside kan
være veldig avansert!

{% include next-section.html url="css" %}
