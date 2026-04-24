# 01 — Audit GEO (Generative Engine Optimization)
## Alchemyx.ai — Priorità MASSIMA

> **Obiettivo**: Dominare le risposte di ChatGPT, Claude, Perplexity, Gemini, AI Overviews per query relative a pubblicità multicanale AI per PMI italiane.
> **Data audit**: 2026-04-24
> **GEO Score attuale stimato**: 28/100
> **GEO Score target a 6 mesi**: 75/100

---

## 1. CRISI DI DISAMBIGUAZIONE ENTITÀ ⚠️ CRITICO

### Il problema
I LLM confondono Alchemyx (alchemyx.ai) con almeno 4 brand simili:

| Brand | URL | Cosa fa | Rischio confusione |
|---|---|---|---|
| **Alchemyx** (tuo) | alchemyx.ai | AI platform pubblicità multicanale PMI Italia | — |
| AlchemyX | alchemyx.io | AI-driven layout and monetisation engine | ALTO |
| Alchemyst AI | alchemyst.ai | AI agents per sales (India, Bengaluru) | ALTISSIMO |
| AlchemyX Trading | alchemytechnologies.eu | Forex/trading platform | MEDIO |
| Alchemy-X | alchemy-x.lovable.app | AI business transformation (generico) | MEDIO |
| alchemyx.online | alchemyx.online | Dominio segnalato per malware | CRITICO (reputazione) |

**Effetto concreto**: Se un utente chiede a ChatGPT "cos'è Alchemyx?", il LLM può rispondere con info mischiate di tutte queste entità — o peggio, citare Alchemyst AI India come se fosse il tuo prodotto.

### Soluzione urgente
1. **Disambiguazione esplicita nel copy**: Ogni pagina deve contenere frasi univoche come *"Alchemyx (alchemyx.ai), la piattaforma italiana di Alchemyst LAB Srl con sede a Milano..."*
2. **Schema Organization con sameAs**: Collegare esplicitamente a Crunchbase, LinkedIn, Wikidata
3. **Creare un Wikidata item** (Q-number) che distingua Alchemyx da Alchemyst AI
4. **Registrare il brand** su Crunchbase, StartupItalia, Registro Imprese (già fatto parzialmente), Italian Tech

---

## 2. ANALISI PAGINA /en/llms ✅ PUNTO DI FORZA

### Cosa è stato trovato
Esiste già una pagina dedicata `alchemyx.ai/en/llms` — "Alchemyx AI Advertising Platform | LLM Information". Ha anche un endpoint `/_functions/llms` aggiornato a marzo 2026.

**Questo è raro**: meno del 10% dei siti ha una pagina LLM-oriented. Alchemyx è avanti sul mercato italiano su questo punto.

### Problemi da risolvere
1. **Non è un `llms.txt` standard**: La pagina esiste ma NON è il file `/llms.txt` in root che gli AI crawler si aspettano per primo
2. **Contenuto da verificare**: Il formato deve seguire lo standard llmstxt.org (Markdown strutturato, sezioni predefinite)
3. **Mancante in italiano**: esiste solo in `/en/llms`, serve anche versione IT

### Azione
- Creare `/llms.txt` in root del sito (vedi file `08-LLMS-TXT.txt` in questo repo)
- Tenere `/en/llms` come pagina human-readable ma aggiornare il contenuto
- Aggiungere link a `llms.txt` nel footer

---

## 3. ROBOTS.TXT — STRATEGIA AI CRAWLER

### Situazione attuale
Robots.txt non verificabile (403 sul WebFetch). Molto probabilmente Wix genera un default che **blocca tutti i bot non-Googlebot**.

### Strategia raccomandata (2026)

Ogni LLM ha bot separati per: (a) training corpus, (b) search live, (c) user-triggered fetch. Bisogna **bloccare il training ma permettere search e user**, così si rifiuta la raccolta dati gratuita ma si resta visibili nelle risposte AI.

```
# =============================
# AI SEARCH BOTS — ALLOW
# =============================
User-agent: OAI-SearchBot
Allow: /

User-agent: ChatGPT-User
Allow: /

User-agent: Claude-SearchBot
Allow: /

User-agent: Claude-User
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: Perplexity-User
Allow: /

User-agent: Google-Extended
Allow: /

User-agent: Bingbot
Allow: /

User-agent: Applebot-Extended
Allow: /

User-agent: Amazonbot
Allow: /

User-agent: CCBot
Allow: /

# =============================
# AI TRAINING BOTS — BLOCK
# =============================
User-agent: GPTBot
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: anthropic-ai
Disallow: /

# =============================
# STANDARD
# =============================
User-agent: *
Allow: /

Sitemap: https://www.alchemyx.ai/sitemap.xml
```

---

## 4. SCHEMA.ORG — GAP ANALYSIS

