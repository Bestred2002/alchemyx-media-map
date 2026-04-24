# 03 — Audit Responsive / Resize / UX
## Alchemyx.ai — Wix Studio

> **Data audit**: 2026-04-24
> **Nota metodologica**: WebFetch bloccato da 403. Analisi basata su pattern noti di Wix Studio, dati da sub-agenti di ricerca, e best practice 2026. Alcune verifiche richiedono ispezione visiva diretta nel browser.

---

## 1. BREAKPOINT WIX STUDIO — COME FUNZIONA

Wix Studio usa un sistema di **breakpoint a cascata** (non mobile-first fisso come il Classic Editor):

| Breakpoint | Range | Nome nel pannello |
|---|---|---|
| Desktop | > 1024px | Desktop |
| Tablet | 768–1024px | Tablet |
| Mobile | < 768px | Mobile |

A differenza del Classic Editor (che aveva solo Desktop + Mobile separati), Studio permette di:
- Definire comportamenti diversi per ogni breakpoint
- Usare Flexbox e CSS Grid nativo
- Impostare proporzioni relative (%, vw, vh) invece di pixel fissi
- Creare container responsivi con `min-width` / `max-width`

---

## 2. PROBLEMI COMUNI SU SITI WIX STUDIO — CHECKLIST DI VERIFICA

Claude Co-work deve verificare visivamente questi punti nel browser e nell'editor:

### 2.1 Hero Section (Above the fold)
- [ ] **Mobile**: il testo H1 è leggibile senza zoom? (min 16px, idealmente 20px+)
- [ ] **Mobile**: il CTA button è facilmente cliccabile? (min 44×44px tap target)
- [ ] **Mobile**: l'immagine/video hero è nascosto o sostituito con immagine statica leggera?
- [ ] **Tablet**: il layout non è né troppo stretto né troppo largo?
- [ ] **Desktop 4K**: il container ha un `max-width` (es. 1440px) centrato?

### 2.2 Navigazione / Header
- [ ] **Mobile**: hamburger menu funzionante e accessibile?
- [ ] **Mobile**: il logo non è troppo grande (max 40px height consigliato)?
- [ ] **Mobile**: il menu a tendina non copre il contenuto principale?
- [ ] **Tablet**: la navigazione desktop è ancora leggibile o collassa a hamburger?

### 2.3 Sezioni di contenuto
- [ ] **Mobile**: le colonne si impilano verticalmente (1 colonna invece di 2-3)?
- [ ] **Mobile**: le card prodotto non sono troppo piccole (min 280px width)?
- [ ] **Mobile**: testo nei bottoni non viene troncato con "..."?
- [ ] **Mobile**: i form hanno input con `font-size: 16px` minimo? (sotto 16px iOS fa zoom automatico)

### 2.4 Form Whitelist
- [ ] **Mobile**: il form è completamente visibile senza scroll orizzontale?
- [ ] **Mobile**: i campi input sono abbastanza grandi per le dita?
- [ ] **Mobile**: il tasto Submit è visibile senza scrollare (above the fold su mobile)?
- [ ] **Tablet**: il form non è troppo stretto (min 320px, idealmente 400px)?

### 2.5 Footer
- [ ] **Mobile**: le colonne del footer si impilano?
- [ ] **Mobile**: i link sono abbastanza distanziati (min 8px gap)?
- [ ] Logo + P.IVA + copyright visibili su tutti i breakpoint?

---

## 3. ERRORI RESPONSIVI TIPICI WIX STUDIO DA CORREGGERE

### 3.1 Overflow orizzontale
**Sintomo**: scroll bar orizzontale su mobile
**Causa comune**: sezione con `width: 100vw` che non conta la scrollbar, o elemento assoluto fuori dal container
**Fix in Wix Studio**: seleziona il container problematico → Layout → imposta `overflow: hidden` oppure riduci il padding/margin dei figli

### 3.2 Testo che si sovrappone a immagini su mobile
**Causa**: overlay text posizionato in assoluto su un'immagine che ridimensiona in modo diverso
**Fix**: usare Wix's "Text on Image" component nativo o settare `position: relative` sul container con `min-height`

### 3.3 CTA button troppo piccolo su mobile
**Standard**: button tap target deve essere almeno **44×44px** (Apple HIG + Google Material)
**Fix in Wix Studio**: seleziona il button → Layout → imposta `min-height: 44px`, `padding: 12px 24px`

### 3.4 Font troppo piccoli su mobile
**Standard**: body text minimo 14px, idealmente 16px. H1 minimo 24px su mobile.
**Fix**: seleziona testo → cambia al breakpoint Mobile → imposta font-size corretto

