# Scegliere e usare lo stack

## Web app in un file HTML (predefinita)

**Perché**: si apre con doppio clic, non va installato niente, funziona su Windows, Mac e telefono, e può diventare un Artifact condivisibile.

Regole:
- Tutto in un file: CSS e JS inline; librerie da CDN (cdnjs.cloudflare.com, cdn.jsdelivr.net/npm, unpkg.com) **con versione esatta** (es. `tone@14.7.77`), mai "latest", così l'app non si rompe quando la libreria cambia.
- Se l'utente vuole l'app anche offline al 100%, scarica le librerie e incorporale nel file, oppure mettile accanto all'HTML in una cartella `lib/`.
- Dati: `localStorage` per impostazioni e dati piccoli (< 5 MB); **IndexedDB** per immagini, audio, cataloghi grandi (usa idb-keyval per semplicità). Avvolgi ogni accesso in try/catch. Offri sempre "Esporta backup" / "Importa backup" in JSON: i dati del browser possono sparire se l'utente pulisce la cache.
- File: `<input type="file">` e trascina-e-rilascia per aprire; download tramite `Blob` + link per salvare. In Chrome/Edge la File System Access API permette "Salva" sullo stesso file.
- Prestazioni: Web Worker per calcoli lunghi; virtualizza liste e griglie con migliaia di elementi; `requestAnimationFrame` per disegno e animazioni.

Librerie collaudate per categoria:

| Serve | Libreria |
|---|---|
| Disegno/grafica su tela | Canvas 2D, Fabric.js, Konva, Paper.js (vettoriale), perfect-freehand |
| 3D | three.js, three-bvh-csg |
| Editor di testo ricco | Tiptap, Quill, Editor.js (a blocchi) |
| Markdown | marked + DOMPurify |
| Fogli di calcolo | SheetJS (xlsx), HyperFormula |
| Grafici | Chart.js |
| PDF | pdf-lib (crea/modifica), PDF.js (visualizza), jsPDF |
| Word/PowerPoint | docx, mammoth, PptxGenJS |
| CSV | PapaParse |
| ZIP | JSZip |
| Audio/musica | Tone.js, Web Audio API, wavesurfer.js, lamejs |
| Video | ffmpeg.wasm, MediaRecorder |
| Trascina e ordina | SortableJS, interact.js |
| Calendario | FullCalendar, ical.js |
| Ricerca | MiniSearch |
| OCR | Tesseract.js |
| Database SQLite | sql.js |
| Archiviazione | idb-keyval |

## App Python per Windows

**Quando**: serve leggere/scrivere molte cartelle del PC, avviare programmi, usare ffmpeg nativo, hardware, o l'utente vuole una vera finestra di programma.

- Interfaccia: **Tkinter** (incluso in Python, nessuna installazione) per app semplici; **PySide6** per interfacce ricche.
- Librerie utili: Pillow (immagini), pypdf, python-docx, openpyxl, send2trash, httpx, cryptography, rembg, mutagen (tag audio).
- Consegna: un file `requirements.txt` e un `avvia.bat` che crea un ambiente virtuale, installa le dipendenze la prima volta e avvia l'app. Esempio:

```bat
@echo off
cd /d "%~dp0"
if not exist .venv (
  python -m venv .venv
  .venv\Scripts\pip install -r requirements.txt
)
.venv\Scripts\python app.py
```

- Se l'utente vuole un `.exe`: PyInstaller (`pyinstaller --onefile --windowed app.py`).
- Controlla che Python sia installato (`python --version`); se manca, suggerisci `winget install Python.Python.3.12`.
- Operazioni distruttive (cancellare, sovrascrivere, rinominare in blocco): mostra un'anteprima, chiedi conferma, usa il Cestino, e quando possibile offri "Annulla".

## Script da riga di comando

Per lavori in blocco senza interfaccia (converti 500 foto, unisci 30 PDF). Rendilo usabile anche da chi non usa il terminale: un `.bat` su cui trascinare file o cartelle (`%*` riceve i percorsi trascinati).