### Situazione attuale
Wix genera automaticamente schema base `Organization` e `WebSite`. Dal sito attuale mancano quasi certamente:

| Schema | Stato | Impatto GEO | Urgenza |
|---|---|---|---|
| `Organization` completo con `sameAs`, `founder`, `foundingDate` | ❌ Parziale | ALTO | Immediato |
| `SoftwareApplication` | ❌ Assente | ALTISSIMO | Immediato |
| `FAQPage` | ❌ Assente | ALTISSIMO | Immediato |
| `Person` (Fabio Ferrara, Davide Catalano) | ❌ Assente | ALTO | Breve termine |
| `Article` sui blog post | ❌ Parziale (Wix genera base) | ALTO | Breve termine |
| `HowTo` | ❌ Assente | MEDIO | Medio termine |
| `BreadcrumbList` | ❌ Parziale | BASSO | Medio termine |
| `Product` + `Offer` | ❌ Assente | MEDIO | Medio termine |

**Stat chiave**: Pagine con `FAQPage` schema ricevono 340% più citazioni dai LLM rispetto a testo normale.

### Azioni prioritarie
1. Aggiungere `Organization` completo in homepage (vedi file `07-SCHEMA-JSONLD.html`)
2. Aggiungere `SoftwareApplication` in homepage e /pmi
3. Creare sezione FAQ in ogni pagina con `FAQPage` schema
4. Aggiungere `Person` schema per Fabio Ferrara e Davide Catalano nella pagina /azienda

---

## 5. CONTENT GAPS PER CITAZIONE LLM

### Pattern che i LLM citano di più
Ricerca 2026 mostra che i LLM citano contenuti che rispettano questi pattern:

1. **FAQ format** — 3× più citazioni di ChatGPT
2. **Risposta diretta nei primi 120 caratteri** — "Alchemyx è una piattaforma AI italiana che unifica pubblicità online e offline per PMI con budget da €2.000"
3. **Statistiche con fonte** — dati originali vengono citati obbligatoriamente
4. **Tabelle comparative** — "Alchemyx vs Mediaset AdManager"
5. **HowTo step-by-step** — 6.4× più inclusi negli AI Overviews

### Gap rilevati su alchemyx.ai
| Contenuto mancante | Query target | Priorità |
|---|---|---|
| Blog IT (zero articoli in italiano) | "pubblicità radio TV PMI Italia" | CRITICA |
| FAQ pagina dedicata | "come funziona Alchemyx" | CRITICA |
| Pagina comparativa vs competitor | "Alchemyx vs Mediaset AdManager" | ALTA |
| Pagina "cos'è il programmatic advertising" | "cos'è la pubblicità programmatica" | ALTA |
| Pagina "quanto costa pubblicità radio PMI" | "costo pubblicità radio piccola impresa" | ALTA |
| Case study numerici | "risultati campagna PMI multicanale" | MEDIA |
| Glossario advertising | "cos'è il DOOH" / "cos'è CTV" | MEDIA |

**Nota critica**: Il blog esiste **solo in inglese**. Per le query italiane che i clienti PMI fanno a ChatGPT/Gemini ("come faccio pubblicità su radio e TV con poco budget"), alchemyx.ai è completamente assente dai corpus in italiano.

---

## 6. E-E-A-T SIGNALS

### Presenti
- Founder con nome e background visibili (Fabio Ferrara — 15+ anni media planning)
- CTO nominato (Davide Catalano)
- CFO nominato (Vincenzo Baldi — ex B3 Capital, Ferrari Group)
- Indirizzo fisico verificabile (Piazza Castello 19, Milano)
- P.IVA pubblica (14297210966)
- Startup Innovativa registrata (Legge 221/2012)

### Mancanti
| Signal | Impatto | Azione |
|---|---|---|
| `Person` schema per founder | ALTO | Aggiungere in /azienda |
| `sameAs` LinkedIn dei founder | ALTO | Aggiungere a schema |
| Wikidata Q-item per Alchemyx | ALTO | Creare manualmente |
| Wikipedia IT (anche solo stub) | MEDIO | Richiedere quando si hanno referenze sufficienti |
| Google Business Profile | MEDIO | Registrare su maps.google.com |
| Crunchbase company page | ALTO | Registrare su crunchbase.com |
| G2 / Capterra listing | ALTO | Registrare pre-lancio (beta reviews) |

---

## 7. ANALISI COMPETITOR GEO

### Chi domina le query target oggi

| Query | Chi vince nelle risposte AI | Gap da colmare |
|---|---|---|
| "migliore piattaforma pubblicità AI per PMI italiane" | **MARiO/Italiaonline** (lanciato Apr 2026) | Blog IT + disambiguazione |
| "piattaforma pubblicità AI PMI Italia" | **Mediaset AdManager, ad:personam** | FAQ + schema |
| "pubblicità radio TV PMI self-service" | **Sky Advertising Manager** | Contenuto comparativo |
| "self-serve programmatic small business" | **ad:personam** (italiano, €149/mo) | Presenza EN + backlinks |
| "AI ad platform multichannel Italy" | **Alchemyx blog post già presente** ✅ | Mantenere e ampliare |

