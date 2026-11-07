# S33 - Vega · Manuale

Vega è un sintetizzatore polifonico a 8 voci nello stile dei primi anni '80 (famiglia Juno-106 / Jupiter-8): pannello fisso a fader, nessun cavo, suono immediato. Fa parte della famiglia S33 e funziona da solo o come modulo della **S33 - Board**.

Funziona in **Chrome sul Mac** con una tastiera MIDI. Safari non supporta il MIDI dal browser.

---

## 1. Primi passi

1. Apri `index.html` in Chrome (basta il doppio clic).
2. Premi **POWER**: si accende il LED e il display mostra la patch.
3. Suona con la tastiera MIDI, con la tastiera a schermo o con i tasti del computer (**A–K**, **Z/X** per l'ottava, **Spazio** per il sustain).

Gli 8 LED **VOICES** in alto mostrano le voci: rossi accesi mentre suonano, scuri durante il rilascio.

## 2. Il pannello

Da sinistra a destra, come il percorso del suono.

| Sezione | Comandi |
|---|---|
| **LFO** | RATE, DELAY (la modulazione entra piano dopo ogni nuova nota), WAVE (TRI, SQR, S&H). Il LED lampeggia a tempo. |
| **DCO** | RANGE 16'/8'/4', LFO (vibrato), PWM e MODE (LFO, MAN, ENV), WAVE (PULSE, SAW), SUB, NOISE |
| **HPF** | Passa-alto a 4 posizioni (OFF, 1, 2, 3) |
| **VCF** | Passa-basso 24 dB risonante: FREQ, RES, ENV, **POL** (+ o −, inviluppo invertito), LFO, KYBD |
| **VCA** | MODE (ENV o GATE, a organo), VELO (quanto conta la dinamica), LEVEL |
| **ENV** | A, D, S, R, uno solo per filtro e volume |
| **CHORUS** | OFF, I, II, I+II: il colore anni '80 |
| **ARPEGGIO** | ON, HOLD, MODE (UP, DOWN, U&D, RND), RANGE 1–3 ottave, RATE |
| **VOICE** | MODE (POLY, UNISON, MONO), DETUNE (per l'unison), GLIDE, BEND (escursione del pitch bend), **DRIFT** |

**I fader**: trascina il cappuccio o clicca sulla guida; **Maiusc** per la regolazione fine; rotella del mouse per i piccoli passi; **doppio clic** per il valore iniziale. Mentre muovi un comando, il display mostra nome e valore.

**Rotelle BEND e MOD** a sinistra della tastiera: seguono quelle della tastiera MIDI. La MOD aggiunge vibrato senza ritardo.

**DRIFT** è l'instabilità analogica: ogni voce è leggermente stonata e con il filtro un po' diverso dalle altre, e l'intonazione oscilla piano nel tempo, come nei synth veri dell'epoca. A zero le voci sono perfette e identiche; al 25% (il valore di partenza) il suono è vivo ma intonato; al massimo arriva a circa ±11 cent, un effetto "vintage" marcato. Il DRIFT si salva con la patch.

## 2b. MIDI Learn e canale MIDI

**MIDI Learn**: fai **clic destro** su un comando (fader, selettore o pulsante): lampeggia e il display chiede di muovere una manopola. Muovi una manopola o un fader della tastiera MIDI: da quel momento la muove lei. L'etichetta del comando diventa azzurra; passandoci sopra col mouse vedi il numero di CC.

- **Togliere un collegamento**: clic destro sul comando, poi di nuovo clic destro mentre lampeggia.
- **Annullare**: Esc.
- Un CC comanda un solo controllo; collegarlo a un altro lo sposta.
- Sui selettori la manopola scorre tra le posizioni; sui pulsanti (ON, HOLD, PULSE…) oltre metà corsa è acceso.
- Mod wheel (CC1) e pedale di sustain (CC64) non si possono collegare: restano mod wheel e sustain.
- I collegamenti valgono per tutte le patch e restano nel browser.

**Canale MIDI**: in basso a sinistra, accanto al nome della tastiera, **CH OMNI** vuol dire che Vega ascolta tutti i canali. Clic per scegliere il canale 1, 2, … 16 (clic destro o Maiusc+clic per tornare indietro). Utile con Logic: Twin Core sul canale 1 e Vega sul 2, per esempio. Nella S33 Board puoi lasciarlo su OMNI: il canale si sceglie già nel modulo MIDI In.

## 3. Memoria

- **Banco A**: 8 suoni di fabbrica (Brass Section, Night Pad, Glass Keys, Unison Lead, Sub Bass, String Machine, Arp City, Hoover). Non si sovrascrivono.
- **Banchi B, C, D**: 24 posti per i tuoi suoni.

**Caricare**: premi il banco e poi il numero. Il display mostra per esempio **A2**; dopo una modifica compare l'asterisco (**A2\***).

**Salvare**: scrivi il nome in **NAME**, premi **WRITE** (il LED lampeggia), poi banco (B–D) e numero.

**Non perdi mai un suono non salvato**: se hai modifiche e premi un numero, il display avvisa *UNSAVED SOUND*. A quel punto **WRITE** salva lì il suono, oppure lo **stesso numero** di nuovo carica quella posizione.

**INIT** riporta tutti i comandi ai valori iniziali.

**SAVE FILE / LOAD FILE**: esporta e reimporta i banchi B–D (`S33-Vega-banks.json`), per un backup o per spostarli su un altro computer o browser.

Vega ricorda i tuoi banchi e l'ultimo suono anche dopo la chiusura.

**MIDI Program Change**: i numeri 0–31 caricano A1…D8.

## 4. Libreria Juno-106

Vega legge le patch del Roland Juno-106 e le converte nei suoi comandi.

1. **LOAD FILE** → scegli un file `.106` (libreria) o `.syx` (SysEx del Juno-106).
2. Si apre la **libreria**: clicca un nome per sentirlo, anche suonando con la tastiera MIDI. **FIND** cerca per nome.
3. Per tenerlo: **WRITE…** (nella libreria), poi banco B–D e numero.

Il pulsante **LIBRARY** riapre l'ultima libreria caricata. Il suono è vicino all'originale ma non identico: filtro e chorus sono quelli di Vega. Le patch "(unison)" partono in modo UNISON. Il Juno-106 non ha la dinamica: le patch importate hanno VELO a zero.

## 5. Nella S33 Board

Vega è un modulo della board, con prese **MIDI**, **CLK** e **OUT**.

- Suona con il motore audio della board: il suo POWER avvia anche la board.
- Di serie riceve dal **MIDI In 2**.
- Con il **CLK** collegato e il Clock in Play, l'arpeggiatore suona in sedicesimi sulla griglia della board (RATE viene ignorato) e l'intestazione ARPEGGIO mostra i BPM. Con il Clock fermo torna al suo RATE.
- Ha il suo canale **VEGA** nel Mixer.
- Il suono corrente viaggia nelle **sessioni** della board; banchi e libreria Juno restano nel browser, come le librerie degli altri strumenti.

## 6. Installare come app

Il service worker richiede `http://localhost` o `https://`:

```bash
cd "v9 (1.2.0)"
python3 -m http.server 8000
# apri http://localhost:8000 in Chrome → menu ⋮ → Installa S33 - Vega
```

Una volta installata funziona anche senza rete. Attenzione: banchi e libreria sono legati all'indirizzo (file, localhost, GitHub Pages): per spostarli usa **SAVE FILE / LOAD FILE**.

## 7. Se qualcosa non va

- **Non suona**: premi POWER; se il display mostra un errore, ricarica la pagina.
- **Note bloccate**: **PANIC**.
- **MIDI: NOT SUPPORTED**: usa Chrome.
- Sul display, dopo POWER, **WORKLET** è il motore normale; **COMPAT** è la modalità di riserva (stesso suono), usata dove il browser blocca il motore principale.
