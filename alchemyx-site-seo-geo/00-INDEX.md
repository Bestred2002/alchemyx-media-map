# Alchemyx — Audit SEO/GEO completo + Playbook implementativo

> **Cliente**: Alchemyst LAB Srl (alchemyx.ai)
> **Claim**: Piattaforma AI per la pubblicità multicanale delle PMI
> **Data audit**: 2026-04-23
> **Preparato da**: Claude Code (Opus 4.7)
> **Destinatario esecuzione**: Claude Co-work con connettore Wix Studio
> **Branch**: `claude/analyze-alchemyx-seo-UtNMx`
> **Obiettivo principale**: Dominare la visibilità nei chatbot AI (ChatGPT, Claude, Perplexity, Gemini, AI Overviews) per query relative a pubblicità multicanale AI per PMI italiane.

---

## 📚 Indice documenti

| # | File | Scopo | Chi esegue |
|---|------|-------|------------|
| 00 | **00-INDEX.md** | Questo file — indice navigazione | — |
| 01 | **01-AUDIT-GEO.md** ⭐ | Audit GEO (priorità MASSIMA) | Lettura |
| 02 | **02-AUDIT-SEO.md** | Audit SEO tecnico + on-page | Lettura |
| 03 | **03-AUDIT-RESPONSIVE.md** | Audit responsive/resize + UX breakpoint | Lettura |
| 04 | **04-COMPETITOR-BENCHMARK.md** | Benchmark competitor + gap analysis | Lettura |
| 05 | **05-CONTENT-PACK-IT.md** | Testi IT pronti da incollare | Claude Co-work |
| 06 | **06-CONTENT-PACK-EN.md** | Testi EN pronti da incollare | Claude Co-work |
| 07 | **07-SCHEMA-JSONLD.html** | Blocchi JSON-LD pronti | Claude Co-work |
| 08 | **08-LLMS-TXT.txt** | File llms.txt per root del sito | Claude Co-work |
| 09 | **09-ROBOTS-TXT.txt** | File robots.txt aggiornato | Claude Co-work |
| 10 | **10-WIX-STUDIO-PLAYBOOK.md** ⭐⭐ | **Istruzioni operative passo-passo per Claude Co-work** | Claude Co-work |
| 11 | **11-IMPLEMENTATION-CHECKLIST.md** | To-do ordinata con priorità | User + Claude Co-work |
| 12 | **12-KPI-TRACKING.md** | Come misurare il successo GEO/SEO | User |

---

## 🎯 Ordine di lettura consigliato

### Per te (fondatore), 20 minuti:
1. Leggi `00-INDEX.md` (questo)
2. Leggi `01-AUDIT-GEO.md` — capisci cosa non va sul GEO e perché
3. Scorri `11-IMPLEMENTATION-CHECKLIST.md` — to-do ordinate
4. Salta a `12-KPI-TRACKING.md` — come capire se sta funzionando

### Per Claude Co-work (esecutore su Wix Studio):
1. Legge `10-WIX-STUDIO-PLAYBOOK.md` ⭐ (istruzioni dettagliate)
2. Consulta `05`, `06`, `07`, `08`, `09` per i contenuti da incollare
3. Esegue intervento per intervento, spunta checklist in `11`

---

## 🔑 Punti chiave dell'audit (TL;DR)

### ✅ Cose già fatte bene
- Esiste già un tentativo di pagina `/en/llms` (LLM Information) → buon segnale, ma da rifare con formato standard llms.txt
- Architettura multilingua IT/EN con sottocartella `/en/` → corretta per hreflang
- Blog attivato in EN (due post già pubblicati)
- Content press ben diffuso (mediakey.it, youmark.it, dailyonline.it) → buon early-stage PR

