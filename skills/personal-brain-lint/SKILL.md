---
name: personal-brain-lint
description: Verifica la salute e la coerenza della Wiki del Personal Brain. Controlla sincronizzazione index.md, wikilink rotti, vault-map aggiornata, attività di evoluzione.md, frontmatter delle pagine. Usa quando l'utente vuole fare manutenzione, dice "controlla la wiki", "lint", "salute del sistema", "/personal-brain-lint".
license: MIT
metadata:
  author: manuel-magnani2
  version: "1.0"
---

# Personal Brain — Lint

Sei il verificatore di salute della Wiki. Identifichi problemi strutturali e proponi correzioni — non le esegui automaticamente senza conferma.

Nota: questo lint non copre il rilevamento di fonti nuove o modificate rispetto al filesystem — quel controllo gira automaticamente ad ogni sessione, definito in `AGENTS.md`, non qui.

## Prima di iniziare

```
Leggi: Wiki/index.md
Leggi: Wiki/vault-map.md
Leggi: references/health-checks.md
```

## Procedura di lint

Esegui i check nell'ordine. Per ogni problema: descrivi, mostra l'istanza specifica, proponi la correzione.

### Check 1 — Vault-map sincronizzata

Scansiona le cartelle di primo livello del vault. Confronta con `Wiki/vault-map.md`.

- Cartelle presenti nel vault ma non in vault-map → **mappa obsoleta**
- Cartelle in vault-map che non esistono più → **voci orfane in mappa**

Fix automatico proposto: aggiorna `vault-map.md`.

### Check 2 — Index.md sincronizzato

Estrai i wikilink da `Wiki/index.md`. Elenca i file `.md` in `Wiki/fonti/`, `Wiki/concetti/`, `Wiki/sintesi/`. Confronta.

- File in Wiki non presenti in index → **index incompleto**
- Wikilink in index che non corrispondono a file reali → **voci orfane**

Fix automatico proposto (con conferma): aggiorna `index.md`.

### Check 3 — Wikilink rotti

Scansiona tutti i file `.md` in `Wiki/fonti/`, `Wiki/concetti/`, `Wiki/sintesi/` e i file speciali (`index.md`, `evoluzione.md`). Escludi `Wiki/sessioni/` — è un log di processo, non conoscenza curata, e non è soggetto a questo check. Per ogni `[[wikilink]]`, verifica che il file esista in `Wiki/`. Raggruppa i link rotti per file sorgente.

Fix: non automatico — l'utente decide se creare la pagina, aggiornare il link, o rimuoverlo.

### Check 4 — Evoluzione.md attiva

Leggi `Wiki/evoluzione.md`. Identifica la data dell'ultima voce (`## YYYY-MM-DD`).

- < 14 giorni: ✅ sistema attivo
- 14–30 giorni: ⚠️ sistema rallentato
- > 30 giorni: ❌ sistema inattivo

Fix: non automatico. Se inattivo, suggerisci un ingest.

### Check 5 — Frontmatter delle pagine

Campiona fino a 10 pagine per tipo (fonti, concetti, sintesi). Verifica che i campi obbligatori siano presenti e che `tipo` corrisponda alla cartella.

Vedi campi obbligatori per tipo in `references/health-checks.md`.

Fix automatico proposto (con conferma): aggiunge i campi mancanti con valore placeholder.

### Check 6 — Concetti stagnanti

Leggi tutti i file in `Wiki/concetti/`. Per quelli con `maturità: emergente`, controlla `data-aggiornamento`. Se > 60 giorni: segnala come stagnante.

Fix: non automatico — richiede riflessione dell'utente.

---

## Output del lint

```markdown
# Lint Report — YYYY-MM-DD

## ✅ Check superati
- [lista]

## ⚠️ Problemi trovati

### Vault-map
- [problema e proposta]

### Index.md
- [problema e proposta]

### Wikilink rotti
- [file sorgente] → [[link-rotto]]

### Evoluzione.md
- Ultima voce: YYYY-MM-DD ([N] giorni fa) — [stato]

### Frontmatter
- [pagine con campi mancanti]

### Concetti stagnanti
- [[nome-concetto]] — emergente da [N] giorni

## 🔧 Azioni proposte
1. [fix automatici sicuri — eseguo con conferma]
2. [fix che richiedono decisione tua]

Procedo con le correzioni automatiche per vault-map e index.md?
```

## Log di sessione

Al termine del lint (dopo il report, indipendentemente dal fatto che siano stati applicati fix), scrivi una voce in `Wiki/sessioni/YYYY-MM-DD.md` (crea il file se non esiste per oggi). Formato in `references/wiki-schema.md` della skill `personal-brain-setup`, sezione `Wiki/sessioni/`. Automatico, non richiede conferma.

## Regole

- Non correggere senza conferma esplicita
- Non cancellare mai pagine — solo segnalare quelle potenzialmente obsolete
- I wikilink rotti e i concetti stagnanti richiedono sempre decisione dell'utente
