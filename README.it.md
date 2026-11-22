# S-3340 · Semi-modular Synth Simulator

*Simulatore di sintetizzatore semi-modulare*

*[English](README.md) · Italiano*

Simulatore da browser di un sintetizzatore semi-modulare analogico con schema ispirato al Behringer Crave: oscillatore 3340, filtro ladder, sequencer a 32 step e Poly Chain fino a 16 voci. Funziona su computer, tablet e telefono, anche **offline** come app installata.

> L'interfaccia parte in inglese: il pulsante **IT** nell'intestazione la passa in italiano (la scelta viene ricordata).

> Progetto non ufficiale e senza alcun legame con Behringer / Music Tribe. "Behringer" e "Crave" sono marchi dei rispettivi proprietari e sono citati solo per descrivere lo strumento a cui si ispira il layout. Grafica, codice e suoni sono originali.

## Cosa contiene

- **VCO 3340**: dente di sega e impulso con larghezza regolabile (PULSE WIDTH), FM, modulazione di larghezza, deriva analogica leggera.
- **Mixer** oscillatore / rumore, con ingresso audio esterno.
- **Filtro ladder 4 poli (24 dB/ottava)**: passa-basso e passa-alto, risonanza fino all'auto-oscillazione.
- **Inviluppo** Attack / Decay / Sustain con levetta SUSTAIN ON/OFF e **VCA** con modalità ENV o sempre aperto (drone).
- **LFO** triangolo / quadra con destinazioni selezionabili.
- **Patch bay** completa con collegamenti interni (normalizzazioni): un cavo nel jack di ingresso sostituisce il collegamento interno.
- **Sequencer a 32 step**: gate 1–8, pausa, accento, glide, ratchet, swing, registrazione dal vivo, 8 banchi × 8 pattern.
- **Arpeggiatore** con 8 modalità (su, giù, giù e su, casuale, su/giù con un'ottava in più sopra o sotto), ARP HOLD, durata delle note, trasposizione dal vivo.
- **Poly Chain**: da 1 a 16 voci.
- **Impostazioni** del sequencer: tempo input (1PPS, 2PPQ, 24/48 PPQN, CV), assign out, tipo e fronte del clock.
- **MIDI** in/out tramite Web MIDI (canale, THRU, invio note e clock MIDI con start/stop).
- **Tastiera a schermo** e tastiera del computer (A W S E D F …, Z/X per l'ottava, spazio = PLAY).
- **Pedaliera effetti** (pulsante FX, sotto la tastiera): i nove tipi di effetto presenti in Vital — overdrive, compressore, filtro (LP/BP/HP con LFO libero o sincronizzato), EQ, chorus, flanger, phaser, delay (libero o sincronizzato al tempo del sequencer) e riverbero. Si aggiungono dal menu «＋ Aggiungi effetto», si tolgono con ×, si riordinano trascinando il nome o con ◀ ▶; ogni pedale ha interruttore e LED; impostazioni e ordine vengono ricordati.
- **Preset** di fabbrica e **preset personali**, con esportazione e importazione della **sessione completa**.

## Avvio rapido

1. Apri la pagina e tocca **▶ Accendi** (i browser attivano l'audio solo dopo un tocco).
2. Dal menu **PRESET** scegli un suono, poi suona con la tastiera in basso o premi **PLAY/STOP** per il sequencer.
3. Per collegare un cavo tocca un'**uscita** e poi un **ingresso**. Toccando un ingresso già collegato il cavo si stacca.
4. Il pulsante **?** apre la guida con tutte le combinazioni di tasti.

## Controller MIDI e registrazione

- **MIDI LEARN** (computer, Chrome o Edge): apri **MIDI**, premi *Assegna manopole e switch (MIDI LEARN)*, clicca una manopola, uno switch, una manopola di un pedale, un interruttore a pedale o SYNC, poi muovi una manopola/un fader o premi un pulsante del controller. I badge viola mostrano il CC o la nota assegnati. *Togli assegnazione* libera il controllo scelto, *Cancella tutte* le toglie tutte, Esc o *Fine* per uscire. Le assegnazioni si salvano da sole nel browser; *Esporta/Importa assegnazioni* nella finestra MIDI le salva in un file .json, ed *Esporta sessione* le include insieme agli effetti.
- Manopole e fader impostano il valore direttamente; i pulsanti (momentanei o a levetta, CC o nota) commutano gli switch e accendono/spengono i pedali.
- Se il controller ha più modalità, scegli quella utente/custom, in cui le manopole inviano normali messaggi CC; le modalità dedicate a un programma DAW potrebbero non inviare nulla di utilizzabile.
- Il **MONITOR MIDI** nella finestra MIDI mostra le porte collegate e gli ultimi messaggi ricevuti: serve a verificare che il controller stia inviando.
- **● REC** (o il tasto **R**) registra l'uscita finale, effetti compresi, e la salva come file WAV. I file vanno nella cartella Download; in Chrome ed Edge su computer il pulsante **📁** accanto a REC permette di scegliere un'altra cartella, dove le registrazioni vengono poi salvate automaticamente (clicca di nuovo 📁 per cambiarla o tornare a Download).

## Preset e sessioni

Dal menu **PRESET**:

| Voce | Cosa fa |
|---|---|
| ＋ Salva il suono attuale… | Salva manopole, levette, cavi e voci con un nome (anche col pulsante SALVA); a scelta anche il pattern su cui stai lavorando |
| ★ nome | Richiama un tuo preset |
| ✕ Elimina «nome» | Elimina il preset caricato |
| ⇩ Esporta sessione… | Salva un file di sessione con data e ora nel nome (es. `S3340-session-2026-11-22-2135.json`). In Chrome ed Edge su computer si apre la finestra *Salva con nome* del sistema per scegliere cartella e nome; altrove puoi modificare il nome e il file va in Download. Una finestra fa scegliere cosa includere (di default tutto): preset utente, suono attuale, i 64 pattern, impostazioni, effetti, assegnazioni MIDI. All'importazione si ripristinano solo le parti presenti nel file |
| ⇧ Importa sessione o preset | Aggiunge i preset del file e, se confermi, ripristina la sessione |

Ogni preset di fabbrica porta con sé un pattern d'esempio: caricandolo, il pattern va nel pattern di lavoro (premi PLAY/STOP per sentirlo) e i banchi salvati non vengono toccati. Se il pattern di lavoro ha modifiche non salvate, il simulatore chiede prima se sostituirlo o caricare solo il suono.

I **pattern** del sequencer hanno una memoria propria (8 banchi × 8 pattern): si salvano tenendo **SHIFT + PLAY per 2 secondi**, scegliendo il pattern coi pad (PATTERN + pad per il banco) e confermando con **SHIFT + REC**.

Tutto viene salvato nel browser. Su iPhone e iPad l'app installata ha una memoria propria, separata da Safari: per passare da una all'altra usa Esporta e Importa.

## Installare l'app e usarla offline

Il simulatore è una PWA: dopo la prima apertura funziona anche senza connessione.

- **iPhone / iPad (Safari)**: apri la pagina, tocca Condividi → **Aggiungi alla schermata Home**.
- **Android (Chrome)**: menu ⋮ → **Installa app**.
- **Computer (Chrome o Edge)**: clicca l'icona di installazione a destra nella barra dell'indirizzo, oppure menu ⋮ → **Installa**. L'app si apre in una finestra propria.

Quando esce una nuova versione, viene scaricata da sola la volta successiva che apri l'app con la connessione attiva.

## Compatibilità

- Audio: Chrome, Edge, Firefox, Safari recenti (AudioWorklet, con ripiego automatico se non disponibile).
- MIDI: Chrome ed Edge su computer e Android. Safari e i browser su iPhone/iPad non supportano Web MIDI.

## Crediti

Sviluppato con l'assistenza dell'AI. Scelte progettuali, test e revisione finale a cura dell'autore.