### 🔴 Rischi GEO critici
1. **Brand confusion**: esistono almeno 5 "Alchemy*" distinti che i LLM possono confondere (alchemyx.io, alchemyst-ai India, alchemy.com, alchemy.cloud, alchemy-x.lovable.app). **Serve disambiguazione esplicita e entity-level.**
2. **Nessun llms.txt standard** in root (quello su `/en/llms` è una pagina, non il file canonico llmstxt.org)
3. **Schema.org probabilmente povero** (Wix default = solo Organization base)
4. **FAQ semantiche assenti** — il formato che i LLM citano di più
5. **Entità Wikidata/Wikipedia non stabilita** — blocca la costruzione del Knowledge Graph
6. **Pagina italiana non indicizzata nei corpora LLM** con keyword strategiche italiane

### 🟡 Aree di miglioramento SEO
- Title/meta: ripetitivi tra pagine, non ottimizzati per long-tail
- H1/H2: probabilmente non strutturati per featured snippet
- Internal linking: da verificare (mappatura topic cluster mancante)
- Core Web Vitals: Wix Studio tendenzialmente soffre su LCP mobile
- Hreflang: da verificare impostazione corretta Wix Multilingual

### 🟠 Whitelist CTA — strategia di conversione
- **IT**: whitelist aperta a PMI e Media (2 segmenti = 2 form dedicati preferibili)
- **EN**: zero conversione, solo informativa → ma ottimizzata SEO/GEO per visibilità globale e credibilità
- Tracking eventi whitelist su GA4 + Meta Pixel + LinkedIn Insight (target B2B)

---

## 🏗️ Struttura sito rilevata

```
alchemyx.ai/
├── /                                    Homepage IT
├── /pmi                                 Pagina per PMI
├── /agenzie                             Pagina per Agenzie (white label)
├── /media                               Pagina per Media Partner
├── /azienda                             Chi Siamo
├── /contatti                            Contatti (?)
├── /en/                                 Homepage EN
├── /en/pmi                              PMI EN (?)
├── /en/agencies                         Agencies EN (?)
├── /en/media                            Media EN (?)
├── /en/about                            About EN (?)
├── /en/contatti                         Contact EN
├── /en/llms                             LLM Information page (da migrare!)
├── /en/post/what-is-alchemyx-...        Blog post EN #1
└── /en/post/the-state-of-ai-in-...      Blog post EN #2
```

Post audit serve verifica: mancano blog IT? Mancano pagine EN sorella /pmi ecc.?

---

## 📊 Dati business raccolti (base per schema + contenuti)

| Campo | Valore |
|---|---|
| Brand | Alchemyx |
| Azienda | Alchemyst LAB Srl |
| Sede | Piazza Castello 19, 20121 Milano |
| P.IVA | 14297210966 |
| ATECO | 62.10.00 (Software Development) |
| Stato | Startup Innovativa (Legge 221/2012) dal Ottobre 2025 |
| Fondazione | Luglio 2025 |
| CEO & Founder | Fabio Ferrara |
| CTO | Davide Catalano |
| Twitter/X | @AlchemyxAi |
| Prodotto | Piattaforma AI self-serve per pubblicità multicanale |
| Canali digitali | Google Search, Google Display, Social |
| Canali offline | Radio, TV addressable, CTV, Cinema, DOOH |
| Commissione | 13.98% |
| Budget minimo | €2.000 |
| Target 1 | PMI italiane |
| Target 2 | Agenzie (white label) |
| Target 3 | Media Partner (radio, DOOH, CTV) |
| Media partner attivo | DCA Cinema (esclusiva cinema nazionale) |
| MVP | H2 2026 (luglio 2026) |
| Pilot | Settembre 2026 |
| Lancio commerciale | Q1 2027 (Italia) |
| Espansione | Spagna 2028 → DE/FR 2029-2030 → USA 2031 |

---

## 🚦 Stato lavori

- [x] Reconnaissance (parziale — sito blocca WebFetch; raccolta via WebSearch + sub-agenti)
- [ ] Audit GEO
- [ ] Audit SEO tecnico
- [ ] Audit responsive
- [ ] Competitor benchmark
- [ ] Content pack IT + EN
- [ ] Schema JSON-LD
- [ ] llms.txt + robots.txt
- [ ] Wix Studio Playbook
- [ ] Implementation checklist
- [ ] KPI tracking doc
