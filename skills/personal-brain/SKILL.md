---
name: personal-brain
description: Setup e onboarding del vault Personal Brain. Crea la Wiki, genera AGENTS.md, costruisce la vault-map iniziale. Usa quando l'utente vuole configurare il vault da zero, eseguire il setup iniziale, o rigenerare AGENTS.md. Trigger quando l'utente dice "setup", "inizia", "configura il vault", "/personal-brain".
license: MIT
metadata:
  author: manuel-magnani2
  version: "1.0"
---

# Personal Brain — Setup Wizard

Sei il wizard di configurazione del sistema Personal Brain. Il tuo compito è tre cose e solo tre: creare la struttura minima della Wiki, generare AGENTS.md, costruire la vault-map iniziale. Non devi creare la struttura delle cartelle raw — quelle le decide e le crea l'utente.

## Prima di iniziare

```
Leggi: references/wiki-schema.md
```

Poi conferma con l'utente di essere nella directory radice del vault corretta.

---

## Procedura di setup

### Passo 1 — Scansiona il vault

Elenca tutte le cartelle e i file presenti alla root. Applica le tre regole:
- Inizia con `_` → IGNORA
- È `Wiki/` → SCRIVI
- Tutto il resto → LEGGI (fonte grezza)

Mostra all'utente cosa hai trovato e come hai classificato ogni elemento.

### Passo 2 — Crea la struttura minima di Wiki/

Crea solo queste cartelle e file se non esistono già. **Non sovrascrivere mai file esistenti.**

```
Wiki/
  fonti/
  concetti/
  sintesi/
```

Crea `Wiki/index.md`:
```markdown
---
tipo: index
data-aggiornamento: YYYY-MM-DD
---

# Index — Personal Brain Wiki

*Catalogo master. Aggiornato dall'AI ad ogni sessione.*

## Fonti (0 totali)

## Concetti (0 totali)

## Sintesi (0 totali)
```

Crea `Wiki/evoluzione.md`:
```markdown
---
tipo: evoluzione
---

# Evoluzione

*Registro cronologico della crescita. Le voci più recenti sono in cima. Solo append — il passato non si modifica.*

---

*(nessuna voce ancora — il registro si popola con l'uso)*
```

### Passo 3 — Crea Wiki/vault-map.md

Costruisci la mappa del vault a partire dalla scansione del Passo 1:

```markdown
---
tipo: mappa-vault
data-aggiornamento: YYYY-MM-DD
---

# Vault Map

*Mappa della struttura del vault. Aggiornata dall'AI quando rileva cambiamenti.*

## Zona scrittura AI
- `Wiki/` — wiki mantenuta dall'AI

## Fonti grezze (lettura)
[lista delle cartelle trovate che non iniziano con _ e non sono Wiki/]

## Cartelle di servizio (ignorate)
[lista delle cartelle trovate che iniziano con _]

## File speciali alla root
- `AGENTS.md` — istruzioni operative per l'AI
- `.agents/` — skill (caricamento automatico)
[altri file trovati alla root]
```

### Passo 4 — Genera AGENTS.md

Leggi il template:
```
Leggi: references/agents-template.md
```

Crea `AGENTS.md` alla root del vault con il contenuto del template. Se `AGENTS.md` esiste già, chiedi conferma prima di sovrascrivere.

### Passo 5 — Riepilogo

Elenca cosa è stato creato e cosa già esisteva. Mostra il passo successivo:

> "Il vault è configurato. Porta del materiale in una delle cartelle raw e usa `/personal-brain-ingest` per iniziare."

---

## Regole

- Non creare cartelle raw (`Mindset/`, `Career/`, `Body/`, ecc.) — quelle le crea l'utente quando vuole
- Non sovrascrivere file esistenti senza conferma esplicita
- Il wizard è idempotente: rieseguirlo non causa danni
