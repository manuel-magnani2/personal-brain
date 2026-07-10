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
sorgente-path: "percorso/relativo/al/file/grezzo.md"
sorgente-modificato: "YYYY-MM-DDTHH:MM"
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

### I campi `sorgente-path` e `sorgente-modificato`

Questi due campi esistono per un solo scopo: permettere ad `AGENTS.md` di rilevare in automatico, ad ogni avvio di sessione, se una fonte grezza è stata modificata dopo l'ultimo ingest o se esistono file nelle cartelle LEGGI mai processati. Non servono ad altro e non vanno usati per altre logiche.

- `sorgente-path`: percorso relativo alla root del vault del file grezzo da cui questa pagina è nata (es. `Mindset/atomic-habits-note.md`)
- `sorgente-modificato`: data e ora di ultima modifica del file grezzo, letta dal filesystem al momento dell'ingest — non inserita a mano

Compilali sempre, per ogni fonte. Se la fonte non proviene da un singolo file (es. testo incollato in chat, dialogo diretto senza file di origine), lascia entrambi i campi vuoti (`""`) — il rilevamento automatico li ignorerà semplicemente.

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
fonti-collegate: ["[[fonte-1]]"]
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

## Voce baseline in evoluzione.md (solo al primo ingest)

### Quando si applica
Prima di scrivere la voce specifica della fonte (fase 4 della skill), controlla `Wiki/evoluzione.md`: se contiene solo il placeholder iniziale (*"nessuna voce ancora"*), questo è il primo ingest mai eseguito su questo vault.

### Cosa scrivere
Una voce baseline che precede quella della fonte, con lo stesso formato standard di `evoluzione.md` (vedi `wiki-schema.md`), ma con contenuto diverso: non descrive la fonte appena processata, descrive lo **stato osservato del vault prima di questo ingest** — cosa emerge da `Profile/me.md` se esiste, quali cartelle raw sono già popolate, eventuali note che l'utente ha già scritto autonomamente nel vault prima di usare queste skill.

### Regola assoluta: niente placeholder sintetico
Se non c'è nulla di genuino da osservare — `Profile/me.md` non esiste o è vuoto, le cartelle raw sono vuote, non c'è alcuno stato pregresso — **non scrivere la baseline**. Una voce tipo *"sistema inizializzato, nessun dato pregresso"* non è una baseline, è un placeholder di processo, ed è esattamente ciò che la regola "niente entry sintetiche" vieta. In questo caso la prima voce reale di `evoluzione.md` è semplicemente quella della prima fonte ingerita — niente viene forzato prima.

### Esempio di quando ha senso
L'utente ha già scritto mesi di appunti in `Mindset/note-sparse.md` prima di configurare il Personal Brain. Il primo ingest legge quel materiale (o `Profile/me.md`, se contiene un autoritratto) e trova pattern reali già esistenti — quello è contenuto genuino, degno di una voce baseline.

### Esempio di quando NON ha senso
Vault appena creato con `/personal-brain-setup`, cartelle raw vuote, `Profile/me.md` assente. Non c'è nulla da osservare: si salta la baseline.

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
