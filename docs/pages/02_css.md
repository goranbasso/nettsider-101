---
layout: page
title: CSS
permalink: /css/
---

## Klærne til en nettside

CSS, eller Cascading Style Sheets, er teknologien som lar oss gi nettsidene våre
et unikt utseende ved å la oss endre på tekster, former og farger. Uten CSS
ville det å surfe nettet vært en ganske kjedelig affære.

Visste du at CSS ble
[oppfunnet av en nordmann](https://medium.com/net-magazine/interview-with-h%C3%A5kon-wium-lie-f3328aeca8ed)?!

Håkon Wium Lie var en av pionere innen utviklingen av moderne nettlesere. Da de
første nettleserne ble lansert, fantes det ingen måte å endre hvordan
HTML-elementer så ut. Man måtte bare akseptere det nettleseren gav. Det var ofte
litt grått og trist. Håkon Lie innså at dersom folk flest skulle ha interesse av
å lese innholdet som fantes på nettet, måtte de kunne designes på en måte som
var appelerende for folk flest, slik man hadde gjort med trykte medier som
aviser, blader og bøker.

For å sitere oppfinneren selv:

> “If we hadn’t developed CSS, we could have ended up with the web being a giant
> fax machine”

Et begrep som ofte brukes når vi snakker om CSS er å "stile elementer", altså å
gi elementer et utseende. "Elementer" er byggeblokkene i HTML, som vi beskrev i
forrige seksjon av kurset. Vi kommer til å bruke begrepet "å stile" i de
kommende seksjonene når vi snakker om å endre utseendet til HTML med CSS.

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

---

#### Oppgave 1

_Lek litt rundt med de forskjellige egenskapene og verdiene i eksemplet over -
klarer du å få den til å bli rød, hvit, og blå?_

- Merk: `color` endrer fargen på _teksten_, mens `background` endrer fargen på
  bakgrunnen

---

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

---

#### Oppgave 2

_Definer flere klasser, og bruk de på flere forskjellige elementer_

- Du angir hvilken klasse et element skal ha ved å bruke `class`-attributten:
  `<div class="jeg-er-en-klasse">`
- Hva skjer om du bruker flere klasser på samme element?

---

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

---

#### Oppgave 3

_Lag en nettside (eller bruk det du lagde på oppgave 4 og 5 fra HTML-delen) der
du bruker denne element-selektoren for å gjøre knappene og tekstfeltene litt
penere_

---

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
**G**rønn og **B**lå), HSL (**H**ue, **S**aturation, **L**ightness) eller
kodeord som f.eks `black`, `hotpink` og `papayawhip` (ja, det er faktisk en
gyldig fargeverdi).

```css
/* Alle fargeverdiene her er like */
.color-me-red {
  color: #ff0000; /* hex */
  color: rgb(255, 0, 0);
  color: hsl(0, 100%, 50%);
  color: red;
}
```

[Det finnes mange flere måter ](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value)
å definere farger på, alle med sine fordeler og ulemper. For enkelhets skyld
holder vi oss til kodeord ("red", "green") og hex-verdier i dette kurset, men du
står selvfølgelig fritt til å teste ut det andre metodene 🎨

---

#### Oppgave 4

_Bruk det du har lært om klasser og farger til å lage en regnbue 🌈_

- Dersom du lager tomme elementer, uten innhold, kan det være lurt å gi de en
  størrelse, slik at de er synlige:

```
width: 40px;
height: 40px;
```

- I neste del skal vi gå litt nærmere inn på hvordan størrelser fungerer

---

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
`50vw` kan eksempelvis leses som "50% of viewport width", eller på godt norsk
"halvparten av bredden til nettleservinduet"

---

#### Oppgave 5

_Lag noen elementer og klasser, og bruk alle disse forskjellige
størrelse-enhetene (`px`, `em`, `rem`, `vw`, `vw`, og `%`) - klarer du å få alle
til å bli like store?_

---

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
`inline`, `none`, `flex` og `grid`. Vi skal ikke gå i detalj på hva alle allle
mulige nøkkelord betyr, men en forenklet forklaring av de nevnte verdiene kan
være:

- `block`: elementet er en "blokk" som tar full bredde dersom ingen bredde
  (`width`) er definert. Et `block`-element havner som regel på en egen linje,
  dvs. at man i utgangspunktet ikke kan ha to `block`-elementer ved siden av
  hverandre, men det finnes måter å endre dette på. Vi kan kontrollere høyden på
  `block`-elementer ved å bruke egenskaper som `height`, `max-height` og
  `min-height`. Mange elementer har `display: block;` som standard f.eks
  `<div>`, `<p>`, `<section>`. `<article>` osv.
- `inline`: elementet kan stilles på linje og tar bare opp bredden til innholdet
  (godt egnet til å putte inn i tekst). Vi kan ikke kontrollere høyden på
  `inline`-elementer slik som vi kan med `block`-elementer. `<span>`-elementet
  er et eksempel på et element som har `display: inline;` som standard.
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

### Boksmodellen, flyt og layout

En ting man ofte jobber mye med i CSS er størrelsen på elementer og hvordan de
posisjonerer seg i forhold til hverandre. I denne seksjonen skal vi snakke om
noen av konseptene som er nyttige å forstå for å kontrollere dette.

#### Boksmodellen

Hvert element i HTML kan sees på som en boks. Denne boksen har forskjellige
CSS-egenskaper som sammen utgjør størrelsen til boksen. I CSS blir dette ofte
omtalt som boksmodellen (box model).

<!-- <p class="center-content"> -->
  <img src="{{ site.baseurl }}/assets/img/boxmodel.png" alt="Bildet viser boksmodellen i css" />
<!-- </p> -->

<aside>
<div>
  Egenskapene <code>margin</code> og <code>padding</code> kan settes for alle
  sidene samtidig, og følger da rekkefølgen "topp", "høyre", "bunn" og "venstre":
</div>
<br />
<div>
<code>margin: 10px 2px 5px 8px</code>
</div>
<br />
<div>
  betyr henholdsvis: 10px luft over, 2px luft til høyre, 5px luft under og 8px
  luft til venstre for elementet. Men man kan også sette verdiene for én side om
  gangen ved å bruke <code>margin-top</code>, <code>margin-right</code>,
  <code>margin-bottom</code> og <code>margin-left</code>.
</div>

</aside>

- I midten finner vi innholdet (content), som kan være tekst eller andre
  elementer
- Utenfor innholdet har vi `padding` som er luften mellom innholdet og kanten på
  boksen.
- Kanten på boksen (`border`) kan enten være usynlig eller ha en definert
  tykkelse, stil og farge (f.eks `border: 4px solid green;`)
- Utenfor boksen har vi enda en egenskap som styrer mellomrommet til andre
  elementer. Denne egenskapen kalles `margin`.

Kombinasjonen av innholdet i boksen og de nevnte egenskapene bestemmer boksen
sin naturlige størrelse. Men vi har også mulighet til overstyre den naturlige
størrelsen ved å sette størrelses-verdier på egenskapene `width` og `height`. Vi
kan også kontrollere minimum- og maksimumsstørrelser med
`min-width`/`min-height` og `max-width`/`max-height`, det vil si at elementet
ikke kan bli mindre eller større enn disse verdiene.

En ting som er viktig å vite om `height` og `width` er at vi kan kontrollere
hvordan nettleseren gjør denne beregningen ved å sette egenskapen `box-sizing`.
Den kan ha 2 verdier

- `box-sizing: content-box`: høyde/bredde er bare beregnet utifra størrelsen til
  innholdet. `padding` og `border` blir ikke tatt med i beregningen.
- `box-sizing: border-box`: høyde/bredde er kombinasjonen av innholdet,
  `padding` og `border`.

Merkelig nok er standarden for alle nettlesere å sette
`box-sizing: content-box`. Dette er ganske forrvirrende, det blir som å si at
dersom man får en pakke i posten, så er størrelsen på pakken kun det som er inni
pakken. Og som vi vet, stemmer dette sjeldent.

<img src="{{site.baseurl}}/assets/img/bigbox.png" alt="Stor eske, lite innhold" style="max-width: 500px" />

Det er derfor vanlig at man i begynnelsen av stilarket setter

```css
* {
  box-sizing: border-box;
}
```

For endre `box-sizing` for alle elementer på nettsiden.

Eksempelet under viser hvordan ting kan endre seg når man endrer på forskjellige
`box-sizing`-verdier.

{% include codepen-embed.html slug="BaEQWWR" height="810" default_tab="result" %}

