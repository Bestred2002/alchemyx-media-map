# 11 — Implementation Checklist
## To-do ordinata per priorità

> Spuntare ogni item mentre viene completato. La numerazione corrisponde alle FASI del `10-WIX-STUDIO-PLAYBOOK.md`.

---

## 🔥 URGENTE — Da fare entro 24h (quick wins)

- [ ] Fix title EN homepage (è in italiano! bug grave)
- [ ] Fix typo "Perchè" → "Perché" in /media
- [ ] Correggi slug /en/contatti → /en/contact + redirect 301
- [ ] Allinea prezzi ovunque (13,98% + €2.000) — rimuovi €2.284 e 13,8%
- [ ] Verifica robots.txt attuale e sostituisci con versione raccomandata (file 09)
- [ ] Crea/sostituisci llms.txt (file 08) — o verifica auto-generato Wix
- [ ] Aggiungi schema Organization + WebSite su homepage (BLOCCO 1 file 07)
- [ ] Aggiungi schema SoftwareApplication su homepage + /pmi (BLOCCO 2)
- [ ] Aggiungi schema FAQPage su homepage (BLOCCO 3)

## 🟧 ALTA PRIORITÀ — Entro 7 giorni

- [ ] Aggiungi sezione FAQ (7 domande IT) in homepage — copy da file 05
- [ ] Aggiungi sezione FAQ (7 domande EN) in /en — copy da file 06
- [ ] Aggiorna H1 homepage IT e EN con claim ottimizzato
- [ ] Aggiorna copy /pmi con nuovo positioning
- [ ] Aggiungi schema Person per Fabio Ferrara e Davide Catalano su /azienda
- [ ] Crea form whitelist in Wix Forms (Nome, Email, Settore, Consent)
- [ ] Incorpora form SOLO su pagine IT (homepage, /pmi, /media)
- [ ] Verifica che /en/* NON mostri il form whitelist
- [ ] Installa GTM container + collega GA4 + Meta Pixel + LinkedIn Insight + Clarity
- [ ] Configura evento `whitelist_signup` con segment (pmi/media/agenzia)
- [ ] Registra alchemyx.ai su Bing Webmaster Tools + submit sitemap
- [ ] Attiva IndexNow in Wix Dashboard

## 🟨 MEDIA PRIORITÀ — Entro 30 giorni

- [ ] Crea pagina /en/about (non esiste) — copy da file 06 sezione 4
- [ ] Crea pagina /en/smb (equivalente EN di /pmi)
- [ ] Crea pagina /en/agencies (equivalente EN di /agenzie)
- [ ] Crea pagina /en/media-partners (equivalente EN di /media)
- [ ] Aggiungi disambiguation notice su /en e /en/about
- [ ] Crea categorie blog IT (Guide PMI, Pubblicità AI, Benchmark, Canali)
- [ ] Pubblica primo articolo IT: "Cos'è Alchemyx? Guida completa"
- [ ] Pubblica secondo articolo IT: "Costi reali pubblicità radio cinema DOOH"
- [ ] Pubblica terzo articolo IT: "AI nella pubblicità 2026 — stato dell'arte"
- [ ] Pubblica articolo comparativo: "Alchemyx vs Mediaset AdManager"
- [ ] Pubblica articolo guida: "Come fare pubblicità multicanale PMI con €5.000"
- [ ] Crea profilo Crunchbase e link a sito
- [ ] Aggiorna LinkedIn Company Page con tutti i campi
- [ ] Registra Google Business Profile (sede Milano)
- [ ] Crea listing pre-lancio su G2 e Capterra
- [ ] Crea profilo StartupItalia
- [ ] Sottometti a directory: Italian Tech, Atoka, Cerved

## 🟩 BASSA PRIORITÀ — Entro 90 giorni

- [ ] Crea item Wikidata per Alchemyx (richiede intervento manuale utente)
- [ ] Distribuisci comunicato stampa via Business Wire o PR Newswire
- [ ] Outreach a CorCom, Wired IT, Il Sole 24 Ore per copertura
- [ ] Registra domain `alchemyx.com` e fai redirect 301 a alchemyx.ai (proteggere brand)
- [ ] Registra domain `alchemyst-lab.com` e fai redirect
- [ ] Bookmark pattern: aggiungi blog IT con cadenza minima 2 post/mese
- [ ] Setup Consent Mode v2 (GDPR) su cookie banner Wix
- [ ] Aggiungi case study numerico (quando primi pilot disponibili)
- [ ] Implementa referral queue sul form whitelist (Viral Loops o simile)
- [ ] Speaker engagement: SMAU, IAB Forum, Marketers

## 📝 REVIEW E REPORT

- [ ] Al termine di FASE 2: testa tutti gli schema su validator.schema.org
- [ ] Al termine di FASE 3: controllo visivo homepage IT su mobile + desktop + tablet
- [ ] Al termine di FASE 5: controllo visivo /en su mobile + desktop
- [ ] Al termine di FASE 7: verifica `alchemyx.ai/robots.txt` accessibile e corretto
- [ ] Al termine di FASE 8: test evento `whitelist_signup` su GA4 DebugView
- [ ] **Report finale**: crea `EXECUTION-REPORT.md` nel repo con cosa fatto, cosa no, residuali

## 🚨 ROADBLOCKS NOTI (da gestire)

1. **Wix IDE vs GitHub integration** — sono mutuamente esclusivi. Se usi Velo IDE non puoi usare GitHub sync e viceversa.
2. **llms.txt custom** — Wix genera auto ma scarsamente customizzabile. Soluzione completa richiede Velo HTTP function.
3. **Pagine EN mancanti** — se sono thin (<300 parole) non aggiungono SEO, meglio pianificare contenuto sostanziale.
4. **Referral queue sul form** — Wix Forms non supporta nativamente, serve integrazione con Viral Loops o custom Velo.
5. **Disambiguation alchemyx.io** — è un dominio `.io` legittimo di un altro prodotto. Non si può rimuovere, solo differenziarsi nettamente con schema + contenuto.
