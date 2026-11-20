# S-3340 · Simulatore semi-modulare

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

## Preset e sessioni

Dal menu **PRESET**:

| Voce | Cosa fa |
|---|---|
| ＋ Salva il suono attuale… | Salva manopole, levette, cavi e voci con un nome (anche col pulsante SALVA); a scelta anche il pattern su cui stai lavorando |
| ★ nome | Richiama un tuo preset |
| ✕ Elimina «nome» | Elimina il preset caricato |
| ⇩ Esporta sessione | Crea `S3340-sessione.json` con preset, suono attuale, tempo, i 64 pattern e le impostazioni |
| ⇧ Importa sessione o preset | Aggiunge i preset del file e, se confermi, ripristina la sessione |

Ogni preset di fabbrica porta con sé un pattern d'esempio: caricandolo, il pattern va nel pattern di lavoro (premi PLAY/STOP per sentirlo) e i banchi salvati non vengono toccati. Se il pattern di lavoro ha modifiche non salvate, il simulatore chiede prima se sostituirlo o caricare solo il suono.

I **pattern** del sequencer hanno una memoria propria (8 banchi × 8 pattern): si salvano tenendo **SHIFT + PLAY per 2 secondi**, scegliendo il pattern coi pad (PATTERN + pad per il banco) e confermando con **SHIFT + REC**.

Tutto viene salvato nel browser. La versione online e quella installata offline hanno memorie separate: per passare da una all'altra usa Esporta e Importa.

## Usarlo offline (iPhone, iPad, Android)

Il simulatore è una PWA: dopo la prima apertura funziona anche senza connessione.

- **iPhone / iPad (Safari)**: apri la pagina, tocca Condividi → **Aggiungi alla schermata Home**.
- **Android (Chrome)**: menu ⋮ → **Installa app**.

Dopo un aggiornamento dei file su GitHub, apri l'app una volta con la connessione attiva per scaricare la nuova versione.

## Pubblicazione su GitHub Pages

1. Carica il contenuto di questa cartella nel repository (deve essere **pubblico**, o serve un piano che consenta Pages su repository privati).
2. Settings → **Pages** → Source: *Deploy from a branch*, branch `main`, cartella `/ (root)`.
3. Dopo un paio di minuti la pagina è disponibile all'indirizzo indicato da GitHub.

## File

| File | Contenuto |
|---|---|
| `index.html` | Il simulatore completo (interfaccia, motore audio, font incorporati) |
| `sw.js` | Service worker per l'uso offline |
| `manifest.webmanifest` | Dati dell'app installabile |
| `icon-*.png` | Icone dell'app |
| `OFL-*.txt` | Licenze dei font Barlow e JetBrains Mono (SIL Open Font License) |

## Compatibilità

- Audio: Chrome, Edge, Firefox, Safari recenti (AudioWorklet, con ripiego automatico se non disponibile).
- MIDI: Chrome ed Edge su computer e Android. Safari e i browser su iPhone/iPad non supportano Web MIDI.

## Note tecniche

Il motore audio gira in un AudioWorklet a frequenza di campionamento piena: oscillatori con anti-aliasing polyBLEP, filtro ladder a ritardo zero (ZDF) con saturazione, inviluppi esponenziali, patch bay elaborata campione per campione.

## Crediti

Sviluppato con l'assistenza dell'intelligenza artificiale. Scelte di progetto, prove e revisione finale a cura dell'autore.