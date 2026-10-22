# REbuild

**REbuild** è una skill per Claude che costruisce da zero la tua versione gratuita dei programmi a pagamento: fotoritocco, fogli di calcolo, kanban, budget, musica e oltre 40 altri.

Sito: https://ascaniolocorotondo.github.io/rebuild/

## Come funziona

1. Chiedi a Claude, per esempio: «Fammi una versione gratis di Trello».
2. REbuild sceglie le funzioni che servono davvero, partendo da un catalogo di oltre 40 programmi.
3. Costruisce una versione base completa e la prova.
4. Ricevi un programma che si apre con doppio clic (web app in un solo file HTML) o un'app Python per Windows.

## Installazione

- **App Claude / claude.ai**: scarica [`rebuild.skill`](rebuild.skill) e caricalo in Impostazioni, nella sezione delle Skill.
- **Claude Code**: `unzip rebuild.skill -d ~/.claude/skills/`, oppure copia la cartella [`skill/`](skill) in `~/.claude/skills/rebuild`.

## Contenuto

| Percorso | Cosa contiene |
|---|---|
| `skill/SKILL.md` | Istruzioni della skill |
| `skill/references/catalogo.md` | Catalogo dei programmi: funzioni essenziali, livello 2, strumenti |
| `skill/references/stack.md` | Come scegliere tra web app e Python, librerie consigliate |
| `skill/assets/template-app.html` | Base di partenza per ogni web app |
| `demo/ritocco.html` | Ritocco, un editor di immagini costruito con REbuild |
| `index.html` | Il sito |

## Regole

REbuild replica le funzioni, non i marchi: niente loghi, crack, aggiramento di licenze o codice proprietario. I nomi dei programmi citati sono marchi dei rispettivi proprietari; il progetto non è affiliato a nessuno di loro.

## Licenza

MIT
