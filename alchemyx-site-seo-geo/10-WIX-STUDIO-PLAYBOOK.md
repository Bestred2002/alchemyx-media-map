# 10 — WIX STUDIO PLAYBOOK per CLAUDE CO-WORK ⭐⭐
## Guida operativa passo-passo per l'esecutore AI

> **Destinatario**: Claude Co-work (con connettore Wix attivo)
> **Modalità**: Esegui in ordine, ogni passo spuntato nel file `11-IMPLEMENTATION-CHECKLIST.md`
> **Obiettivo**: Implementare tutte le raccomandazioni dei 9 file precedenti sul sito Wix Studio alchemyx.ai

---

## 🎯 CONTESTO INIZIALE

Tu sei Claude Co-work e stai operando sul sito Wix Studio `alchemyx.ai` tramite il connettore Wix MCP. L'obiettivo è implementare un audit SEO/GEO completo che trovi già documentato in questo repo GitHub:

```
Bestred2002/alchemyx-media-map (branch: claude/analyze-alchemyx-seo-UtNMx)
└── alchemyx-site-seo-geo/
    ├── 00-INDEX.md           (panoramica)
    ├── 01-AUDIT-GEO.md       (priorità)
    ├── 02-AUDIT-SEO.md       (fix tecnici)
    ├── 03-AUDIT-RESPONSIVE.md
    ├── 04-COMPETITOR-BENCHMARK.md
    ├── 05-CONTENT-PACK-IT.md (testi IT)
    ├── 06-CONTENT-PACK-EN.md (testi EN)
    ├── 07-SCHEMA-JSONLD.html (schema pronti)
    ├── 08-LLMS-TXT.txt       (llms.txt per root)
    ├── 09-ROBOTS-TXT.txt     (robots.txt AI-bot)
    └── 10-WIX-STUDIO-PLAYBOOK.md  ← questo file
```

**Prima di iniziare**: leggi 00-INDEX, 01-AUDIT-GEO, 02-AUDIT-SEO in questo ordine per capire il contesto.

---

## 🧰 STRUMENTI WIX NECESSARI

Verifica di avere accesso a:
1. **Wix Studio Editor** (canvas visuale, modifiche pagine)
2. **Wix Dashboard** (SEO Panel, Settings, Robots.txt Editor, Redirect Manager)
3. **Wix Blog** (CMS post, categorie, tag)
4. **Wix Multilingual** (switch IT/EN)
5. **Wix Custom Code** (Settings → Custom Code)
6. **Wix Forms** (creazione e tracking form)

Se manca qualcosa → **STOP**, avvisa l'utente e non proseguire.

---

## 📋 FASI DI LAVORO (IN ORDINE)

### FASE 1 — QUICK WINS CRITICI (1-2h)

#### 1.1 Fix title EN homepage
- Wix Dashboard → Pages → `/en` (Home EN) → SEO → Title Tag
- **Attuale**: `Alchemyx – Piattaforma AI per la pubblicità semplice delle PMI` (in italiano!)
- **Nuovo**: `Alchemyx | AI Multichannel Advertising Platform for SMBs`
- Meta description → usa testo da `06-CONTENT-PACK-EN.md` sezione 1

#### 1.2 Fix typo pagina /media
- Wix Dashboard → Pages → `/media` → SEO → Title Tag
- **Attuale**: `Perchè diventare Media Partner Alchemyx?`
- **Nuovo**: `Perché diventare Media Partner Alchemyx?`

#### 1.3 Fix slug /en/contatti → /en/contact
- Wix Dashboard → Pages → Contatti EN → Advanced SEO → URL Slug
- Cambia da `contatti` a `contact`
- Vai su Dashboard → SEO → Tools → URL Redirect Manager
- Aggiungi redirect 301: `/en/contatti` → `/en/contact`

