# pension
Interaktiv guide till det svenska pensionssystemet - allmän pension (PGI), ITP 1 och privat sparande. Ren HTML/CSS/JS.

> **Vad kan du förvänta dig i pension?**
> En informativ och interaktiv guide till det svenska pensionssystemet – på svenska.

Live: [davethebabe.github.io/pension](https://davethebabe.github.io/pension)

---

## Om projektet

En statisk enkelsidig webbplats (ren HTML + CSS + JavaScript, ingen backend) som förklarar det svenska pensionssystemet och låter besökaren simulera sina egna pensionsavsättningar baserat på lönenivå.

Sidan riktar sig till privatpersoner som vill förstå hur allmän pension, tjänstepension (ITP 1) och privat sparande hänger ihop – och vad den egna lönen faktiskt ger i pensionsavsättning.

---

## Innehåll

| Sektion | Beskrivning |
|---|---|
| **Allmän pension** | Förklaring av inkomst- och premiepension, PGI-mekaniken (7 % avgift), 18,5 %-regeln och inkomsttaket |
| **Tjänstepension (ITP 1)** | Avtalstabell, 4,5 %/30 %-reglerna, nyckeltal 2026, varning om stigande IBB |
| **Löneexempel** | Statisk tabell med beräknade avsättningar för 30 000 / 52 125 / 70 000 kr/mån |
| **Historik IBB** | Tabell 2020–2026 med IBB, ITP 1-gränser och AP-tak per år – med interaktiv lås-funktion |
| **Interaktiv simulator** | Slider 10 000–120 000 kr/mån med live-uppdaterad tabell, stapeldiagram och kurvdiagram |
| **Privat sparande** | Råd, tumregler, riskperspektiv, systemets hållbarhet vs. tillräcklighet |
| **Resurser** | Länkar till MinPension, Ekonomifakta, Avanza, Pensionsmyndigheten och podcavsnitt |

---

## Funktioner

- **PGI-korrekt beräkning** – allmän pension räknas via pensionsgrundande inkomst efter 7 % avgiftsavdrag, inte direkt på bruttolön
- **Interaktiv lönesimulator** med stapeldiagram (per komponent) och kurvdiagram (avsättning som funktion av lönen)
- **Historisk IBB-tabell** med lås-funktion: klicka på valfritt antal år för att frysa deras ITP 1-värde och jämföra med nuvarande lön
- **Responsiv design** – fungerar på mobil och desktop
- Inga ramverk, ingen build-step – en enda `index.html`

---

## Teknisk stack

| Del | Teknik |
|---|---|
| Markup & layout | HTML5 + CSS (custom properties, flexbox) |
| Logik & interaktivitet | Vanilla JavaScript (ES2020) |
| Diagram | [Chart.js 4](https://www.chartjs.org/) via CDN |
| Backend | Ingen – helt statisk |

---

## Nyckeltal (2026)

| Parameter | Värde |
|---|---|
| Inkomstbasbelopp (IBB) | 83 400 kr |
| Praktiskt inkomsttaket AP (8,07 × IBB / 12) | 56 087 kr/mån |
| PGI-tak (7,5 × IBB / 12) | 52 125 kr/mån |
| Allmän pensionsavgift | 7 % |
| Pensionsrätt | 18,5 % av PGI (16 % IP + 2,5 % PP) |
| ITP 1 bas | 4,5 % upp till 52 125 kr/mån |
| ITP 1 tillägg | 30 % på lönedel 52 125–208 500 kr/mån |

Konstanterna uppdateras varje år i `<script>`-blocket i `index.html`.

---

## Att uppdatera för nytt år

Öppna `index.html` och hitta konstantblocket:

```javascript
const IBB           = 83400;         // inkomstbasbelopp – uppdatera varje år
```

Lägg även till det nya årets IBB i `IBB_HISTORY`-arrayen:

```javascript
const IBB_HISTORY = [
  ...
  { year: 2026, ibb: 83400 },
  { year: 2027, ibb: XXXXX },  // ← lägg till här
];
```

Uppdatera slutligen de statiska exempelvärdena i löneexempeltabellen och texthänvisningar till aktuellt år.

---

## Licens

Fri att använda och anpassa. Inga garantier lämnas för siffrornas aktualitet – kontrollera alltid mot officiella källor (Pensionsmyndigheten, Collectum).

---

## Källor

- [Pensionsmyndigheten – Årsredovisning 2024](https://www.pensionsmyndigheten.se/content/dam/pensionsmyndigheten/blanketter---broschyrer---faktablad/publikationer/%C3%A5rsredovisningar/pensionsmyndighetens-%C3%A5rsredovisning/Pensionsmyndighetens%20%C3%A5rsredovisning%202024.pdf)
- [Pensionsmyndigheten – Är pensionerna tillräckliga?](https://www.pensionsmyndigheten.se/content/dam/pensionsmyndigheten/blanketter---broschyrer---faktablad/publikationer/rapporter/2021/ar-pensionerna-tillrackliga.pdf)
- [MinPension.se](https://www.minpension.se/)
- [Ekonomifakta.se](https://www.ekonomifakta.se/)
- [Collectum – ITP 1](https://www.collectum.se/)
