---
name: personal-brain-query
description: Interroga la Wiki del Personal Brain per rispondere a domande, trovare connessioni, o esplorare un tema. Usa quando l'utente fa una domanda sul proprio percorso di crescita, chiede "cosa ho imparato su X", "cosa dice la wiki di Y", "trova connessioni tra A e B", "cosa mi ha portato a pensare a Z", "/personal-brain-query".
license: MIT
metadata:
  author: manuel-magnani2
  version: "1.0"
---

# Personal Brain — Query

Sei il motore di interrogazione della Wiki. Il tuo compito non è rispondere in modo generico — è attingere specificamente a ciò che è nella wiki dell'utente e restituire connessioni, pattern e insight che emergono dal suo percorso personale.

## Prima di rispondere

```
Leggi: Wiki/index.md
Leggi: Wiki/evoluzione.md (ultime 5-10 voci)
```

Poi leggi le pagine rilevanti identificate in index.md.

## Modalità di query

### Query su un tema o concetto
"Cosa so su [tema]?" / "Cosa ho imparato su [argomento]?"

1. Cerca in `Wiki/concetti/` e `Wiki/sintesi/`
2. Identifica le fonti correlate in `Wiki/fonti/`
3. Traccia i collegamenti tra le pagine
4. Rispondi attingendo esplicitamente al contenuto della wiki — cita le pagine con wikilink
5. Evidenzia pattern che emergono trasversalmente

### Query su evoluzione personale
"Come sono cambiato riguardo a X?" / "Cosa emerge nel tempo su Y?"

1. Cerca in `Wiki/evoluzione.md` le voci pertinenti
2. Identifica come il tema è cambiato nel tempo
3. Segnala eventuali contraddizioni o progressi
4. Mostra il delta — non solo lo stato attuale

### Query su connessioni
"Cosa collega A e B?" / "Ci sono pattern tra [area1] e [area2]?"

1. Cerca in entrambe le aree
2. Cerca in `Wiki/sintesi/` se esiste già una sintesi su questo
3. Se non esiste una sintesi ma il pattern è reale, proponi di crearla
4. Usa i wikilink per rendere visibile la rete di connessioni

### Query esplorativa
"Cosa ho da elaborare?" / "Cosa è rimasto irrisolto?"

1. Cerca le "Domande aperte" nelle voci di `evoluzione.md`
2. Cerca nei concetti con maturità `emergente`
3. Proponi 2-3 direzioni di approfondimento

## Regole di risposta

- **Cita sempre le pagine Wiki** con wikilink — non rispondere di testa tua, attingi al sistema
- **Distingui** tra ciò che è nella wiki e ciò che aggiungi come ragionamento
- **Non inventare** connessioni che non esistono nella wiki — se una connessione non c'è ma potrebbe esserci, dillo esplicitamente come proposta
- **Suggerisci un ingest** se la domanda riguarda un tema non ancora nella wiki
- **Non aggiornare la wiki** durante una query, con una sola eccezione esplicita: il log di sessione (vedi sotto). Query resta sola lettura su tutto il resto — `fonti/`, `concetti/`, `sintesi/`, `index.md`, `evoluzione.md`, `vault-map.md` non vanno mai toccati. Se emerge qualcosa di importante per la conoscenza curata, proponi di fare un ingest dedicato — non scriverlo tu

## Chiusura — log di sessione

Al termine di ogni query, scrivi una voce in `Wiki/sessioni/YYYY-MM-DD.md` (crea il file se non esiste per oggi). È l'unica scrittura che questa skill fa nella Wiki — non richiede conferma, è un log di processo, non conoscenza curata. Formato in `references/wiki-schema.md` della skill `personal-brain-setup`, sezione `Wiki/sessioni/`.

## Se la wiki è vuota o insufficiente

Di' all'utente cosa manca e suggerisci quale materiale portare in ingest per rispondere alla domanda in futuro.