#### 1.4 Allineamento prezzi ovunque
Valori ufficiali da usare:
- Commissione: **13,98%** (sempre — mai 13,8%)
- Budget minimo: **€2.000** (sempre — mai €2.284)
- Aggiorna: Homepage IT, /pmi, blog post, about

#### 1.5 Crea file /llms.txt in root
- Dashboard → Settings → Custom Code → Head
- **Non è possibile creare /llms.txt direttamente su Wix** (non è un file fisico modificabile). Due opzioni:
  - **Opzione A**: Crea una pagina Wix con URL slug `llms.txt`, incolla contenuto da `08-LLMS-TXT.txt` come plain text, imposta Content-Type text/plain via Velo (avanzato)
  - **Opzione B** (più semplice): Wix 2026 auto-genera `/llms.txt` — verifica su Dashboard → SEO → Tools → "Go to LLMs.txt"; se il contenuto è diverso da quello raccomandato, sovrascrivi via Velo HTTP function

Se l'opzione A/B non funziona, lascia una nota nel commento e passa oltre. L'utente può risolvere al rientro.

---

### FASE 2 — SCHEMA JSON-LD (2h)

Apri file `07-SCHEMA-JSONLD.html` e procedi per pagina:

#### 2.1 Homepage IT
- Dashboard → Pages → Home IT → SEO → Advanced SEO → Structured Data
- Clicca "+ Add New Markup"
- Incolla **BLOCCO 1** (Organization + WebSite) — verifica < 7000 chars
- Salva
- "+ Add New Markup" → **BLOCCO 2** (SoftwareApplication)
- "+ Add New Markup" → **BLOCCO 3** (FAQPage)

#### 2.2 Pagina /pmi
- Duplica i blocchi BLOCCO 2 e BLOCCO 3 anche qui
- NON serve il BLOCCO 1 (Organization è solo per homepage)

#### 2.3 Pagina /azienda
- Aggiungi **BLOCCO 4** (Person Fabio Ferrara)
- Aggiungi **BLOCCO 5** (Person Davide Catalano)

#### 2.4 Breadcrumb su tutte le pagine
Per ogni pagina (/pmi, /agenzie, /media, /azienda), adatta il **BLOCCO 6** cambiando nome e URL della pagina specifica.

#### 2.5 Validazione
Una volta pubblicato, testa su:
- https://validator.schema.org/
- https://search.google.com/test/rich-results

---

### FASE 3 — CONTENUTO IT (2-3h)

Apri `05-CONTENT-PACK-IT.md`.

#### 3.1 Homepage IT — sezioni
- H1, subheadline, CTA principale → Wix Editor canvas
- Sezione "Come funziona" (4 step) → aggiungi via Container + Repeater
- Sezione Canali → lista Online/Offline
- Sezione "Per chi è" → testo breve
- Sezione Social Proof → "6 PMI già in whitelist", "DCA Cinema partner"
- Sezione Urgency → "Registrazioni aperte fino luglio 2026"
- **Nuova sezione FAQ** (7 domande) → Usa Wix Repeater collapsible

#### 3.2 Pagina /pmi — aggiornamento copy
- H1, subheadline
- Pricing box FREE (5 bullet)
- Pricing box PREMIUM (4 bullet)
- CTA box whitelist con form (vedi FASE 4)

#### 3.3 Pagina /media — fix typo + copy
- Aggiorna H1, meta title (già fatto in FASE 1)
- Verifica che il CTA sia "Diventa Media Partner"

#### 3.4 Pagina /azienda — team e about
- Sostituisci about con testo da CONTENT-PACK-IT sezione 8
- Aggiungi bio di Vincenzo Baldi (nuovo team member)

#### 3.5 Footer IT
- Aggiungi P.IVA, sede, PEC in footer (usa testo sezione 9 di CONTENT-PACK-IT)
- Link a Privacy Policy, Cookie Policy, Note Legali

---

### FASE 4 — FORM WHITELIST (1h)

