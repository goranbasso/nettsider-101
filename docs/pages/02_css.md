---
layout: page
title: CSS
permalink: /css/
---

## Klærne til en nettside

Her trenger jeg en intro...

Visste du at CSS ble
[oppfunnet av en nordmann](https://medium.com/net-magazine/interview-with-h%C3%A5kon-wium-lie-f3328aeca8ed)?!

Og for å sitere oppfinneren selv:

> “If we hadn’t developed CSS, we could have ended up with the web being a giant
> fax machine”

Et begrep som ofte brukes når vi snakker om CSS er å "stile elementer", altså å
gi elementer et utseende. "Elementer" er byggeblokkene i HTML, som vi beskrev i
forrige seksjon av kurset. Vi kommer til å bruke begrepet "å stile" i de
kommende seksjonene.

Stilene vi definerer for en nettside kan være i 1 eller flere "stilark". Et
stilark er en fil med endingen `.css` som følger språkkonvensjonene for CSS.
Disse konvensjonene skal vi beskrive i de kommende avsnittene.

I denne seksjonen vil vi bruke en rekke kodeeksempler som er "live". Med "live"
mener vi at du kan endre på koden og i eksempelet, og raskt se hvilken effekt
det har. Vi anbefaler at du eksperimenterer med disse eksemplene. Test ut å
endre på CSS eller HTML for å se hva som skjer! Det er ingen fare for at du
ødelegger noe, dersom du laster siden på nytt vil eksemplene gå tilbake til slik
de var før du begynte å gjøre endringer😉

Disse eksemplene bruker tjenesten Codepen. Oppe i høyre hjørne av eksemplene ser
de en lenke hvor det står "Fork on Codepen". Dersom du trykker denne lenken kan
du lage din egen kopi av eksempelet på Codepen, hvor du står enda mer fritt til
å eksperimentere. Merk at du er nødt til å opprette en bruker på Codepen dersom
du har lyst til å lagre endringer du gjør

### Anatomien til en CSS-regel

I sin enkleste form består en CSS-regel av 3 ting: en **selektor** (hva skal vi
stile), en **egenskap** (hvilket "utseende" ønsker vi å endre) og en **verdi**
(hvilken endring ønsker vi å gjøre). Dersom vi skulle vise det som pseudo-kode
(altså kode som ikke er gyldig, men som beskriver et konsept) kunne man uttrykt
det slik:

```css
selector {
  egenskap: verdi;
}
```

Kombinasjonen av `egenskap: verdi;` kalles også for en "deklarasjon". Senere
skal vi se at vi kan gruppere mange deklarasjoner i samme CSS-regel.

<aside>
Det som er litt kult (og kanskje forvirrende) er at CSS er veldig tilgivende.
Eksempelet over er ikke gyldig CSS. Det har ingen effekt, men dersom du putter
det i stilarket ditt vil det ikke få nettsiden til å krasje eller se rar ut,
det vil bare bli ignorert. Dette kan være litt betryggende å tenke på. Det verste
som kan skje om du gjør en feil er at "ingenting skjer"😛.
Ulempen er at dersom vi har en skrivefeil et sted i regelen vår, så vil den ikke
ha noen effekt, og det er ingen som skriker til oss om hva som er galt.
</aside>

#### Hva er en "selektor" {#selektor}

En selektor er noe som definerer hva vi ønsker å stile. En selektor har
varierende grad av _spesifisitet_. Det vil si at den kan være veldig generell,
og gjelde for mange elementer samtidig, eller helt spesifikk og bare gjelde for
ett enkelt element. Den mest generelle selektoren er `*` "jokertegnet" (wildcard
på engelsk). Denne selektoren gjelder for alle elementene på en HTML-side! 😈

Den mest spesifikke selektoren er derimot "ID-selektoren" som består av tegnet
`#` (som symboliserer ID-attributtet) og navnet vi har gitt IDen, f.eks
`#jeg-er-en-id`. ID-attributtet er noe alle HTML-elementer kan ha, men regelen
er at en ID må være unik, derfor vet vi at en ID kun gjelder for ett element på
en HTML-side.

{% include codepen-embed.html slug="VwNKPbO" %}

Det at en ID alltid er unik er en sannhet med modifikasjoner. Reglene for HTML
sier at en ID skal være unik for hver side, men nettleserne tolker både CSS og
HTML på en veldig tilgivende måte. Selv om man gjør en feil, prøver nettleseren
alltid å vise noe. Det betyr at dersom 2 eller flere elementer har samme ID, så
vil fortsatt nettleseren vise disse elementene med tilhørende stiling. Det betyr
derimot IKKE at man skal gjøre det, siden det kan skape en rekke andre
problemer. Istedet finnes det et annet attribut som vi kan gi alle
HTML-elementer, hvor verdien kan deles mellom så mange elementer man ønsker,
nemlig `class`.

`class` defineres på lignende måte som `id`-attributtet, men CSS-selektoren for
en klasse bruker `.`-tegnet (punktum)

{% include codepen-embed.html slug="oNOzWXw" %}

På samme nivå av spesifisitet som klasse-selektoren, har vi også
tilstands-selektoren og attributt-selektoren. Tilstands-selektoren er aktiv når
et element er i en spesifikk tilstand. F.eks er `:hover`-selektoren gyldig når
man tar musepekeren over et element ("hover" betyr å sveve på engelsk).
Attribut-selektoren er derimot gyldig når et html element har et spesifikt
attribut. F.eks kan alle HTML-elementer ha et `title`-attribut som kan gi ekstra
informajson om elmentet. Dette kan brukes som en selektor ved å bruke formatet
`[title]`.

{% include codepen-embed.html slug="zYXKeJZ" %}

En mindre spesifikk selektor-type som er også er mye brukt er
"element-selektoren". Element-selektoren består rett og slett av navnet
på HTML-elementet du ønsker å stile:

```css
div {
  /* Regelen gjelder for alle <div>-elementer */
}

p {
  /* Regelen gjelder for alle <p>-elementer (avsnitt) */
}

table {
  /* Regelen gjelder for alle <table>-elementer (tabeller) */
}
```

#### Hva er en "egenskap"

En egenskap er "utseendet" vi ønsker å endre på elementet (eller elementene) vi
har valgt med selektoren. På engelsk kaller man dette en "CSS property". Vi har
allerede sett en del eksempler på css-egenskaper som kan endre ting som
skrifttype, skriftstørrelse, farge, bakgrunn, bredde, høyde, osv.

Legg merke til at vi ikke er begrenset til å sette én enkelt egenskap per
CSS-regel, vi kan gruppere så mange som vi ønsker. Dersom vi skriver den samme
egenskapen flere ganger er det kun den siste som har effekt.

```css
.jeg-har-en-egenskap {
  color: red; /* Forvirrende nok gjelder egenskapen "color" bare fargen på tekst */
}

.jeg-har-mange {
  color: white;
  background-color: red; /* Blir overskrevet av den neste linjen */
  background-color: black;
  border: 5px solid pink;
  padding: 1rem;
}
```

Vi kan tilogmed definere regler med den samme selektoren flere ganger. Da blir
reglene kombinert som om du skulle ha skrevet de i samme regel:

{% include codepen-embed.html slug="LYvRjrZ" %}

Det man ser i effekt her er en viktig del av CSS som kalles "kaskaden" (CSS =
**Cascading** Style Sheets). Kaskaden refererer til arbeidet nettleseren gjør
for å kombinere og prioritere CSS-regler for å bestemme hvilke stiler som
faktisk skal gjelde for en HTML-side.

Senere skal vi se nærmere på hvordan nettleseren gjør denne prioriteringen, og
hva vi kan gjøre for å kontrollere prosessen.

#### Hva er en "verdi"

En verdi tilhører en egenskap. Hvilken verdier man kan bruke avhenger av
egenskapen. De fleste verdier er enten av typen "farge", "størrelse",
"nøkkelord" eller en kombinasjon av disse. Hver verdi-type kan representeres på
mange forskjellige måter.

<!-- <aside>
I praksis kan man gi en egenskap hvilken som helst verdi, men dersom verdien ikke
er gyldig har den heller ikke noen effekt. <code>color: 10px;</code> har f.eks
ingen effekt fordi vi gir en "størrelses-verdi" til en egenskap som forventer en
"farge-verdi"
</aside>

<br /> -->

##### Farge

Farger er oftest representert i heksadesimale verdier (hex), RGB (andel **R**ød,
**G**rønn og **B**lå), HSL(**H**ue, **S**aturation, **L**ightness) eller kodeord
som f.eks "black", "pink", "papayawhip" (ja, det er faktisk en gyldig
fargeverdi).

```css
/* Alle fargeverdiene her er like */
.color-me-red {
  color: #ff0000; /* hex */
  color: rgb(255, 0, 0)
  color: hsl(0, 100%, 50%)
  color: red;
}
```

[Det finnes mange flere måter ](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value)
å definere farger på, alle med sine fordeler og ulemper. For enkelhets skyld
holder vi oss til kodeord ("red", "green") og hex-verdier i dette kurset.

##### Størrelse

Størrelser oppgis som regel i absolutte eller relative verdier.

Absolutte verdier kan f.eks være piksler (`px`), punkter (`pt`), centimeter
(`cm`) eller tommer (`in`). Av disse er piksler (`px`) desidert mest brukt. En
dataskjerm består av tett rutenett av lys som kan ha forskjellige farger. Rutene
med farger er det som lager bildene vi ser på skjermen. Hver av disse rutene
kalles en "piksel" (av engelsk "picture element"). Dersom du går helt nærme
skjermen din vil du mest sannsynlig kunne se de individulle pikslene.

Relative enheter er størrelser som avhenger av størrelsen på andre elementer.
Eksempler på relativer verdier er prosent (`%`), `em`, `rem`, `vw` og `vw`.
Blant disse verdiene er prosent, `rem`, `vw`, `vh` mye brukt.

`rem` er relativ til skriftstørrelsen til rot-elementet i HTML-dokumentet
(<html>-taggen). Som standard er denne på 16 piksler (`px`). Det vil si at
`1rem` = `16px`, `2rem` = `32px` osv.

`vw` og `vh` er størrelser som er relative til bredden og høyden til
nettleser-vinduet (på engelsk "viewport") og kan ha en verdi fra 0 til 100.
`50vw` kan leses som "50% of viewport width", eller på godt norsk "halvparten av
bredden til nettleseren"

##### Nøkkelord

Nøkkelord er kanskje den største og mest komplekse gruppen med verdier i CSS.
Heldigvis trenger man ikke å kunne så veldig mange av dem for å komme i gang.
Ikke engang utviklere med mange års erfaring klarer å huske alle tilgjengelige
nøkkelord-verdier for forskjellige CSS-egenskaper. Derfor er det veldig nyttig å
ha et godt oppslagsverk i nærheten når man jobber med CSS, slik at man enkelt
kan finne ut hvilke nøkkelord som er gyldige for forskjellige CSS-egenskaper. Vi
anbefaler å bruke nettsiden
[Mozilla Developer Network (MDN)](https://developer.mozilla.org/en-US/).

Som et eksempel på en egenskap som bruker nøkkelord har vi `display`. Denne
egenskapen definerer hvordan et element og eventuelle underelementer (barn) skal
posisjonere seg i "flyten" av innhold på en nettside. Dersom vi
[ser på dokumentasjonen på MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
kan vi lese at `display` støtter mange forskjellige nøkkelord som `block`,
`inline` `none`, `flex` og `grid`. Vi skal ikke gå i detalj på hva alle allle
mulige nøkkelord betyr, men en forenklet forklaring av de nevnte verdiene kan
være:

- `block`: elementet er en "blokk" som tar full bredde (mange elementer har
  dette som standard f.eks `<div>`, `<p>`, `<section>`, `<article>` osv.)
- `inline`: elementet kan stilles på linje og tar bare opp bredden til innholdet
  (godt egnet til å putte inn i tekst)
- `none`: elementet er ikke synlig (det er overraskende ofte vi trenger å gjemme
  elementer med CSS)
- `flex`: elementet oppfører seg som `block` men alle barn følger en layout som
  kalles flexbox
- `grid`: elementet oppfører seg som `block` men alle barn følger en layout som
  kalles grid (rutenett)

{% include codepen-embed.html slug="eYodKyz" default_tab="result" height="800" %}

### Selektorer, spesifisitet og "kaskaden"

Som nevnt i [avsnittet om selektorer](#selektor), så har CSS-regler ulik
spesifisitet avhengig av hvilken selektor som brukes. Jo høyere spesifisitet en
selektor har, jo viktigere tenker nettleseren at regelen er. Dersom det er
konflikt mellom to CSS-regler, er det regelen med høyest spesifisitet som
vinner. Dersom to regler har samme spesifisitet, er det regelen som ble skrevet
sist som vinner.

Spesifisiteten til en selektor kan tenkes på som en poengsum, hvor høyeste
poengsum vinner stilings-krigen⚔️:

- ID-selektoren gir 1 **høynivå-poeng**
- Klasse-, tilstand- og attribut-selektorene gir 1 **mellomnivå-poeng**
- Element-selektoren gir 1 **lavnivå-poeng**

Vi har ikke snakket om det enda, men det går an å kombinere flere selektorer for
å øke poengsummen til en CSS-regel. Tenk at vi har det følgende HTML-elementet:

```html
<p
  id="viktig-avsnitt"
  class="kjeks potet"
  title="Dette avsnittet inneholder viktig informasjon"
>
  Husk å spise grønnsaker 🥦
</p>
```

Da kan vi lage 2 selektorer som treffer det samme elementet med forskjellig
poengsum

```css
/* 1 ID-selektor - Poengsum: "1, 0, 0" */
#viktig-avsnitt {
  background-color: red;
}

/* 1 element, 2 klasser, 1 attributt - Poengsum: "0, 3, 1" */
p.kjeks.potet[title] {
  background-color: blue;
}
```

Til tross for at den siste selektoren har samlet 4 poeng, er de poeng av et
lavere nivå enn ID-selektoren. Selektorer av høyere nivå, slår alltid de på
lavere nivå. ID-selektoren blir derfor vinneren i denne krigen, og avsnittet får
rød bakgrunn.

Det er viktig å legge merke til at vi bare får "krig" dersom de to reglene
prøver å endre samme CSS-egenskap (`background-color` i dette tilfellet). Dersom
reglene endrer på forskjellige egenskaper vil det ikke oppstå noen krig, og
reglene vil bli slått sammen.

```css
/* Her får avsnittet både rød bakgrunn og hvit tekst */
#viktig-avsnitt {
  background-color: red;
}

p.kjeks.potet[title] {
  color: white;
}
```

- spesifistets-vekt av selektorer
- kombinasjon av selektorer
- !important
- order matters
- regler arves

### Boksmodellen, flyt og layout

En ting man ofte jobber mye med i CSS er størrelsen på elementer og hvordan de
posisjonerer seg i forhold til hverandre. I denne seksjonen skal vi snakke om
noen av konseptene som er nyttige å forstå for å kontrollere dette.

- Boksmodellen
- Position
- Float
- Flexbox
- Grid

## Ressurser

https://developer.mozilla.org/en-US/docs/Web/CSS/Reference

{% include next-section.html url="javascript" %}
