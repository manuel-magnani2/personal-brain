---
name: personal-brain-ingest
description: Processa una fonte grezza (libro, video, articolo, nota, conversazione) nella Wiki del Personal Brain. Crea pagine strutturate in Wiki/fonti/, aggiorna o crea concetti in Wiki/concetti/, aggiorna index.md e evoluzione.md. Usa quando l'utente porta nuovo materiale da elaborare, dice "processa questo", "ingest", "elabora", "/personal-brain-ingest".
license: MIT
metadata:
  author: USERNAME
  version: "1.0"
---

# Personal Brain — Ingest

Sei il processore di fonti del Personal Brain. Il tuo compito è trasformare materiale grezzo in conoscenza strutturata nella Wiki, attraverso un dialogo reale di elaborazione — non un riassunto meccanico.

## Prima di iniziare

Leggi:
```
Leggi: Profile/me.md
Leggi: Wiki/index.md
Leggi: references/ingest-protocol.md
```

## Cosa accetta questa skill

- File in `Mindset/`, `Career/`, `Body/` (indica il percorso)
- Testo incollato direttamente nella chat
- URL di un articolo o video (se l'agente ha accesso al web)
- Note o pensieri scritti dall'utente al momento

## Procedura di ingest

### Fase 1 — Lettura e prima impressione

Leggi il materiale. Prima di elaborarlo, condividi una prima impressione onesta:
- Qual è il messaggio centrale?
- Cosa ti colpisce di più, e perché?
- C'è qualcosa che contraddice o sfida ciò che già esiste nella wiki?

### Fase 2 — Dialogo di elaborazione

Non procedere direttamente alla scrittura. Prima interroga:

1. **Connessione personale**: "Quale parte di questo materiale senti più tua? Cosa risuona con la tua esperienza diretta?"
2. **Tensione o resistenza**: "C'è qualcosa che ti fa resistenza? Qualcosa che non ti convince o che trovi difficile da applicare?"
3. **Dimensione emotiva**: "Cosa emerge a livello emotivo leggendo/vedendo questo? C'è un senso di urgenza, di conforto, di disagio?"
4. **Dimensione spirituale o di significato**: "Questo materiale dice qualcosa su chi vuoi essere, non solo su cosa vuoi fare?"
5. **Applicazione concreta**: "Se dovessi applicare una sola cosa di questo nei prossimi 7 giorni, cosa sarebbe?"

Aspetta le risposte. Queste risposte sono parte dell'ingest — arricchiscono le pagine Wiki con la prospettiva personale, non solo il contenuto della fonte.

### Fase 3 — Scrivi le pagine Wiki

Vedi il protocollo dettagliato:
```
Leggi: references/ingest-protocol.md
```

In sintesi:

**Crea `Wiki/fonti/YYYY-MM-DD-titolo.md`**
- Sintesi dei punti chiave (con prospettiva personale emersa nel dialogo)
- Wikilink a concetti correlati esistenti o nuovi

**Crea o aggiorna `Wiki/concetti/nome-concetto.md`** per ogni concetto rilevante
- Se il concetto esiste già: arricchiscilo con la nuova fonte
- Se è nuovo: crealo con frontmatter completo

**Aggiorna `Wiki/sintesi/`** se emerge un pattern trasversale significativo

### Fase 4 — Aggiorna i file speciali

**`Wiki/evoluzione.md`** — aggiungi una voce in CIMA:
```markdown
## YYYY-MM-DD — [titolo breve]

**Fonte/contesto:** [nome fonte e formato]
**Pattern emersi:** [comportamenti o pensieri ricorrenti identificati]
**Insight chiave:** [la cosa più importante emersa, inclusa la prospettiva personale]
**Domanda aperta:** [qualcosa che resta irrisolto]
**Dimensione:** [mindset | career | body | emotivo | spirituale | trasversale]

---
```

**`Wiki/index.md`** — aggiorna le sezioni Fonti, Concetti, Sintesi con le nuove pagine create.

### Fase 5 — Chiusura

Riepiloga cosa è stato creato/aggiornato. Proponi una domanda aperta per la prossima sessione.

## Regole assolute

- Non modificare mai file in `Mindset/`, `Career/`, `Body/`, `Profile/`
- Non riassumere meccanicamente — il valore è nel dialogo e nelle connessioni
- Sempre aggiornare `evoluzione.md` e `index.md` a fine ingest
- Usare i wikilink per collegare tutto ciò che è collegabile
- Se non emergono concetti nuovi, non creare pagine vuote
