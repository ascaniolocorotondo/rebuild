# Catalogo dei programmi da ricreare

Per ogni programma: **Essenziali** (livello 1, da costruire subito), **Livello 2** (da proporre dopo), **Stack** (forma e librerie consigliate; dettagli in `stack.md`). "HTML" = web app in un solo file. Se il programma richiesto non c'è, usa la voce più simile della stessa categoria come modello.

## Indice
1. Grafica e foto
2. Design e disegno vettoriale
3. Ufficio e documenti
4. Produttività e organizzazione
5. Finanze
6. Audio e musica
7. Video
8. Sviluppo e strumenti tecnici
9. Sistema e file
10. Studio e insegnamento
11. 3D e CAD
12. Comunicazione e marketing

---

## 1. Grafica e foto

### Photoshop (fotoritocco)
- **Essenziali**: apri/trascina immagine; livelli (aggiungi, nascondi, opacità, riordina); pennello, gomma, secchiello, contagocce; selezione rettangolare/ellittica/lazo; ritaglia, ridimensiona, ruota; luminosità/contrasto/saturazione/tonalità; testo; annulla/ripeti con cronologia; esporta PNG/JPG/WebP; zoom e pan.
- **Livello 2**: metodi di fusione dei livelli; maschere; bacchetta magica; timbro clone; sfocatura/nitidezza; curve e livelli; rimozione sfondo (modello ONNX con onnxruntime-web, o algoritmo a soglia di colore); salvataggio progetto con livelli (JSON + immagini base64).
- **Stack**: HTML + Canvas 2D (OffscreenCanvas per filtri pesanti). Nessuna libreria obbligatoria.

### Lightroom (sviluppo e catalogo foto)
- **Essenziali**: importa cartella di foto (input `webkitdirectory`); griglia miniature; valutazione a stelle ed etichette; regolazioni non distruttive (esposizione, contrasto, temperatura, tinta, alte luci/ombre, vibranza, nitidezza) con anteprima e prima/dopo; preset salvabili; esportazione in blocco ridimensionata.
- **Livello 2**: istogramma; curve; ritaglio con raddrizzamento; copia/incolla regolazioni tra foto; lettura dati EXIF (exifr).
- **Stack**: HTML + WebGL (shader per regolazioni in tempo reale) o Canvas 2D; IndexedDB per il catalogo.

### Canva
- **Essenziali**: tela con formati preimpostati (post Instagram, storia, A4, banner YouTube); testo con Google Fonts; forme; immagini caricate; allineamento e guide; livelli/porta avanti-indietro; modelli di partenza creati da te; esporta PNG/PDF.
- **Livello 2**: gruppi; effetti testo (ombra, contorno); griglie e cornici foto; palette colori del brand; più pagine.
- **Stack**: HTML + Fabric.js; jsPDF per il PDF.

### Remove.bg / scontorno
- **Essenziali**: carica immagine, rimozione sfondo automatica, ritocco manuale (pennello mantieni/rimuovi), sfondo trasparente o colore, esporta PNG.
- **Stack**: HTML + @imgly/background-removal (modello in browser) oppure Python + rembg.

### TinyPNG / compressori immagini
- **Essenziali**: trascina molte immagini, qualità regolabile, ridimensiona, converti in WebP/JPG/PNG, mostra risparmio in %, scarica tutto in ZIP.
- **Stack**: HTML + Canvas (`toBlob` con qualità) + JSZip; oppure Python + Pillow per cartelle intere.

## 2. Design e disegno vettoriale

### Illustrator
- **Essenziali**: strumento penna (curve di Bézier) e modifica punti; forme; riempimento/traccia; livelli; testo; allinea e distribuisci; operazioni booleane (unisci, sottrai, interseca); esporta SVG/PNG/PDF.
- **Livello 2**: sfumature; testo su tracciato; simboli/componenti; importa SVG.
- **Stack**: HTML + Paper.js (booleane incluse) o SVG puro.

### Figma (interfacce e prototipi)
- **Essenziali**: tavole (frame) di dimensioni dispositivo; rettangoli, testo, immagini; vincoli base; componenti riutilizzabili; ispettore proprietà (colori, bordi, raggio, ombra); allineamento intelligente; esporta PNG/SVG; prototipo cliccabile (collegamenti tra frame + modalità presentazione).
- **Livello 2**: auto layout (flexbox); stili condivisi; commenti; esporta CSS dei componenti.
- **Stack**: HTML con DOM/SVG; interact.js per trascina/ridimensiona.

### Procreate / app di disegno
- **Essenziali**: pennelli sensibili alla pressione (Pointer Events), stabilizzazione del tratto, livelli, gomma, colori recenti, zoom/rotazione tela, annulla, esporta PNG.
- **Stack**: HTML + Canvas; perfect-freehand per tratti morbidi.

