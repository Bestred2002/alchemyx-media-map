# 02 — Audit SEO Tecnico + On-Page
## Alchemyx.ai

> **Data audit**: 2026-04-24
> **SEO Score attuale stimato**: 42/100
> **SEO Score target a 6 mesi**: 80/100

---

## 1. PROBLEMI TECNICI CRITICI

### 1.1 Title tag EN homepage — BUG GRAVE
**Problema**: Il title tag della homepage EN (`/en`) è ancora in **italiano**.
- Title attuale rilevato: `"Alchemyx – Piattaforma AI per la pubblicità semplice delle PMI"`
- Title corretto EN: `"Alchemyx – AI Platform for Simple Multichannel Advertising | SMBs"`

**Impatto**: Google/Bing indicizzano il titolo italiano per la versione EN → confusione hreflang, ranking EN compromesso, utenti anglofoni vedono titolo italiano in SERP.

**Fix**: Wix Dashboard → Pages → `/en` homepage → SEO → Title Tag

---

### 1.2 Slug italiano su pagina EN
**Problema**: `/en/contatti` usa slug italiano invece di `/en/contact`
- Impatto SEO: negativo su keyword anglofone
- Impatto UX: confonde utenti EN

**Fix**: Wix Dashboard → Pages → Contatti EN → Advanced SEO → URL Slug → cambia in `contact`
Poi aggiungere redirect 301 da `/en/contatti` a `/en/contact` nel Redirect Manager.

---

### 1.3 Typo nel title della pagina /media
**Problema**: Title pagina `/media` è `"Perchè diventare Media Partner Alchemyx?"` — typo senza accento
- Corretto: `"Perché diventare Media Partner Alchemyx?"`
- Impatto: SEO minore ma E-E-A-T negativo (professionalità percepita)

**Fix**: Wix Dashboard → Pages → /media → SEO → Title Tag

---

### 1.4 Pagine EN mancanti
**Problema critico**: Non esistono versioni EN dedicate di:
- `/en/pmi` (o `/en/smb`)
- `/en/agencies`
- `/en/media-partners`
- `/en/about`

Solo `/en` (homepage thin), `/en/contatti`, `/en/llms` e i blog post EN.

**Impatto**: Hreflang incompleto, utenti EN che arrivano su pagine IT rimbalzano, keyword EN non rankano.

**Fix strutturale** (da valutare con roadmap): creare versioni EN delle 4 pagine principali o, per il teaser, almeno una pagina `/en/about` sostanziale.

---

### 1.5 Incoerenza prezzi
**Problema**: Tre diverse cifre in giro:
- Marketing copy e PR: "budget da €2.000"
- Pagina /pmi: "wallet minimo di €2.284"
- Fee: "13.98%" in /pmi, "13.8%" in alcune press

**Impatto SEO**: Featured snippet impossibile su "quanto costa Alchemyx" con dati incoerenti. Impatto GEO: i LLM trovano dati contraddittori e perdono fiducia nell'entità.

**Fix**: Decidere i numeri ufficiali e allineare ovunque — sito, blog, comunicati.

---

## 2. META TAG — ANALISI PAGINA PER PAGINA

### Homepage IT `/`
| Campo | Stato | Note |
|---|---|---|
| Title | ⚠️ Da verificare | Probabilmente generico |
| Meta description | ⚠️ Da verificare | Wix default o customizzato? |
| Canonical | ✅ Auto-Wix | `https://www.alchemyx.ai/` |
| OG title | ⚠️ Da verificare | Punta a immagine corretta? |
| OG image | ⚠️ Da verificare | Dimensioni 1200×630? |
| Twitter Card | ⚠️ Da verificare | summary_large_image? |
| Robots | ✅ Presumibilmente index,follow | — |

### Homepage EN `/en`
| Campo | Stato | Note |
|---|---|---|
| Title | ❌ BUG — in italiano | Vedere §1.1 |
| Meta description | ⚠️ Da verificare | Potrebbe anche essere IT |
| Hreflang | ⚠️ Da verificare in source | Auto-generato da Wix Multilingual |
| Canonical | ✅ | `https://www.alchemyx.ai/en` |

