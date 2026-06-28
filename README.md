# personal-brain

Un sistema di crescita personale continua mantenuto da LLM, basato sul [pattern LLM Wiki di Andrej Karpathy](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) e sul formato [Agent Skills](https://agentskills.io).

Adattato per la crescita personale integrale — mentale, fisica, emotiva, spirituale — con Obsidian come interfaccia di lettura.

## Prerequisiti

- **[Obsidian](https://obsidian.md)** — per navigare il vault
- **Un agente AI** — [OpenCode](https://opencode.ai), [Pi](https://pi.dev), [Claude Code](https://claude.ai/code), o qualsiasi agente compatibile con Agent Skills
- **[Node.js](https://nodejs.org)** — per il comando di installazione
- **Git** — per il versionamento del vault

## Installazione

```bash
npx skills add manuel-magnani2/personal-brain
```

Installa quattro skill nel tuo agente AI:

| Skill | Quando usarla |
|---|---|
| `/personal-brain` | Setup iniziale del vault (wizard guidato) |
| `/personal-brain-ingest` | Processa una fonte grezza nella wiki |
| `/personal-brain-query` | Interroga la wiki su un tema o domanda |
| `/personal-brain-lint` | Verifica salute e coerenza della wiki |

## Come funziona

```
Fonti grezze → Mindset/ Career/ Body/      (tu smisti, l'AI non scrive qui)
                       ↓
              /personal-brain-ingest        (l'AI elabora)
                       ↓
              Wiki/                         (l'AI scrive e mantiene)
              ├── index.md                  (catalogo aggiornato ad ogni sessione)
              ├── evoluzione.md             (registro cronologico della crescita)
              ├── fonti/                    (una pagina per fonte ingested)
              ├── concetti/                 (modelli mentali e framework adottati)
              └── sintesi/                  (analisi tematiche trasversali)
```

L'AI è il bibliotecario. Tu sei il curatore.

## Quick Start

1. **Installa le skill** (vedi sopra)
2. **Esegui il wizard**: digita `/personal-brain` nel tuo agente — ti guida attraverso il setup del vault
3. **Apri il vault in Obsidian**: File → Open Vault → seleziona la cartella
4. **Porta una fonte**: copia un file in `Mindset/`, poi esegui `/personal-brain-ingest`
5. **Sfoglia la wiki**: segui i `[[wikilink]]`, esplora il grafo in Obsidian

## Ispirato da

- [Andrej Karpathy — LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- [NicholasSpisak/second-brain](https://github.com/NicholasSpisak/second-brain)
- [Agent Skills open standard](https://agentskills.io)
- Framework "File over AI"