---

#### Oppgave 6

_Se om du klarer å få det indre elementet (blå boks med klassen `child`) til å
bli like stort som det ytre elementet ved å endre egenskapene som påvirker høyde
og bredde_

- Vi har satt `box-sizing: border-box;` for alle elementer i eksempelet
- Trykk på knappen som sier "Sjekk størrelsen til barnet" etter du har gjort en
  endring for å se hvilke størrelse "barnet" faktisk har (høyde x bredde)

{% include codepen-embed.html slug="ExJNxqG" height="700" %}

---

#### Flexbox

Layouten til en nettside blir gjerne litt mer spennende om man posisjonerer
elementene på en bedre måte enn å bare ha de nedover, som en liste. Dette kan vi
oppnå ved å bruke flexbox eller grid.

Med flexbox, så definerer vi elementene våre som bokser og sier hvor de skal
være i forhold til hverandre, ved å se for oss at vi har en retning (enten
vertikalt eller horisontalt), og så hvor stor plass de indre elementene skal ta
i forhold til hverandre.

{% include codepen-embed.html slug="yLrVbqN" height="500" %}

Først setter vi denne `display`-egenskapen til `flex`, og så bruker vi
`justify-content` til å fortelle hvor mye avstand det skal være mellom de
forskjellige elementene i boksen. I eksemplet over ser man hvordan
`space-between`, `space-around`, `space-evenly`, og `center` oppfører seg
annerledes.

Legg merke til `flex-direction: row-reverse` på den grønne raden - som gjør at
rekkefølgen blir reversert, og at den ytterste (`<div class="outer-box">`) har
`flex-direction: column`, som sier at retningen vår er vertikal, som en søyle.
De andre trenger vi ikke definere `flex-direction: row` på, siden det er det som
er default.

#### Grid

Et annet verktøy vi har for å endre på layouten er grid, som ser for seg at
elementene ligger som en tabell, med rader og kolonner.

{% include codepen-embed.html slug="XWQNgJR" height="500" %}

I eksemplet over, så ser vi hvordan vi først har definert en wrapper-boks, der
vi sier `display: grid`, og forteller at vi ønsker å ha 3 kolonner, med denne
`grid-template-columns: repeat(3, 1fr)`, og at radene skal ha en størrelse på 50
piksler, med `grid-auto-rows: minmax(50px, auto)`, som gjør at det automatisk
har blitt 4 rader.

I tillegg har vi sagt at det skal være et gap på 10 piksler mellom hver celle
(`gap: 10px`).

Deretter definerer vi egne klasser for hver celle, og vi ser hvordan vi kan
endre hvor stor plass de tar i tabellen, ved å sette verdier for disse
`grid-column` og `grid-cell`.

For eksempel, for celle E, har vi sagt at den skal være i kolonne 2, og rad 4:

```css
.cell-e {
  grid-column: 2;
  grid-row: 4;
}
```

Mens for celle B, har vi sagt at den skal strekke seg over kolonnene 2 og 3, og
over radene 1 og 2:

```css
.cell-b {
  grid-column: 2 / 4;
  grid-row: 1 / 3;
}
```

Med denne `2 / 4`-verdien, sier vi egentlig 'fra og med 2, til (men ikke med)
4'. Merk også at celle A og celle B overlapper i første rad på kolonne 2.

Dette er bare et enkelt eksempel på hvordan du kan bruke grid, men det er mye
mer som er mulig å få til. Denne nettsiden har en grei oversikt, og kan være
verdt å ta en kjapp titt på:
[CSS Tricks: Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)

---

#### Oppgave 7

_Ved å bruke enten flexbox eller grid (opp til deg), lag et sjakkbrett_

- Bonus om sjakkbrettet også har koordinatene på siden (A, B, C, etc; 1, 2,
  3...)

---

### Oppsummering

- CSS lar oss stile elementer på nettsiden vår, slik at de ser litt bedre ut
- Man setter regler for CSS-en ved å angi en selektor, en egenskap, og en verdi
- Man kan sette flere regler på samme element - spesifisiteten avgjør hvilken
  som blir gjeldende, dersom det er en konflikt
- Boksmodellen deler elementer inn i deler: margin, border, padding, og content

## Ressurser

[Mozilla CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)

{% include next-section.html url="javascript" %}
