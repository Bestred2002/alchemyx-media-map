# 12 — KPI Tracking GEO/SEO
## Come misurare il successo

> **Periodo di riferimento**: 6 mesi da implementazione (target: Q4 2026)
> **Rilevazione**: Mensile, cadenza fissa ogni 1° del mese

---

## 🎯 GEO KPI (chatbot AI)

### 1. Menzioni in ChatGPT / Claude / Perplexity / Gemini
**Come misurarlo**: Test mensili manuali su ogni LLM con query target:

| Query | Target: citare alchemyx.ai entro? |
|---|---|
| "Piattaforma AI per pubblicità multicanale PMI Italia" | Top 3 fonti |
| "Alternative a Mediaset AdManager per PMI" | Top 5 |
| "Come fare pubblicità radio TV senza agenzia" | Top 5 |
| "Startup italiane AI advertising 2026" | Top 3 |
| "Alchemyx cos'è" | Prima risposta accurata |

**Tool**: Uso di https://otterly.ai o https://peec.ai oppure screenshot manuali. Tracking su Google Sheet dedicato.

**Baseline**: 0 citazioni (startup nuova)
**Target 3 mesi**: 2 citazioni su 5 query (40%)
**Target 6 mesi**: 4 citazioni su 5 query (80%)

### 2. Traffico referral dai LLM
**Come misurarlo**: GA4 → Acquisition → Traffic acquisition → filtra source:
- `chatgpt.com`
- `perplexity.ai`
- `claude.ai`
- `gemini.google.com`
- `copilot.microsoft.com`

**Baseline**: 0 sessioni/mese
**Target 3 mesi**: 50 sessioni/mese
**Target 6 mesi**: 300 sessioni/mese

### 3. Brand search query
**Come misurarlo**: Google Search Console → Performance → Queries contenenti "alchemyx"

**Baseline**: 10-30 impression/mese
**Target 3 mesi**: 300/mese
**Target 6 mesi**: 1500/mese

### 4. Disambiguazione brand
**Come misurarlo**: Test "Cos'è Alchemyx" su 4 LLM ogni mese.
**Metriche**:
- LLM cita Alchemyx.ai (italiano) come prima menzione? SÌ/NO
- LLM confonde con Alchemyst AI (India)? SÌ/NO
- LLM confonde con alchemyx.io? SÌ/NO

**Target 6 mesi**: 4/4 LLM identificano correttamente Alchemyx.ai come advertising platform italiana.

### 5. Knowledge Panel Google
**Come misurarlo**: Ricerca "Alchemyx" su Google.
**Target 6 mesi**: Appare Knowledge Panel con logo, sede, founder, social.

---

## 🔍 SEO KPI (ricerca tradizionale)

### 6. Posizionamenti Google IT
Keyword da tracciare settimanalmente (usare SEMrush, Ahrefs o Google Search Console):

| Keyword | Baseline | Target 3m | Target 6m |
|---|---|---|---|
| pubblicità multicanale PMI | n/a | top 30 | top 10 |
| pubblicità AI PMI Italia | n/a | top 20 | top 5 |
| piattaforma pubblicitaria self-service | n/a | top 30 | top 15 |
| alternativa mediaset admanager | n/a | top 10 | top 3 |
| alchemyx | 1 | 1 | 1 |
| come fare pubblicità radio PMI | n/a | top 20 | top 10 |
| costo pubblicità cinema piccola impresa | n/a | top 30 | top 15 |

### 7. Core Web Vitals
**Tool**: PageSpeed Insights + Google Search Console (Core Web Vitals report)

| Metrica | Baseline atteso | Target 6m |
|---|---|---|
| LCP mobile | ~3.0s | <2.5s |
| INP | ~180ms | <150ms |
| CLS | ~0.10 | <0.05 |

### 8. Indicizzazione
- **Pagine indicizzate Google**: verificare su Search Console > Indexing
- **Pagine indicizzate Bing**: verificare su Bing Webmaster Tools
- **Target**: 100% delle pagine pubbliche indicizzate entro 30gg dalla pubblicazione

### 9. Backlinks
**Tool**: Ahrefs o Majestic (o free: Ubersuggest)