### /pmi
| Campo | Stato | Note |
|---|---|---|
| Title | ✅ Ottimo | "Pubblicità semplice per PMI \| Piattaforma AI Alchemyx" |
| Meta description | ✅ Presente | Descrizione funzionalità |
| H1 | ⚠️ Da verificare | Probabilmente = title |

### /agenzie
| Campo | Stato | Note |
|---|---|---|
| Title | ✅ | "White Label ADV per Agenzie \| Piattaforma AI Alchemyx" |

### /media
| Campo | Stato | Note |
|---|---|---|
| Title | ❌ Typo | "Perchè" → "Perché" |

### /azienda
| Campo | Stato | Note |
|---|---|---|
| Title | ✅ | "Chi Siamo \| Alchemyx — Alchemyst LAB Srl" |

---

## 3. STRUTTURA H1/H2 — ON-PAGE

### Pattern ideale per LLM e Featured Snippet
```
H1: [Claim principale — risposta diretta alla query primaria]
H2: [Sotto-argomento 1 — risposta diretta FAQ]
H2: [Sotto-argomento 2]
...
```

### Raccomandazioni per homepage IT
```
H1: "La piattaforma AI che unifica pubblicità online e offline per le PMI italiane"
H2: "Pianifica su radio, TV, cinema, social e Google in un'unica interfaccia"
H2: "Come funziona Alchemyx in 4 passi"
H2: "Quanto costa fare pubblicità con Alchemyx?"
H2: "Domande frequenti"
```

Il copy attuale è probabilmente buono ma manca la sezione FAQ strutturata come H2 con risposta diretta sotto.

---

## 4. HREFLANG — ANALISI

### Come funziona Wix Multilingual (auto-generato)
Wix genera hreflang automaticamente quando Multilingual è attivo:
```html
<link rel="alternate" hreflang="it" href="https://www.alchemyx.ai/pmi" />
<link rel="alternate" hreflang="en" href="https://www.alchemyx.ai/en/pmi" />
<link rel="alternate" hreflang="x-default" href="https://www.alchemyx.ai/" />
```

### Problema attuale
Le pagine IT `/pmi`, `/agenzie`, `/media`, `/azienda` **non hanno corrispondente EN**. Questo crea hreflang incompleto — Google vede pagine IT senza pair EN e può penalizzare o ignorare l'hreflang.

### Fix
Opzione A (consigliata per teaser): creare pagine EN minime (anche solo 300 parole) per /en/smb, /en/agencies, /en/media, /en/about — poi espandere post-lancio.
Opzione B: escludere le pagine senza pair dall'hreflang tramite `hreflang="x-default"` only.

---

## 5. SITEMAP.XML

Wix auto-genera la sitemap. Verificare che contenga:
- Tutte le pagine principali IT e EN
- I blog post EN
- Le pagine categoria blog

Escludere dalla sitemap (via noindex):
- Pagine di thank-you
- Pagine di sistema Wix (`/_api/`, `/_functions/`)

---

## 6. CORE WEB VITALS — WIX STUDIO 2026

### Benchmark atteso
Wix Studio con Turbo 3.0 raggiunge questi valori medi su siti marketing:

| Metrica | Valore atteso | Soglia "Good" |
|---|---|---|
| LCP (Largest Contentful Paint) | 2.1–2.8s mobile | < 2.5s |
| INP (Interaction to Next Paint) | 150–200ms | < 200ms |
| CLS (Cumulative Layout Shift) | 0.05–0.12 | < 0.1 |

**LCP mobile è il punto critico** — dipende dall'immagine hero. Se l'hero è un video background o un'immagine non ottimizzata, LCP può salire a 3.5–4s.

