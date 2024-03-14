---
layout: page
title: CSS
permalink: /css/
---

## Klærne til en nettside

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
en **egenskap** (hvilken "utseende" ønsker vi å endre) og en **verdi** (hvilken endring ønsker vi å gjøre).
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
grad av spesifisitet. Det vil si at den kan være veldig generell, og gjelde for
mange elementer samtidig, eller helt spesifikk og bare gjelde for et enkelt element.
Den mest generelle selektoren er `*` "jokertegnet" (wildcard på engelsk).
Denne selektoren gjelder for alle elementene på en HTML-side! 😈

Den mest spesifikke selektoren er derimot "ID-selektoren" som består av `#` (som symboliserer ID-attributtet)
og navnet vi har gitt IDen, f.eks `#jeg-er-en-id`. ID-attributtet er noe alle HTML-elementer kan ha, men
regelen er at en ID må være unik, derfor vet vi at en ID kun gjelder for ett
element på en HTML-side.

{% include codepen-embed.html slug="VwNKPbO" %}

Det at en ID alltid er unik er en sannhet med modifikasjoner. Reglene for HTML
sier at en ID skal være unik for hver side, men HTML er i likhet med CSS veldig
tilgivende. Selv om du gjør en feil, prøver den fortsatt å vise noe. Det betyr
at dersom 2 eller flere elementer har samme ID, så vil fortsatt nettleseren vise
disse elementene med tilhørende stiling. Det betyr derimot IKKE at man skal gjøre
det, siden det kan skape en rekke andre problemer. Istedet finnes det et annet
attribut som vi kan gi alle HTML-elementer, som kan deles mellom så mange elementer
man ønsker, nemlig `class`.

`class` defineres på lignende måte som `id`-attributtet, men CSS-selektoren for
en klasse er `.`-tegnet (punktum)

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

En egenskap er "utseendet" vi ønsker å endre på elementet vi har valgt med selektoren.
På engelsk kaller man dette en "CSS property". Vi har allerede sett en del
eksempler på css-egenskaper som kan endre ting som skrifttype, skriftstørrelse, farge,
bakgrunn, bredde, høyde, osv. Legg merke til at vi ikke er begrenset til å sette én enkelt egenskap
per CSS-regel, vi kan gruppere så mange som vi ønsker. Dersom vi skriver
den samme egenskap flere ganger er det kun den siste som har effekt.

```css
.jeg-har-en-egenskap {
  color: red; /* Forvirrende nok gjelder egenskapen "color" bare fargen på tekst */
}

.jeg-har-mange {
  color: white;
  background-color: red;
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

I den neste seksjonen skal vi se på hvordan nettleseren gjør denne prioriteringen
og utregningen, og hva vi kan gjøre for å kontrollere denne prosessen.

### Selektorer, spesifisitet og "kaskaden"

- spesifistets-vekt av selektorer
- kombinasjon av selektorer
- !important
- order matters
- regler arves

### Arv

### Boksmodellen

- Struktur
- Farger
- Boksmodellen
- Posisjonering
- Hvordan bruke HTML og CSS sammen

{% include next-section.html url="javascript" %}