#### 4.1 Crea form whitelist in Wix Forms
- Dashboard → Forms → Crea nuovo form "Whitelist Alchemyx"
- Campi:
  - Nome e Cognome (richiesto, testo)
  - Email aziendale (richiesto, email)
  - Settore (dropdown: PMI / Agenzia / Media Partner / Altro)
  - [Hidden] UTM source (auto-populate)
  - Privacy consent (checkbox richiesto)
- Testo submit button: `Richiedi accesso anticipato`

#### 4.2 Incorpora form solo nelle pagine IT
- Homepage IT → sezione whitelist
- /pmi → sezione whitelist
- /media → sezione whitelist (per Media Partner)
- **NON** nelle pagine /en/* (critical requirement!)

#### 4.3 Configura tracking
- Dashboard → Marketing → Integrations → aggiungi GTM Container ID
- Event automatico: Wix emette `form_submit` su dataLayer
- Configura in GTM:
  - GA4 event: `whitelist_signup`
  - Meta Pixel: evento Lead
  - LinkedIn Insight: evento Conversion

#### 4.4 Destinazione lead
- I submit finiscono in Wix Contacts automaticamente
- Configura email notification a `info@alchemystlab.com`
- Opzionale: connetti a Mailchimp/HubSpot se già in uso

---

### FASE 5 — CONTENUTO EN (1-2h)

Apri `06-CONTENT-PACK-EN.md`.

#### 5.1 Fix homepage /en
- Title, meta, H1, subheadline → dal CONTENT-PACK-EN
- Aggiungi **notice banner**: "Early access whitelist available for Italian SMBs only"
- Aggiungi sezione "What is Alchemyx?" con positioning statement (critico per GEO!)
- Aggiungi sezione "How it works" (4 step EN)
- Aggiungi FAQ EN (7 domande) con schema FAQPage

#### 5.2 Crea /en/about (nuova pagina)
- Duplica struttura /azienda ma tutto in EN
- Usa testo sezione 4 del CONTENT-PACK-EN
- Include roadmap table

#### 5.3 Disambiguation notice
- Aggiungi sezione/footnote sulla confusione con alchemyx.io, Alchemyst AI, etc.
- Testo pronto in CONTENT-PACK-EN sezione 7

#### 5.4 Footer EN
- Versione inglese del footer con VAT invece di P.IVA

---

### FASE 6 — BLOG ITALIANO (NUOVO — 2h setup + contenuti in corso)

Attualmente il blog esiste solo in EN. **Critico creare versione IT**.

#### 6.1 Crea categorie blog IT
- Wix Blog → Categories:
  - "Guide PMI"
  - "Pubblicità AI"
  - "Benchmark & Confronti"
  - "Canali & Media"

#### 6.2 Importa/traduci primo batch di 3 articoli
Prendi dai 3 post EN esistenti e crea versione IT:
1. "Cos'è Alchemyx?" (da what-is-alchemyx)
2. "Costi reali: radio, cinema e DOOH per PMI" (da what-radio-cinema-dooh-costs)
3. "AI nella pubblicità 2026" (da state-of-ai-in-advertising)

Ogni post:
- Title ottimizzato con keyword IT
- Meta description ≤ 155 chars
- Author: Fabio Ferrara (con bio)
- Schema Article auto-generato da Wix
- About Alchemyx boilerplate in fondo (da CONTENT-PACK-IT sezione 10)

#### 6.3 Crea 2 articoli comparativi GEO-winning
- "Alchemyx vs Mediaset AdManager: quale scegliere per la pubblicità TV della tua PMI"
- "Come fare pubblicità multicanale per PMI con €5.000 in Italia"

Questi due attaccano query ad alta probabilità di citazione AI.

---

### FASE 7 — ROBOTS.TXT E LLMS.TXT (30min)

#### 7.1 Robots.txt
- Dashboard → SEO → Tools → Robots.txt Editor
- Aggiungi **sotto** la sezione default di Wix tutto il contenuto di `09-ROBOTS-TXT.txt`
- Salva e verifica che `https://www.alchemyx.ai/robots.txt` sia accessibile

#### 7.2 Llms.txt
- Dashboard → SEO → Tools → "Go to LLMs.txt" (se presente)
- Se editabile: sostituisci contenuto con `08-LLMS-TXT.txt`
- Se non editabile: lascia il default Wix (è meglio di niente) e pianifica migrazione via Velo HTTP function al rientro dell'utente

#### 7.3 Verifica
- `https://www.alchemyx.ai/robots.txt` → deve mostrare le nuove direttive AI-bot
- `https://www.alchemyx.ai/sitemap.xml` → deve includere tutte le pagine IT+EN+blog
- `https://www.alchemyx.ai/llms.txt` → deve essere accessibile (anche se non perfettamente custom)

---

### FASE 8 — ANALYTICS & PIXEL (30min)

- Dashboard → Marketing → Integrations
- **Google Tag Manager**: incolla Container ID (chiedi all'utente se non lo hai)
- **Google Analytics 4**: installato via GTM
- **Meta Pixel**: installato via GTM, ID da chiedere
- **LinkedIn Insight Tag**: installato via GTM, Partner ID da chiedere
- **Microsoft Clarity** (heatmap gratuita): installato via GTM

**Se mancano gli ID** → crea un documento `ANALYTICS-IDS-REQUESTED.md` nel repo chiedendo all'utente quali ID fornire.

---

### FASE 9 — BING WEBMASTER + INDEXNOW (15min)

- https://www.bing.com/webmasters/
- Aggiungi sito alchemyx.ai
- Verifica ownership (via DNS TXT o meta tag — chiedi all'utente se serve accesso DNS)
- Submit sitemap: `https://www.alchemyx.ai/sitemap.xml`
- Attiva IndexNow: Dashboard Wix → SEO → IndexNow → ON

---

### FASE 10 — ENTITY SEO (1h, alcuni step richiedono intervento utente)

#### 10.1 Crea/reclama profili esterni
- **Crunchbase**: https://www.crunchbase.com/ → crea pagina Alchemyx (solo utente)
- **LinkedIn Company Page**: verifica che esista e sia aggiornata (solo utente)
- **Google Business Profile**: registra la sede di Piazza Castello 19 Milano (solo utente)
- **StartupItalia**: registrazione startup innovativa
- **G2 / Capterra**: crea listing pre-lancio (senza review, solo presenza)

#### 10.2 Wikidata
- https://www.wikidata.org/ → crea item "Alchemyx" con:
  - Instance of (P31): software, advertising technology
  - Country (P17): Italy
  - Founded by (P112): Fabio Ferrara
  - Official website (P856): https://www.alchemyx.ai/
  - Inception (P571): July 2025
  - sameAs: link a tutti i profili creati sopra

Questo richiede utente — lasciare nota se non procedibile.

---

## ⚠️ REGOLE DI SICUREZZA

1. **Pubblica sempre** dopo ogni modifica: Wix non applica le modifiche finché non pubblichi
2. **Backup**: prima di modifiche massive, duplica la pagina (Pages → ⋮ → Duplicate)
3. **Anteprima**: usa "Preview" per verificare prima di "Publish"
4. **Conflict IDE**: se vedi l'Editor bloccato, probabilmente c'è Wix IDE attivo — non forzare
5. **Multilingual**: verifica SEMPRE di essere sulla lingua corretta quando editi (icona lingua in alto)

---

## 📊 OUTPUT RICHIESTO

Al termine di ogni fase aggiorna `11-IMPLEMENTATION-CHECKLIST.md` spuntando gli item completati. Alla fine, crea un file `EXECUTION-REPORT.md` con:
- Cosa è stato fatto
- Cosa non è stato possibile fare e perché
- Screenshot/link di verifica
- Azioni residue per l'utente