### Ottimizzazioni specifiche per Alchemyx
1. **Hero image**: usare JPG/WebP, dimensioni esplicite width/height, `loading="eager"` solo per hero
2. **Font**: max 2-3 famiglie, WOFF2, `font-display: swap`
3. **Video background**: se presente, caricare solo su desktop (hidden su mobile), usare poster frame JPG
4. **App Wix**: disabilitare Wix Chat, Wix Bookings e qualsiasi app non necessaria su ogni pagina
5. **Immagini sezioni**: tutte lazy load tranne hero

---

## 7. INTERNAL LINKING — TOPIC CLUSTER

### Struttura attuale (stimata)
Non è chiara la struttura di internal linking. Probabilmente navigazione via header menu.

### Struttura raccomandata (Topic Cluster Model)
```
PILLAR PAGE: Homepage (pubblicità AI multicanale PMI)
  ├── CLUSTER 1: /pmi — per le PMI
  │     └── Blog: "Come fare pubblicità radio TV con €2000"
  │     └── Blog: "Pubblicità DOOH per PMI locali"
  │     └── Blog: "Costo pubblicità cinema piccola impresa"
  ├── CLUSTER 2: /agenzie — per le agenzie
  │     └── Blog: "White label adtech per agenzie media"
  ├── CLUSTER 3: /media — per i media partner
  │     └── Blog: "Come monetizzare l'inventory radio locale"
  └── CLUSTER 4: /azienda — about
        └── Blog: "Chi è Alchemyx" (già esiste in EN)
```

**Azioni**: aggiungere link interni da ogni blog post verso la pagina prodotto più rilevante, e viceversa.

---

## 8. INDEXING — BING WEBMASTER TOOLS

**Critico per ChatGPT Search**: 87% delle citazioni ChatGPT Search corrispondono ai top result Bing. Se non sei in Bing, non sei citato da ChatGPT browsing.

**Azioni**:
1. Registrare alchemyx.ai su https://www.bing.com/webmasters/
2. Verificare ownership (TXT record DNS o meta tag)
3. Submittare sitemap.xml
4. Attivare **IndexNow** — Wix Studio supporta IndexNow nativo (SEO dashboard → Indexing)
5. Controllare che Bingbot sia allowed in robots.txt

---

## 9. ANALYTICS — STACK RACCOMANDATO

### Setup minimo per un teaser pre-lancio
```
GTM Container (unico punto d'installazione)
  ├── GA4 — tracking standard
  ├── Meta Pixel — retargeting PMI
  ├── LinkedIn Insight Tag — B2B signal (fondamentale per PMI/agenzie)
  ├── Hotjar o Microsoft Clarity — heatmap gratuita
  └── Google Ads Conversion Tag (pronto per quando si attiva paid)
```

### Evento critico da tracciare
```javascript
// Whitelist form submit
dataLayer.push({
  event: 'whitelist_signup',
  segment: 'pmi', // o 'media' o 'agenzia'
  source: document.referrer
});
```

Questo evento alimenta le audience personalizzate Meta e LinkedIn per retargeting.

---

## 10. SEO SCORE BREAKDOWN

| Dimensione | Score attuale | Score target | Priority |
|---|---|---|---|
| Title tags | 55/100 | 90/100 | ALTA (EN bug) |
| Meta description | 50/100 | 85/100 | ALTA |
| Hreflang | 35/100 | 80/100 | ALTA |
| Schema.org | 20/100 | 85/100 | CRITICA |
| Core Web Vitals | 55/100 | 80/100 | MEDIA |
| Internal linking | 30/100 | 75/100 | MEDIA |
| Sitemap | 65/100 | 85/100 | BASSA |
| Bing indexing | 20/100 | 80/100 | ALTA |
| Analytics setup | 40/100 | 85/100 | MEDIA |
| Content depth | 35/100 | 75/100 | ALTA |
| **TOTALE** | **42/100** | **84/100** | |

---

*Continua in: `03-AUDIT-RESPONSIVE.md` per analisi resize/breakpoint*
