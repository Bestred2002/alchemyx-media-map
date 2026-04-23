# ⚠️ Nota al rientro — Blocker sul push GitHub

**Data**: 2026-04-23

Durante il lavoro autonomo il push via **git CLI** e via **GitHub MCP** è stato bloccato con errore:

```
remote: Permission to Bestred2002/alchemyx-media-map.git denied to Bestred2002.
fatal: unable to access ... The requested URL returned error: 403

# e da MCP push_files / create_branch:
403 Resource not accessible by integration
```

Significa che il GitHub App installato sul repo **non ha permessi di scrittura** sul branch `claude/analyze-alchemyx-seo-UtNMx` per questo token.

## Come sbloccare (30 secondi)

1. Vai su GitHub → tuo profilo → **Settings → Applications → Installed GitHub Apps** (o Integrations)
2. Trova l'app di Claude / Anthropic
3. Click **Configure** → Repository access → verifica che `alchemyx-media-map` sia incluso
4. Permissions → abilita **Contents: Read & Write** e **Metadata: Read**
5. Save

In alternativa, se ha senso per il tuo account, crea un **Personal Access Token** (classic, scope `repo`) e configuralo nelle impostazioni di Claude Code.

## Come recuperare il lavoro se non sblocchi subito

Tutti i file dell'audit sono salvati nel sandbox locale in:
```
/home/user/alchemyx-media-map/alchemyx-site-seo-geo/
```

Per scaricarli puoi:

**Opzione A** — da Claude Code al rientro: chiedimi di creare un archivio `.tar.gz` e poi scaricarlo via Bash/cat (oppure ti mostro i file uno a uno e li copi a mano).

**Opzione B** — committo tutto su `master` via MCP (ma è rischioso, sporca la tree principale e non era l'intento).

**Opzione C** — una volta sbloccati i permessi, basta un singolo comando `git push` dal sandbox e tutto il lavoro finisce sul branch.

## File prodotti in questa sessione (filesystem sandbox)

Elenco aggiornato alla fine della sessione — vedi `00-INDEX.md`.
