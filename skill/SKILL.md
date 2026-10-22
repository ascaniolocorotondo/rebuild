---
name: rebuild
description: REbuild — costruisce da zero un programma gratuito che replica le funzioni principali di un software a pagamento (Photoshop, Office, Notion, Trello, FL Studio, Premiere, Canva, Todoist, YNAB, Figma, AutoCAD, Lightroom, ecc.) come app funzionante — di solito una web app in un solo file HTML, oppure uno script/app Python per Windows. Usa questa skill ogni volta che l'utente vuole "una versione gratis di X", "il mio Photoshop", "un clone di Notion", "qualcosa tipo Excel ma fatto da noi", "rifammi questo programma", "non voglio pagare l'abbonamento a X, creamelo", o chiede di costruire un'alternativa/equivalente/sostituto/clone a un'app commerciale, anche se non usa la parola "alternativa". Vale anche in inglese ("build me a free Trello", "make my own version of Notion"). Non usarla se l'utente vuole solo sapere quali alternative gratuite esistono già senza costruirle.
---

# REbuild — ricrea gratis i programmi a pagamento

Questa skill serve a **costruire** un equivalente funzionante di un programma commerciale, non a consigliarne uno esistente. L'obiettivo è che l'utente, alla fine, abbia in mano un'app che usa davvero al posto di quella a pagamento, per le cose che gli servono.

L'utente tipico non è uno sviluppatore: vuole aprire un file e usarlo. Per questo la scelta predefinita è un'app in **un unico file HTML** che si apre con doppio clic, funziona offline e salva i dati nel browser. Parla con l'utente nella sua lingua (spesso italiano) e senza gergo tecnico.

## Flusso di lavoro

### 1. Capire cosa serve davvero

Un programma come Photoshop ha migliaia di funzioni; l'utente ne usa una decina. Prima di scrivere codice, individua quelle.

- Apri [references/catalogo.md](references/catalogo.md) e cerca il programma (o la categoria più vicina). Lì trovi le funzioni essenziali, quelle "di livello 2" e lo stack consigliato.
- Se l'utente è stato specifico ("mi serve solo per ritagliare e scontornare le foto"), parti da lì e non chiedere altro.
- Se è vago ("fammi Photoshop"), proponi in un messaggio breve l'elenco delle funzioni essenziali dal catalogo e chiedi se aggiungere o togliere qualcosa. Una sola domanda, poi costruisci. Se l'utente ha già detto "fai tu", non chiedere: usa le funzioni essenziali del catalogo.

### 2. Scegliere la forma dell'app

Leggi [references/stack.md](references/stack.md) quando la scelta non è ovvia. In sintesi:

| Situazione | Forma |
|---|---|
| Quasi tutto: editor, organizer, calcoli, grafica, audio, note, kanban, fogli di calcolo | **Web app in un file HTML** (predefinita) |
| Serve accedere a file/cartelle del PC in blocco, processi di sistema, hardware, automazioni | **Script o app Python** (Tkinter o PySide6) |
| Elaborazioni ripetitive su molti file (convertire, rinominare, comprimere) | **Script Python da riga di comando**, con un `.bat` per avviarlo con doppio clic |
| L'utente vuole condividerla o usarla da più dispositivi | Web app pubblicata come Artifact, se lo strumento è disponibile |

Parti da [assets/template-app.html](assets/template-app.html) per le web app: contiene già barra degli strumenti, tema chiaro/scuro, salvataggio automatico, esporta/importa dati e scorciatoie da tastiera. Così ti concentri sulle funzioni vere invece di riscrivere ogni volta l'impalcatura.

### 3. Costruire per livelli

Costruisci prima la **versione essenziale, completa e funzionante**, poi aggiungi. Una versione piccola che funziona tutta vale molto più di una grande con metà dei pulsanti rotti: l'utente deve poterla usare subito.

- **Livello 1**: le funzioni essenziali, tutte funzionanti, con salvataggio dei dati ed esportazione nei formati standard (PNG/JPG, CSV/XLSX, PDF, MP3/WAV, JSON, Markdown…). I formati standard sono importanti perché l'utente non deve restare intrappolato nella nostra app più di quanto lo fosse in quella a pagamento.
- **Livello 2**: dopo che il livello 1 funziona, proponi le funzioni successive del catalogo e aggiungile se l'utente le vuole.

Regole pratiche che rendono l'app usabile davvero:
- **Annulla/Ripeti** (Ctrl+Z / Ctrl+Y) in ogni editor: senza, nessuno si fida a usarlo.
- **Salvataggio automatico** e conferma prima di perdere dati.
- **Scorciatoie da tastiera** uguali a quelle del programma originale (Ctrl+S, Ctrl+C, B per pennello, ecc.): l'utente le conosce già.
- **Disposizione familiare**: posiziona strumenti e pannelli dove l'utente se li aspetta, così non deve reimparare.
- Interfaccia **in italiano** se l'utente scrive in italiano.
- Gestisci file grandi senza bloccare la pagina (Web Worker, OffscreenCanvas, elaborazione a blocchi) quando l'app tratta immagini, audio o video.

### 4. Verificare

Prima di consegnare, apri l'app e provala: se hai il browser integrato, caricala e clicca le funzioni principali; controlla la console per errori. Per Python, eseguila almeno una volta. Correggi ciò che non va prima di dire che è pronta: un'app che si rompe al primo clic fa perdere fiducia all'utente.

### 5. Consegnare

- Salva i file in una cartella con un nome chiaro (es. `mio-photoshop/`).
- Spiega in 3-5 righe: come aprirla, cosa sa fare, dove salva i dati e come esportarli.
- Proponi in una riga le funzioni del livello 2 che si possono aggiungere.

## Cosa non fare (e perché)

Queste regole proteggono l'utente da problemi legali e di sicurezza:

- **Niente nomi, loghi, icone o grafica dei marchi originali.** Dai all'app un nome proprio (es. "Ritocco" invece di "Photoshop"). Replicare le *funzioni* è legittimo; copiare il *marchio* no.
- **Niente crack, keygen, aggiramento di licenze, DRM o periodi di prova**, e niente codice proprietario copiato. Se l'utente chiede questo, spiega che la skill costruisce un'alternativa nuova, non sblocca quella esistente.
- **Niente file o asset proprietari** (font, preset, campioni audio, template a pagamento): usa risorse libere (Google Fonts, suoni sintetizzati, icone open source).
- Se il programma dipende da un servizio online (es. sincronizzazione cloud, IA, banche), costruisci la parte locale e spiega onestamente cosa manca.

## Quando costruire non conviene

Alcuni programmi (motori 3D completi, montaggio video professionale 4K, CAD industriale, antivirus) sono troppo grandi per essere replicati in modo utile. In questi casi:
1. Costruisci comunque la parte che serve all'utente (es. un editor video che taglia, unisce e aggiunge testo con ffmpeg.wasm).
2. Di' chiaramente cosa la nostra versione non fa, e cita in una riga il progetto open source maturo che lo fa (es. Blender, DaVinci Resolve gratuito, FreeCAD), così l'utente ha una strada anche per i casi più pesanti.