## 3. Ufficio e documenti

### Microsoft Word
- **Essenziali**: editor ricco (grassetto, corsivo, titoli, elenchi, allineamento, colori, link, immagini, tabelle); impaginazione A4 a schermo; conteggio parole; salvataggio automatico; esporta DOCX, PDF e HTML; apri DOCX.
- **Livello 2**: intestazioni e piè di pagina; sommario automatico; trova e sostituisci; commenti; modelli (lettera, CV, fattura).
- **Stack**: HTML + Tiptap o Quill; docx (libreria) per esportare DOCX; mammoth per importare DOCX; html2pdf/jsPDF per PDF.

### Microsoft Excel
- **Essenziali**: griglia con righe/colonne ridimensionabili; formule (SOMMA, MEDIA, SE, CERCA.VERT, CONTA.SE, riferimenti relativi/assoluti); formattazione numeri e celle; più fogli; ordina e filtra; copia/incolla da e verso Excel; apri/salva XLSX e CSV; grafici (barre, linee, torta).
- **Livello 2**: blocca riquadri; formattazione condizionale; tabelle pivot semplici; convalida dati.
- **Stack**: HTML + SheetJS (xlsx) per i file; motore formule con HyperFormula; Chart.js per i grafici. Griglia virtualizzata per migliaia di righe.

### PowerPoint
- **Essenziali**: diapositive con layout (titolo, titolo+contenuto, due colonne, immagine); testo, immagini, forme; temi colore; riordina diapositive; modalità presentazione a schermo intero con frecce; note del relatore; esporta PDF e PPTX.
- **Livello 2**: transizioni; animazioni di comparsa; vista relatore con timer.
- **Stack**: HTML; PptxGenJS per esportare PPTX.

### Adobe Acrobat (PDF)
- **Essenziali**: visualizza PDF; unisci, dividi, ruota, elimina e riordina pagine; aggiungi testo, firma disegnata, evidenziazione; compila moduli; immagini → PDF; comprimi.
- **Livello 2**: OCR (Tesseract.js); estrai testo e immagini; filigrana; numeri di pagina.
- **Stack**: HTML + pdf-lib (modifica) + PDF.js (visualizzazione). Python + pypdf per lavori in blocco.

### Grammarly / correttore
- **Essenziali**: editor che sottolinea errori ortografici e grammaticali con suggerimenti; leggibilità; conteggio parole.
- **Stack**: HTML + chiamata a un servizio LanguageTool (pubblico o locale) se l'utente accetta; altrimenti dizionario Hunspell italiano con nspell. Dillo all'utente se il testo esce dal PC.

## 4. Produttività e organizzazione

### Notion
- **Essenziali**: pagine annidate in barra laterale; editor a blocchi (testo, titoli, elenchi, checkbox, citazioni, codice, immagini, divisori) con menu "/"; trascina blocchi; database semplici con vista tabella e kanban; ricerca; esporta Markdown.
- **Livello 2**: vista calendario; proprietà (data, select, numero); modelli; link tra pagine.
- **Stack**: HTML + Editor.js o Tiptap; IndexedDB.

### Trello / Asana (kanban)
- **Essenziali**: bacheche, colonne, schede trascinabili; dettaglio scheda (descrizione, checklist, scadenza, etichette colorate); filtri; archivio; esporta/importa JSON.
- **Livello 2**: vista calendario; promemoria (Notification API); più bacheche; allegati.
- **Stack**: HTML + SortableJS.