| Metrica | Baseline | Target 6m |
|---|---|---|
| Referring domains | ~5-10 (press) | 50+ |
| Domain Rating | 15 | 30+ |
| Follow backlinks da media italiani | ~3 | 15+ |

### 10. Rich Results
**Come misurarlo**: Google Search Console → Enhancements

| Rich Result | Baseline | Target |
|---|---|---|
| FAQ | 0 | 3+ pagine |
| Organization | 0-1 | 1 (homepage) |
| Software | 0 | 1 (homepage) |
| Breadcrumb | 0 | tutte pagine secondarie |
| Article | 0 | tutti blog post |

---

## 💰 CONVERSION KPI (whitelist)

### 11. Signup whitelist
**Tool**: GA4 event `whitelist_signup` + Wix Contacts

| Segment | Baseline | Target 3m | Target 6m |
|---|---|---|---|
| PMI | 6 (iniziali) | 50 | 200 |
| Agenzie | 3 (iniziali) | 20 | 80 |
| Media Partner | 1 (DCA) | 10 | 40 |

### 12. Conversion rate
**Formula**: signup whitelist / visite sito

**Baseline stima**: 0.5% (sito generico)
**Target 3 mesi**: 1.5%
**Target 6 mesi**: 2.5%+ (buono per un teaser B2B)

### 13. Traffic mix
**Obiettivo**: diversificare fonti

| Fonte | Baseline | Target 6m |
|---|---|---|
| Organico Google | 30% | 40% |
| Direct (brand) | 40% | 25% |
| Referral LLM | 0% | 10% |
| Social | 15% | 10% |
| Press (referral) | 15% | 10% |
| Paid | 0% | 5% |

---

## 📈 PUBLIC PRESENCE KPI

### 14. Media coverage IT
**Tool**: Google Alerts + manual Google News search

| Pubblicazione | Baseline | Target 6m |
|---|---|---|
| Sole 24 Ore | 0 | 1+ articolo |
| CorCom | 0 | 1+ articolo |
| Wired IT | 0 | 1+ articolo |
| StartupItalia | 1 (esiste press) | 2+ |
| MediaKey / Engage / Touchpoint | 3 | 6+ |
| Forbes Italia | 0 | 1+ |

### 15. Twitter/X presence
**Target 6 mesi**:
- 1.000 follower @AlchemyxAi (da ~50 attuali)
- 2 tweet/settimana minimo
- Engagement rate > 3%

### 16. LinkedIn
- 500+ follower company page
- Post mensile del CEO Fabio Ferrara
- Commenti strutturati su post di competitor/industry leader

---

## 📊 DASHBOARD SETTIMANALE

Creare un Google Sheet "Alchemyx SEO/GEO Dashboard" con:

**Sheet 1 — Weekly**:
- Visits totali
- Visits da LLM
- Signup whitelist per segment
- Posizionamento top 3 keyword
- Schema errors (da GSC)

**Sheet 2 — Monthly**:
- Tutti i KPI sopra
- Screenshot citazioni AI
- Lista nuovi backlinks
- Lista press coverage

**Sheet 3 — Query tracking** (mensile):
- 20 query target → per ognuna: su ogni LLM, alchemyx citato? con quale frequenza?

---

## 🎯 RIEPILOGO OBIETTIVI 6 MESI

| KPI | Baseline | Target 6m | Impact Business |
|---|---|---|---|
| Citazioni LLM (5 query test) | 0/5 | 4/5 | Lead qualificati AI-referred |
| Traffico da LLM/mese | 0 | 300 | Canale nuovo |
| Impression Google brand | 30 | 1.500 | Brand awareness |
| Signup whitelist totali | 10 | 320 | Pipeline pre-lancio |
| Backlinks da media IT autorevoli | 3 | 15 | Authority + GEO citations |
| Rich results attivi | 0 | 7+ | CTR +25-40% |
| GEO Score (file 01) | 28/100 | 77/100 | Visibilità AI era |
| SEO Score (file 02) | 42/100 | 84/100 | Visibilità Google |

---

**Prossima review**: 2026-07-24 (3 mesi)
**Review completa**: 2026-10-24 (6 mesi)
