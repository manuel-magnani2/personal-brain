# Health Checks — Specifica Dettagliata

---

## Check 1 — Vault-map sincronizzata

**Severità: alta**

`vault-map.md` è il punto di orientamento dell'AI all'avvio di ogni sessione. Se non è aggiornata, l'AI può ignorare cartelle nuove o cercare cartelle che non esistono più.

Procedura:
1. Scansiona le cartelle di primo livello del vault (escluse quelle nascoste tecniche come `.agents/`, `.git`)
2. Applica le tre regole di navigazione: `_*` → ignora, `Wiki/` → scrivi, resto → leggi
3. Confronta con le sezioni di `Wiki/vault-map.md`

Problemi:
- **Cartella non mappata**: esiste nel vault ma non in vault-map → aggiungila alla sezione corretta
- **Voce orfana**: in vault-map ma non nel vault → rimuovila

Fix automatico proposto: aggiorna `vault-map.md` direttamente con conferma dell'utente.

---

## Check 2 — Index.md sincronizzato

**Severità: alta**

Procedura:
1. Estrai tutti i `[[wikilink]]` da `Wiki/index.md`
2. Elenca i file `.md` reali in `Wiki/fonti/`, `Wiki/concetti/`, `Wiki/sintesi/`
3. Confronta

Problemi:
- **File non in index**: file esiste, non è in index → aggiungilo
- **Voce orfana**: link in index, file non esiste → rimuovi o crea il file

Fix automatico proposto: aggiorna `index.md` con conferma.

---

## Check 3 — Wikilink rotti

**Severità: media**

Procedura:
1. Scansiona tutti i `.md` in `Wiki/`
2. Per ogni `[[testo]]` trovato, cerca `Wiki/**/testo.md` (case-insensitive, ignora estensione)
3. Riporta i non trovati raggruppati per file sorgente

Fix: non automatico. L'utente decide per ogni link rotto:
- Creare la pagina mancante
- Aggiornare il link a una pagina esistente
- Rimuovere il link

---

## Check 4 — Evoluzione.md attiva

**Severità: alta**

Procedura:
1. Leggi `Wiki/evoluzione.md`
2. Identifica la data dell'ultima voce `## YYYY-MM-DD`
3. Calcola i giorni trascorsi rispetto alla data odierna

Soglie:
- < 14 giorni: ✅ attivo
- 14–30 giorni: ⚠️ rallentato (segnala)
- > 30 giorni: ❌ inattivo (segnala con forza — il sistema non sta funzionando)

Fix: suggerisci un ingest. Non automatizzabile.

---

## Check 5 — Frontmatter delle pagine

**Severità: media**

Campi obbligatori per tipo:

| Tipo | Campi obbligatori |
|---|---|
| `fonte` | `tipo`, `titolo`, `autore`, `formato`, `data-ingest`, `area` |
| `concetto` | `tipo`, `titolo`, `area`, `data-creazione`, `data-aggiornamento`, `maturità` |
| `sintesi` | `tipo`, `titolo`, `data-creazione`, `data-aggiornamento` |

Verifica anche:
- `tipo` corrisponde alla cartella di appartenenza
- Le date sono in formato `YYYY-MM-DD`
- `maturità` nei concetti è uno di: `emergente`, `consolidato`, `cristallizzato`

Fix automatico proposto (con conferma): aggiunge campi mancanti con valore `TODO`.

---

## Check 6 — Concetti stagnanti

**Severità: bassa**

Procedura:
1. Leggi tutti i file in `Wiki/concetti/`
2. Filtra quelli con `maturità: emergente`
3. Calcola giorni da `data-aggiornamento`

Soglie:
- 30–60 giorni: segnala come "da rivedere"
- > 60 giorni: segnala come "stagnante"

Fix: non automatico. Opzioni per ogni concetto stagnante:
- Promuovere a `consolidato` se l'esperienza lo giustifica
- Archiviare in `Wiki/sintesi/` se è diventato parte di un pattern più ampio
- Lasciare emergente se è ancora irrisolto

---

## Ordine di priorità dei fix

Quando si propongono correzioni, usare questo ordine:

1. **Vault-map** — fix automatico safe, impatto alto sull'orientamento AI
2. **Index.md** — fix automatico safe, impatto alto sulla navigazione
3. **Frontmatter mancante** — fix automatico safe, impatto medio
4. **Wikilink rotti** — richiede decisione umana
5. **Evoluzione.md inattiva** — richiede azione umana (ingest)
6. **Concetti stagnanti** — bassa urgenza, richiede riflessione
