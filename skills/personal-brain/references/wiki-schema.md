# Wiki Schema — Personal Brain

Questo file definisce le regole di navigazione del vault e le convenzioni per la Wiki. Non descrive una struttura fissa — la struttura la scopre l'AI e la documenta in `Wiki/vault-map.md`.

---

## Regole di navigazione (le uniche tre che contano)

### IGNORA
Qualsiasi cartella o file il cui nome inizia con `_` (underscore).
Sono cartelle di servizio (Obsidian, template, allegati). Non leggerle, non scriverci, non citarle nel lavoro sui contenuti — a meno che l'utente non le menzioni esplicitamente.

Esempi: `_Utility/`, `_Archivio/`, qualsiasi futura cartella `_*`.

### SCRIVI
Solo `Wiki/`. È l'unica area di output dell'AI. Scrittura libera, secondo le convenzioni di questa specifica.

### LEGGI
Tutto il resto — qualsiasi cartella o file che non inizia con `_` e non è `Wiki/`. L'AI legge, analizza, connette. Non scrive mai.

Questo include: `Profile/`, `Mindset/`, `Career/`, `Body/`, qualsiasi nuova cartella che l'utente aggiunge in futuro. Se una cartella esiste e non inizia con `_`, l'AI la considera fonte grezza da leggere.

---

## Scoperta della struttura e vault-map.md

Il vault evolve nel tempo. L'AI non porta con sé una mappa precotta — la costruisce e la aggiorna.

### Prima sessione (vault-map.md non esiste)
1. Scansiona tutte le cartelle di primo livello del vault
2. Applica le tre regole: classifica ogni cartella come IGNORA / LEGGI / SCRIVI
3. Crea `Wiki/vault-map.md` con la struttura scoperta

### Sessioni successive (vault-map.md esiste)
1. Leggi `Wiki/vault-map.md` come punto di partenza
2. Verifica se ci sono cartelle nuove non presenti nella mappa
3. Se trovi qualcosa di nuovo: aggiorna `vault-map.md` e segnalalo all'utente ("Ho trovato una nuova cartella: [nome]. La tratto come fonte grezza e aggiungo alla mappa.")

### Formato di vault-map.md

```markdown
---
tipo: mappa-vault
data-aggiornamento: YYYY-MM-DD
---

# Vault Map

*Mappa della struttura del vault. Aggiornata automaticamente dall'AI quando rileva cambiamenti.*

## Zona scrittura AI
- `Wiki/` — unica area di output

## Fonti grezze (lettura)
- `Profile/` — [descrizione breve del contenuto]
- `Mindset/` — [descrizione breve del contenuto]
- [altre cartelle scoperte...]

## Cartelle di servizio (ignorate)
- `_Utility/` — template e allegati Obsidian
- [altre cartelle `_*` scoperte...]

## File speciali alla root
- `AGENTS.md` — istruzioni operative per l'AI
- `.agents/` — skill (caricamento automatico, non navigare come contenuto)
```

---

## Tassonomia di Wiki/

### File speciali (sempre presenti)

**`Wiki/index.md`** — Catalogo master di tutto ciò che è nella Wiki. L'AI lo aggiorna ad ogni sessione.

```markdown
# Index — Personal Brain Wiki

*Ultima modifica: YYYY-MM-DD*

## Fonti ([N] totali)
- [[YYYY-MM-DD-titolo]] — breve descrizione (area)

## Concetti ([N] totali)
- [[nome-concetto]] — breve descrizione (maturità)

## Sintesi ([N] totali)
- [[tema-sintesi]] — breve descrizione
```

**`Wiki/evoluzione.md`** — Registro cronologico della crescita. Solo append in cima, mai modificare il passato.

```markdown
## YYYY-MM-DD — [titolo breve della sessione]

**Fonte/contesto:** [cosa è stato processato]
**Pattern emersi:** [comportamenti, pensieri, tendenze ricorrenti identificati]
**Insight chiave:** [la cosa più importante emersa]
**Domanda aperta:** [qualcosa che resta irrisolto o merita approfondimento]
**Dimensione:** mindset | career | body | emotivo | spirituale | trasversale

---
```

**`Wiki/vault-map.md`** — Mappa strutturale del vault, mantenuta dall'AI (vedi sezione sopra).

### Sottocartelle tematiche

**`Wiki/fonti/`** — Una pagina per ogni fonte processata via ingest.
Nome file: `YYYY-MM-DD-titolo-breve.md`

Frontmatter:
```yaml
---
tipo: fonte
titolo: "Titolo completo"
autore: "Nome Autore"
formato: libro | video | articolo | podcast | conversazione | corso
data-ingest: YYYY-MM-DD
area: [nome della cartella sorgente, es. mindset | career | body]
tags: []
---
```

**`Wiki/concetti/`** — Modelli mentali, framework, principi adottati.
Nome file: `nome-concetto.md`

Frontmatter:
```yaml
---
tipo: concetto
titolo: "Nome del concetto"
area: mindset | career | body | emotivo | spirituale | trasversale
fonti: ["[[fonte-1]]", "[[fonte-2]]"]
data-creazione: YYYY-MM-DD
data-aggiornamento: YYYY-MM-DD
maturità: emergente | consolidato | cristallizzato
tags: []
---
```

**`Wiki/sintesi/`** — Analisi tematiche trasversali (almeno 2-3 fonti o concetti collegati).
Nome file: `tema-sintesi.md`

Frontmatter:
```yaml
---
tipo: sintesi
titolo: "Tema della sintesi"
concetti-collegati: ["[[concetto-1]]", "[[concetto-2]]"]
fonti-collegate: ["[[fonte-1]]"]
data-creazione: YYYY-MM-DD
data-aggiornamento: YYYY-MM-DD
tags: []
---
```

---

## Regole per l'AI

1. **Le tre regole di navigazione sono assolute.** IGNORA / LEGGI / SCRIVI non ammettono eccezioni senza richiesta esplicita dell'utente.
2. **Aggiorna vault-map.md quando scopri nuove cartelle.** Il vault cresce — la mappa deve restare sincronizzata.
3. **Mai modificare le voci passate di `evoluzione.md`.** Solo append in cima.
4. **Sempre aggiornare `index.md`** dopo ogni sessione in cui vengono create o modificate pagine Wiki.
5. **Usare i wikilink** (`[[nome-pagina]]`) per connettere tutto ciò che è collegabile.
6. **Sondare sempre le dimensioni emotiva e spirituale** durante l'elaborazione — anche se il materiale sembra puramente tecnico o professionale.
7. **Non creare pagine per ogni dettaglio.** Preferire pagine consolidate con wikilink a una proliferazione di stub.
8. **Il contenuto delle fonti grezze è immutabile.** Non spostare, non modificare, non rinominare file fuori da `Wiki/`.

---

## Convenzioni di naming

- File: `kebab-case` (tutto minuscolo, trattini)
- Wikilink: nome file esatto senza estensione: `[[nome-file]]`
- Date: formato ISO `YYYY-MM-DD`
- Tag: italiano, minuscolo, senza spazi: `crescita-personale`, `mindset`, `abitudini`