### 3.5 Immagini non ottimizzate per mobile
**Best practice**: Wix auto-converte in WebP ma bisogna:
- Caricare immagini ad almeno 2× la dimensione display (per retina)
- Non caricare immagini 3000px su sezioni dove vengono visualizzate a 400px
- Usare il "focal point" di Wix per definire il punto di interesse dell'immagine su mobile

---

## 4. PERFORMANCE MOBILE — SPECIFICHE WIX STUDIO 2026

### Cosa Wix fa automaticamente
- ✅ Conversione WebP automatica
- ✅ Lazy loading su immagini fuori viewport
- ✅ HTTP/3 + Brotli compression
- ✅ CDN globale (Cloudflare)
- ✅ Turbo 3.0: pre-rendering edge delle pagine marketing statiche

### Cosa richiede intervento manuale
- ⚠️ **Video background**: disabilitare su mobile (impostazione per breakpoint nel pannello background)
- ⚠️ **Font Google**: limitare a max 2-3 varianti di peso (ogni peso = 1 request aggiuntiva)
- ⚠️ **App Wix installate**: ogni app aggiunge JS. Verificare nel Dashboard quali sono attive e disabilitare quelle non utilizzate in specifiche pagine
- ⚠️ **Custom Code in head**: ogni script GTM/pixel deve usare async/defer

---

## 5. UX TEASER — ANALISI CONVERSIONE

### Obiettivo pagine IT
Convertire PMI e Media a cliccare sulla whitelist. Il funnel è:
```
Atterraggio → Comprensione del prodotto → Fiducia → Azione (whitelist)
```

### Friction points comuni sui teaser site
1. **CTA non above the fold su mobile** — il visitatore mobile non vede il bottone whitelist senza scrollare
2. **Mancanza di social proof immediata** — PMI e Media vogliono vedere "chi ci ha già creduto"
3. **Copy troppo tecnico** — "AI Agents orchestrano il lifecycle" non parla alla PMI media
4. **Form troppo lungo** — ogni campo aggiuntivo riduce conversione del 10-15%
5. **Nessuna urgenza** — "registrazioni aperte fino a luglio 2026" è buona urgency, deve essere visibile

### Raccomandazioni UX specifiche
| Elemento | Stato attuale (stimato) | Raccomandazione |
|---|---|---|
| CTA above fold mobile | ⚠️ Da verificare | Deve essere visibile senza scroll |
| Numero campi form | ⚠️ Da verificare | Max 3 campi (nome, email, tipo azienda) |
| Social proof | ⚠️ Probabilmente assente in homepage | Aggiungere "6 PMI già in whitelist", "DCA Cinema partner" |
| Urgency | ✅ "Registrazioni aperte fino luglio 2026" | Renderlo visibile e contatore countdown |
| Differenziazione PMI vs Media | ⚠️ Da verificare | 2 CTA separate: "Sono una PMI" / "Sono un Media" |

---

## 6. SEPARAZIONE IT / EN — WHITELIST

### Requisito
- **IT**: form whitelist visibile e funzionante
- **EN**: NO form whitelist — solo pagine informative

### Come implementare in Wix Studio
1. Il form whitelist vive nelle pagine IT (`/pmi`, `/media`, homepage IT)
2. Le corrispondenti pagine EN (`/en`, `/en/post/*`) NON hanno il form
3. Il language switcher IT→EN reindirizza a versione EN senza form

**Verifica critica**: assicurarsi che nelle pagine EN il codice del form Wix non sia semplicemente "nascosto" con CSS (sarebbe comunque nel DOM e indicizzato), ma proprio assente dal layout EN.

In Wix Multilingual: nella versione EN di ogni pagina, rimuovere fisicamente il widget form dal canvas della versione EN (non solo nasconderlo visivamente).

---

## 7. CHECKLIST MOBILE PRIORITARIA PER CLAUDE CO-WORK

Queste verifiche devono essere fatte **nel browser** su alchemyx.ai prima di ogni altra modifica:

```
[ ] Aprire alchemyx.ai su iPhone (o Chrome DevTools → iPhone 14 Pro)
[ ] Verificare H1 leggibile senza zoom
[ ] Verificare CTA whitelist visibile above fold (senza scrollare)
[ ] Cliccare il CTA → form appare correttamente?
[ ] Compilare il form su mobile → submit funziona?
[ ] Aprire /pmi su mobile → stessa verifica
[ ] Aprire /agenzie su mobile → layout OK?
[ ] Aprire /media su mobile → layout OK?
[ ] Header hamburger → menu si apre e chiude?
[ ] Footer → P.IVA e contatti leggibili?
[ ] Scroll orizzontale assente su tutte le pagine?
[ ] /en (homepage EN) → NO form whitelist visibile?
```

---

*Continua in: `04-COMPETITOR-BENCHMARK.md` per analisi concorrenziale*
