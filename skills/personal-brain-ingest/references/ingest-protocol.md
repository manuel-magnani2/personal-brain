# Ingest Protocol — Specifica Dettagliata

Questo file definisce le regole precise per la scrittura delle pagine Wiki durante l'ingest.

---

## Pagina fonte (`Wiki/fonti/`)

### Quando crearla
Per ogni fonte processata: libro, video, articolo, podcast, conversazione significativa, sessione di formazione.

### Nome file
`YYYY-MM-DD-titolo-breve.md`
- Data: giorno dell'ingest (non di pubblicazione della fonte)
- Titolo: kebab-case, massimo 5 parole

### Struttura

```markdown
---
tipo: fonte
titolo: "Titolo completo della fonte"
autore: "Nome Autore"
formato: libro | video | articolo | podcast | conversazione | corso
data-ingest: YYYY-MM-DD
area: mindset | career | body | trasversale
tags: []
---

# [Titolo]

## Punti chiave

[3-7 punti, non un riassunto esaustivo. Seleziona ciò che è più rilevante per la crescita personale dell'utente, non ciò che è più importante "in assoluto".]

## Prospettiva personale

[Cosa ha detto l'utente durante il dialogo di elaborazione. Questo è il valore aggiunto rispetto alla fonte originale — la voce personale che trasforma informazione in conoscenza.]

## Connessioni

- [[concetto-1]] — come si collega
- [[concetto-2]] — perché è rilevante
- [[altra-fonte]] — punto di contatto o tensione

## Domanda aperta

[La domanda con cui si chiude questa fonte — da riprendere in sessioni future.]
```

---

## Pagina concetto (`Wiki/concetti/`)

### Quando crearla
Quando emerge un modello mentale, framework, principio o idea che potrebbe cambiare il modo di pensare o agire. Non creare concetti per ogni termine tecnico — solo per ciò che ha valore operativo.

### Quando aggiornare un concetto esistente
Sempre che una nuova fonte porta un punto di vista nuovo, un esempio concreto, o mette in tensione il concetto esistente. Non riscrivere — arricchire.

### Livelli di maturità
- `emergente`: comparso una volta, non ancora validato dall'esperienza
- `consolidato`: comparso più volte, parzialmente applicato
- `cristallizzato`: integrato nel comportamento quotidiano

### Struttura

```markdown
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

# [Nome concetto]

## Definizione

[Cosa significa in modo chiaro e diretto. Non la definizione accademica — quella personale, contestualizzata.]

## Perché è rilevante

[Cosa cambia sapere/applicare questo. Connessione esplicita con i pattern personali dell'utente dove rilevante.]

## Come si applica

[Esempi concreti. Almeno uno tratto dall'esperienza o contesto personale.]

## Tensioni e limiti

[Cosa questo concetto non cattura. Dove potrebbe essere sbagliato o parziale. Dove entra in tensione con altri concetti nella wiki.]

## Fonti

[Wikilink alle fonti da cui viene. Aggiornato ad ogni nuova fonte che tocca questo concetto.]
```

---

## Pagina sintesi (`Wiki/sintesi/`)

### Quando crearla
Solo quando emerge un pattern trasversale chiaro che connette almeno 2-3 fonti o concetti. Non è un riassunto — è una riflessione tematica che aggiunge insight rispetto alle singole parti.

Esempi di quando ha senso:
- Tre libri diversi convergono sullo stesso principio di comportamento
- Si nota una tensione ricorrente tra due aree della propria vita
- Un tema emerge trasversalmente tra mindset, career e body

### Struttura

```markdown
---
tipo: sintesi
titolo: "Tema della sintesi"
concetti-collegati: ["[[concetto-1]]", "[[concetto-2]]"]
fonti-collegate: ["[[fonte-1]]", "[[fonte-2]]"]
data-creazione: YYYY-MM-DD
data-aggiornamento: YYYY-MM-DD
tags: []
---

# [Titolo sintesi]

## Il pattern

[Descrizione del tema trasversale. Cosa lega queste fonti/concetti oltre il contenuto esplicito?]

## Evidenze

[Le connessioni concrete tra le fonti/concetti che supportano questo pattern.]

## Implicazioni personali

[Cosa significa questo pattern per la propria crescita. Cosa suggerisce di fare o smettere di fare.]

## Domande aperte

[Ciò che questa sintesi lascia irrisolto o che merita ulteriore esplorazione.]
```

---

## Regole di naming per i wikilink

- Usa sempre il nome file esatto, senza estensione: `[[nome-file]]`
- Per le fonti, usa il nome completo con data: `[[2026-06-01-atomic-habits]]`
- Per i concetti, usa il nome del concetto: `[[identita-basata-su-sistema]]`
- Per le sintesi, usa il titolo breve: `[[pattern-evitamento-conflitto]]`
- I wikilink rotti non sono un errore grave — meglio crearli e risolverli con il lint

---

## Priorità durante l'ingest

1. **Dialogo prima di scrittura** — le risposte dell'utente sono il contenuto più prezioso
2. **Connessioni prima di nuovi file** — controlla sempre index.md per vedere cosa già esiste
3. **Qualità prima di quantità** — meglio una pagina ben scritta che tre stub
4. **Evoluzione.md sempre** — è il registro della crescita, non può mancare mai