### Todoist / Microsoft To Do
- **Essenziali**: attività con scadenza, priorità, progetti, sottoattività; viste Oggi / Prossimi 7 giorni; inserimento rapido in linguaggio naturale ("domani alle 15 #lavoro p1"); ricorrenze; notifiche.
- **Stack**: HTML; chrono-node per le date in linguaggio naturale (supporta l'italiano parzialmente: aggiungi regole tue per "domani", "lunedì", ecc.).

### Evernote / OneNote / Obsidian
- **Essenziali**: note in Markdown con anteprima; cartelle e tag; ricerca a testo completo; link tra note [[nome]]; allegati immagine; esporta in .md.
- **Livello 2**: grafo dei collegamenti; note giornaliere; modelli.
- **Stack**: HTML + marked + DOMPurify; MiniSearch per la ricerca. Per lavorare su una cartella vera del PC: File System Access API (Chrome/Edge).

### Google Calendar / agende
- **Essenziali**: viste mese/settimana/giorno; eventi con colore, ricorrenza, promemoria; trascina per spostare; importa/esporta .ics.
- **Stack**: HTML + FullCalendar; ical.js per i file .ics.

### Toggl / Clockify (tracciamento tempo)
- **Essenziali**: timer avvia/ferma per progetto e cliente; inserimento manuale; report settimanale con grafici; tariffa oraria e totale; esporta CSV.
- **Stack**: HTML + Chart.js.

### Forest / Pomodoro / Habit tracker
- **Essenziali**: timer pomodoro configurabile, statistiche giornaliere, serie di giorni (streak), griglia abitudini stile GitHub.
- **Stack**: HTML.

## 5. Finanze

### YNAB / gestione budget
- **Essenziali**: conti; transazioni con categorie; budget mensile per categoria ("assegna ogni euro"); importa CSV dell'estratto conto con mappatura colonne e regole automatiche di categoria; grafici spese per categoria e andamento; esporta CSV.
- **Livello 2**: obiettivi di risparmio; spese ricorrenti; patrimonio netto nel tempo.
- **Stack**: HTML + PapaParse + Chart.js; IndexedDB. Dati solo in locale: dillo all'utente, è un punto di forza.

### Fatturazione (es. Fatture in Cloud, QuickBooks base)
- **Essenziali**: anagrafica clienti; creazione fattura/preventivo con righe, IVA, sconti, numerazione progressiva; PDF con intestazione personalizzata; stato pagata/da pagare; riepilogo per mese.
- **Nota**: la fattura elettronica italiana (XML FatturaPA verso lo SdI) richiede un intermediario accreditato: la nostra app può generare l'XML, ma l'invio va fatto con un servizio abilitato. Dillo chiaramente.
- **Stack**: HTML + jsPDF/pdf-lib.

## 6. Audio e musica

### FL Studio / Ableton (DAW)
- **Essenziali**: step sequencer per batteria (16 passi, più tracce); piano roll per melodie; sintetizzatore con oscillatori, inviluppo, filtro; BPM e play/stop/loop; mixer con volume/pan/mute/solo; effetti riverbero e delay; esporta WAV.
- **Livello 2**: arrangiamento in pattern sulla timeline; caricamento campioni propri; automazioni; MIDI in ingresso (Web MIDI API); esporta MIDI.
- **Stack**: HTML + Tone.js. Campioni di batteria sintetizzati (niente campioni proprietari).

### Audacity-like / Adobe Audition
- **Essenziali**: apri file audio, forma d'onda con zoom, selezione, taglia/copia/incolla/silenzia, dissolvenza in entrata/uscita, normalizza, cambio volume, registra dal microfono, esporta WAV/MP3.
- **Livello 2**: riduzione rumore; più tracce; cambio velocità/tono.
- **Stack**: HTML + Web Audio API + wavesurfer.js; lamejs per MP3.

### Accordatore, metronomo, Guitar Pro (tablature)
- **Essenziali**: accordatore con microfono (rilevamento frequenza); metronomo con accenti; editor di tablature con riproduzione.
- **Stack**: HTML + Web Audio (autocorrelazione per il pitch); alphaTab per tablature.

### Spotify locale / lettore musicale
- **Essenziali**: apri cartella di musica; libreria per artista/album dai tag (music-metadata-browser / jsmediatags); playlist; coda; equalizzatore; visualizzatore.
- **Stack**: HTML + Web Audio.

## 7. Video

### Premiere / CapCut (montaggio semplice)
- **Essenziali**: importa clip; timeline con taglio, divisione, riordino; testo sovrapposto; musica di sottofondo con volume; transizione dissolvenza; esporta MP4.
- **Livello 2**: velocità; filtri colore; sottotitoli da file .srt; formati verticale/orizzontale.
- **Stack**: HTML + ffmpeg.wasm (lento su file lunghi: avvisa) oppure Python + ffmpeg (molto più veloce). Se ffmpeg non è installato, spiega come installarlo con `winget install ffmpeg`.

### OBS / registratore schermo
- **Essenziali**: registra schermo, finestra o scheda; webcam in sovrimpressione; microfono; pausa; salva WebM/MP4.
- **Stack**: HTML + getDisplayMedia + MediaRecorder.

### HandBrake / convertitori
- **Essenziali**: converti formato, comprimi con preset (WhatsApp, YouTube, email), estrai audio, ritaglia inizio/fine.
- **Stack**: Python + ffmpeg con interfaccia Tkinter o `.bat` trascina-e-rilascia.

## 8. Sviluppo e strumenti tecnici

### Postman
- **Essenziali**: richieste HTTP (metodo, URL, header, body JSON/form); risposta formattata con stato e tempo; raccolte salvate; variabili d'ambiente; cronologia.
- **Nota**: dal browser molte API bloccano le richieste (CORS); la versione Python (httpx + Tkinter/PySide6) non ha questo limite. Scegli quella se l'utente deve chiamare API qualsiasi.

### Editor di database (TablePlus, DB Browser)
- **Essenziali**: apri file SQLite; elenco tabelle; vista e modifica righe; editor SQL con risultati; esporta CSV.
- **Stack**: HTML + sql.js.

### Diagrammi (Visio, Lucidchart)
- **Essenziali**: forme, connettori che seguono le forme, testo, allineamento, esporta PNG/SVG; in più modalità testo → diagramma.
- **Stack**: HTML + JointJS o SVG puro; Mermaid per la modalità testo.

## 9. Sistema e file

### WinRAR / WinZip
- **Essenziali**: crea ZIP da file/cartelle, estrai ZIP, elenco contenuto, password (ZIP AES).
- **Stack**: Python (zipfile, pyzipper per AES; py7zr per .7z) con Tkinter; oppure HTML + JSZip per ZIP semplici.

### CCleaner / pulizia disco
- **Essenziali**: analizza dimensione cartelle (mappa ad albero); trova file duplicati (hash); file grandi e vecchi; svuota cartelle temporanee *dopo conferma*.
- **Sicurezza**: mostra sempre l'elenco e chiedi conferma prima di cancellare; sposta nel Cestino (send2trash) invece di eliminare definitivamente; non toccare il registro di sistema.
- **Stack**: Python + PySide6/Tkinter.

### Rinominatore in blocco (Bulk Rename Utility)
- **Essenziali**: anteprima prima/dopo; trova e sostituisci; numerazione; data EXIF nel nome; maiuscole/minuscole; annulla l'ultima operazione.
- **Stack**: Python + Tkinter.

### Password manager (1Password, LastPass)
- **Essenziali**: archivio cifrato con password principale (AES-GCM + PBKDF2/Argon2), generatore di password, ricerca, copia negli appunti con cancellazione automatica, esporta archivio cifrato.
- **Nota**: la crittografia va fatta bene: usa Web Crypto API o la libreria `cryptography` di Python, mai algoritmi inventati. Avvisa che senza la password principale i dati non sono recuperabili.

## 10. Studio e insegnamento

### Anki / Quizlet
- **Essenziali**: mazzi di flashcard; ripetizione spaziata (algoritmo SM-2); modalità quiz e scelta multipla; importa da CSV; statistiche.
- **Stack**: HTML.

### Kahoot / quiz
- **Essenziali**: editor domande con tempo; modalità gioco a schermo intero con classifica; risultati esportabili.
- **Stack**: HTML (versione per un solo schermo; il multigiocatore in rete richiede un server: spiegalo).

### Duolingo-like / esercizi
- **Essenziali**: lezioni a livelli, esercizi a scelta, completamento, ascolto (Web Speech API), punti e serie.
- **Stack**: HTML.

## 11. 3D e CAD

### SketchUp / Tinkercad
- **Essenziali**: forme base (cubo, cilindro, sfera), sposta/ruota/scala con maniglie, unione/sottrazione (CSG), griglia e misure in mm, esporta STL/OBJ per stampa 3D.
- **Stack**: HTML + three.js + three-bvh-csg.

### AutoCAD (2D)
- **Essenziali**: linee, polilinee, cerchi, archi, rettangoli; aggancio ai punti (snap); quote; livelli; inserimento coordinate da tastiera; esporta DXF e SVG/PDF.
- **Stack**: HTML + Canvas/SVG; scrittura DXF manuale (formato testuale semplice) o dxf-writer.
- **Limite**: per modellazione 3D parametrica seria cita FreeCAD.

## 12. Comunicazione e marketing

### Mailchimp (newsletter)
- **Essenziali**: editor email a blocchi che produce HTML compatibile con i client di posta (tabelle, stili inline); anteprima desktop/mobile; elenco contatti da CSV; esporta HTML.
- **Nota**: l'invio in massa richiede un servizio SMTP; la nostra app prepara l'email, non la spedisce.

### Hootsuite / Later (pianificazione social)
- **Essenziali**: calendario contenuti; bozze con immagine e testo; anteprima per piattaforma con conteggio caratteri; stato (idea, pronto, pubblicato); esporta CSV.
- **Nota**: la pubblicazione automatica richiede le API delle piattaforme e account sviluppatore; la versione base è un planner.

### Typeform / Google Forms
- **Essenziali**: costruttore di moduli (testo, scelta, scala, data); anteprima; raccolta risposte; riepilogo con grafici; esporta CSV.
- **Nota**: per raccogliere risposte da altre persone serve uno spazio condiviso (Artifact con database condiviso, se disponibile, o un foglio Google). In locale funziona solo sullo stesso dispositivo.
