---
layout: page
title: CSS
permalink: /css/
---

## Klærne til en nettside

Her trenger jeg en intro...

Visste du at CSS ble [oppfunnet av en nordmann](https://medium.com/net-magazine/interview-with-h%C3%A5kon-wium-lie-f3328aeca8ed)?!

Og for å sitere oppfinneren selv:

> “If we hadn’t developed CSS, we could have ended up with the web being a giant fax machine”

Et begrep som ofte brukes når vi snakker om CSS er å "stile elementer", altså å
gi elementer et utseende. "Elementer" er byggeblokkene i HTML, som vi beskrev i
forrige seksjon av kurset. Vi kommer til å bruke begrepet "å stile" i de kommende seksjonene.

Stilene vi definerer for en nettside kan være i 1 eller flere "stilark". Et
stilark er en fil med endingen `.css` som følger språkkonvensjonene for CSS. Disse
konvensjonene skal vi beskrive i de kommende avsnittene.

### Anatomien til en CSS-regel

I sin enkleste form består en CSS-regel av 3 ting: en **selektor** (hva skal vi stile),
en **egenskap** (hvilket "utseende" ønsker vi å endre) og en **verdi** (hvilken endring ønsker vi å gjøre).
Dersom vi skulle vise det som pseudo-kode (altså kode som ikke er gyldig, men som beskriver et konsept)
kunne man uttrykt det slik:

```css
selector {
  egenskap: verdi;
}
```

<aside>
Det som er litt kult (og kanskje forvirrende) er at CSS er veldig tilgivende.
Eksempelet over er ikke gyldig CSS. Det har ingen effekt, men dersom du putter
det i stilarket ditt vil det ikke få nettsiden til å krasje eller se rar ut,
det vil bare bli ignorert. Dette kan være litt betryggende å tenke på. Det verste
som kan skje om du gjør en feil er at "ingenting skjer"😛.
Ulempen er at dersom vi har en skrivefeil et sted i regelen vår, så vil den ikke
ha noen effekt, og det er ingen som skriker til oss om hva som er feil.
</aside>

#### Hva er en "selektor"

En selektor er noe som definerer hva vi ønsker å stile. En selektor har varierende
grad av _spesifisitet_. Det vil si at den kan være veldig generell, og gjelde for
mange elementer samtidig, eller helt spesifikk og bare gjelde for ett enkelt element.
Den mest generelle selektoren er `*` "jokertegnet" (wildcard på engelsk).
Denne selektoren gjelder for alle elementene på en HTML-side! 😈

Den mest spesifikke selektoren er derimot "ID-selektoren" som består av tegnet `#`
(som symboliserer ID-attributtet) og navnet vi har gitt IDen, f.eks `#jeg-er-en-id`.
ID-attributtet er noe alle HTML-elementer kan ha, men regelen er at en ID må være
unik, derfor vet vi at en ID kun gjelder for ett element på en HTML-side.

{% include codepen-embed.html slug="VwNKPbO" %}

Det at en ID alltid er unik er en sannhet med modifikasjoner. Reglene for HTML
sier at en ID skal være unik for hver side, men nettleserne tolker både CSS og HTML
på en veldig tilgivende måte. Selv om man gjør en feil, prøver nettleseren alltid å vise noe.
Det betyr at dersom 2 eller flere elementer har samme ID, så vil fortsatt nettleseren vise
disse elementene med tilhørende stiling. Det betyr derimot IKKE at man skal gjøre
det, siden det kan skape en rekke andre problemer. Istedet finnes det et annet
attribut som vi kan gi alle HTML-elementer, hvor verdien kan deles mellom så mange elementer
man ønsker, nemlig `class`.

`class` defineres på lignende måte som `id`-attributtet, men CSS-selektoren for
en klasse bruker `.`-tegnet (punktum)

{% include codepen-embed.html slug="oNOzWXw" %}

En mindre spesifikk selektor-type som er også er mye brukt er "element-selektoren".
Element-selektoren består rett og slett av navnet på HTML-elementet du ønsker å
stile:

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

En egenskap er "utseendet" vi ønsker å endre på elementet (eller elementene) vi har
valgt med selektoren. På engelsk kaller man dette en "CSS property". Vi har allerede sett en del
eksempler på css-egenskaper som kan endre ting som skrifttype, skriftstørrelse, farge,
bakgrunn, bredde, høyde, osv.

Legg merke til at vi ikke er begrenset til å sette én enkelt egenskap
per CSS-regel, vi kan gruppere så mange som vi ønsker. Dersom vi skriver
den samme egenskapen flere ganger er det kun den siste som har effekt.

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

Det man ser i effekt her er en viktig del av CSS som kalles "kaskaden"
(CSS = **Cascading** Style Sheets). Kaskaden refererer til arbeidet nettleseren
gjør for å kombinere og prioritere CSS-regler for å bestemme hvilke stiler som
faktisk skal gjelde for en HTML-side.

Senere skal vi se nærmere på hvordan nettleseren gjør denne prioriteringen, og hva vi kan gjøre for å kontrollere prosessen.

#### Hva er en "verdi"

En verdi tilhører en egenskap. Hvilken verdier man kan bruke avhenger av egenskapen.
De fleste verdier er enten av typen "farge", "størrelse", "nøkkelord" eller en kombinasjon av disse.
Hver verdi-type kan representeres på mange forskjellige måter.

<!-- <aside>
I praksis kan man gi en egenskap hvilken som helst verdi, men dersom verdien ikke
er gyldig har den heller ikke noen effekt. <code>color: 10px;</code> har f.eks
ingen effekt fordi vi gir en "størrelses-verdi" til en egenskap som forventer en
"farge-verdi"
</aside>

<br /> -->

##### Farge

Farger er oftest representert i heksadesimale verdier (hex),
RGB (andel **R**ød, **G**rønn og **B**lå), HSL(**H**ue, **S**aturation, **L**ightness)
eller kodeord som f.eks "black", "pink", "ochre".

```css
/* Alle fargeverdiene her er like */
.color-me-red {
  color: #ff0000; /* hex */
  color: rgb(255, 0, 0)
  color: hsl(0, 100%, 50%)
  color: red;
}
```

[Det finnes mange flere måter ](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) å definere farger på, alle med sine fordeler og
ulemper. For enkelhets skyld holder vi oss til kodeord ("red", "green") og
hex-verdier i dette kurset.

##### Størrelse

Størrelser oppgis som regel i absolutte eller relative verdier.

Absolutte verdier kan f.eks være piksler (`px`), punkter (`pt`), centimeter (`cm`) eller tommer (`in`).
Av disse er piksler (`px`) desidert mest brukt. En dataskjerm består av tett rutenett av
lys som kan ha forskjellige farger. Rutene med farger er det som lager bildene vi
ser på skjermen. Hver av disse rutene kalles en "piksel" (av engelsk "picture element").
Dersom du går helt nærme skjermen din vil du mest sannsynlig kunne se de individulle pikslene.

Relative enheter er størrelser som avhenger av størrelsen på andre elementer.
Eksempler på relativer verdier er prosent (`%`), `em`, `rem`, `vw` og `vw`.
Blant disse verdiene er prosent, `rem`, `vw`, `vh` mye brukt.

`rem` er relativ til skriftstørrelsen til rot-elementet i HTML-dokumentet (<html>-taggen).
Som standard er denne på 16 piksler (`px`). Det vil si at `1rem` = `16px`,
`2rem` = `32px` osv.

`vw` og `vh` er størrelser som er relative til bredden og høyden til
nettleser-vinduet (på engelsk "viewport") og kan ha en verdi fra 0 til 100.
`50vw` kan leses som "50% of viewport width", eller på godt norsk "halvparten
av bredden til nettleseren"

##### Nøkkelord

Nøkkelord er kanskje den største og mest komplekse gruppen med verdier i CSS.
Heldigvis trenger man ikke å kunne så veldig mange av dem for å komme i gang.
Ikke engang utviklere med mange års erfaring klarer å huske alle tilgjengelige
nøkkelord-verdier for forskjellige CSS-egenskaper. Derfor er det veldig nyttig
å ha et godt oppslagsverk i nærheten når man jobber med CSS, slik at man enkelt
kan finne ut hvilke nøkkelord som er gyldige for forskjellige CSS-egenskaper.
Vi anbefaler å bruke nettsiden [Mozilla Developer Network (MDN)](https://developer.mozilla.org/en-US/).

Som et eksempel på en egenskap som bruker nøkkelord har vi `display`. Denne
egenskapen definerer hvordan et element og eventuelle underelementer (barn) skal vises.
Dersom vi [ser på dokumentasjonen på MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
kan vi lese at `display` støtter mange forskjellige nøkkelord som `block`, `inline`
`none`, `flex` og `grid`. Vi skal ikke gå i detalj på alle de mulige nøkkelordene,
men en forenklet forklaring av de nevnte verdiene kan være:

- `block`: elementet er en "blokk" som tar full bredde (mange elementer har dette
  som standard f.eks `<div>`, `<p>`, `<section>`, `<article>` osv.)
- `inline`: elementet kan stilles på linje og tar bare opp bredden til innholdet (godt egnet til å putte inn i tekst)
- `none`: elementet er ikke synlig (det er overraskende ofte vi trenger å gjemme elementer med CSS)
- `flex`: elementet oppfører seg som `block` men alle barn følger en layout som kalles flexbox
- `grid`: elementet oppfører seg som `block` men alle barn følger en layout som kalles grid (rutenett)

{% include codepen-embed.html slug="eYodKyz" default_tab="result" height="800" %}

### Selektorer, spesifisitet og "kaskaden"

- spesifistets-vekt av selektorer
- kombinasjon av selektorer
- !important
- order matters
- regler arves

### Arv?

### Boksmodellen

- Struktur
- Farger
- Boksmodellen
- Posisjonering
- Hvordan bruke HTML og CSS sammen

### Layout

- Flexbox
- Grid

## Ressurser

https://developer.mozilla.org/en-US/docs/Web/CSS/Reference

{% include next-section.html url="javascript" %}