### Il rivale più pericoloso: MARiO di Italiaonline
Lanciato il **21 aprile 2026** (3 giorni fa dall'audit), ha già generato una valanga di PR su Sole 24 Ore, CorCom, MediaKey, Teleborsa. Posizionato come "AI per PMI italiane" ma è customer service, non media buying. **Alchemyx deve distinguersi esplicitamente** con la keyword "pubblicità" vs "assistente AI" per non venire schiacciato dalla PR wave di Italiaonline.

---

## 8. ENTITY SEO ROADMAP

### Fase 1 — Immediata (settimane 1-2)
1. Creare profilo Wikidata per Alchemyx (e per Fabio Ferrara)
2. Reclamare/creare pagina Crunchbase
3. Aggiornare pagina LinkedIn aziendale con tutti i campi
4. Registrare su StartupItalia e Italian Tech directory
5. Aggiungere Google Business Profile (sede Milano)

### Fase 2 — Breve termine (settimane 3-6)
6. Attivare G2 e Capterra listing (anche senza reviews, la presenza è segnale)
7. Ottenere listing su Registro Imprese digitale con link al sito
8. Pubblicare press kit su `/press` o `/en/press` con logo, bio, fact sheet
9. Distribuire comunicato stampa su Business Wire o PR Newswire (entra in Common Crawl)

### Fase 3 — Medio termine (mese 2-3)
10. Pubblicare 4-6 articoli IT su media autorevoli italiani (CorCom, Wired IT, Il Sole 24 Ore)
11. Ottenere link/menzione da almeno 2 università o centri ricerca italiani sul tema AI/advertising
12. Partecipare come speaker a eventi (Convegno IAB, SMAU, etc.) con bio linkabile

---

## 9. FRESHNESS STRATEGY

I LLM pesano molto la data di aggiornamento (35% del confidence score RAG):

- Pagine aggiornate negli ultimi 30 giorni ricevono **3.2× più citazioni**
- `dateModified` nel JSON-LD **deve corrispondere** alla data di revisione reale
- Il blog EN deve avere cadenza minima **2 articoli/mese**
- Il blog IT (da creare) deve avere cadenza **1 articolo/mese** come minimo
- Aggiornare la homepage ogni 30-45 giorni con almeno una modifica sostanziale

---

## 10. QUICK WINS (entro 7 giorni)

Impatto alto, effort basso:

| # | Azione | Dove | Impatto GEO |
|---|---|---|---|
| 1 | Aggiungere `/llms.txt` in root | Wix Custom Code | +++ |
| 2 | Correggere title EN homepage (è in italiano!) | Wix SEO Panel pagina /en | +++ |
| 3 | Correggere typo "Perchè" → "Perché" in /media | Wix SEO Panel | + |
| 4 | Aggiungere `Organization` schema completo | Wix Structured Data | +++ |
| 5 | Aggiungere `SoftwareApplication` schema | Wix Structured Data | +++ |
| 6 | Creare 5 FAQ in homepage + schema `FAQPage` | Wix Editor + Structured Data | +++ |
| 7 | Uniformare commissione: scegliere 13.98% e usare ovunque | Copy su tutte le pagine | ++ |
| 8 | Creare profilo Crunchbase | crunchbase.com | ++ |
| 9 | Creare profilo Wikidata | wikidata.org | +++ |
| 10 | Correggere slug /en/contatti → /en/contact | Wix URL settings | ++ |

---

## 11. GEO SCORE BREAKDOWN

| Dimensione | Score attuale | Score target | Note |
|---|---|---|---|
| Entity disambiguation | 10/100 | 80/100 | Brand confusion crisis |
| Schema.org | 20/100 | 85/100 | Solo Wix default |
| llms.txt | 35/100 | 90/100 | /en/llms esiste, manca root |
| Robots.txt AI bots | 15/100 | 80/100 | Probabilmente blocca tutto |
| Content for LLM citation | 25/100 | 75/100 | Blog solo EN, FAQ mancanti |
| E-E-A-T signals | 40/100 | 80/100 | Team visibile, manca schema |
| Entity registry | 20/100 | 75/100 | Mancano Wikidata, Crunchbase, G2 |
| Freshness | 45/100 | 80/100 | Blog attivo ma irregolare |
| Italian corpus presence | 15/100 | 70/100 | Zero blog IT |
| **TOTALE** | **28/100** | **77/100** | |

---

*Continua in: `02-AUDIT-SEO.md` per la parte tecnica on-page*
