# FMA Texture – web app (PC e telefono Android)

App per i sensori Honeywell FMA collegati a una XIAO nRF52840 Sense con lo sketch
`FMA_Sense_raw_v3.ino`. La scheda manda i dati grezzi (accelerometro 1 kHz,
microfono 16 kHz, forza 100 Hz) e **l'analisi della trama la fa l'app**.

## File
| File | A cosa serve |
|---|---|
| `index.html` | l'app (funziona anche da sola, aprendola in Chrome sul PC) |
| `manifest.webmanifest`, `sw.js`, `icon-*.png` | per installarla come app sul telefono e usarla offline |

## Sul PC
Apri `index.html` con Chrome o Edge → **+ USB** → scegli la XIAO.

## Sul telefono Android (installabile come app)
Serve un indirizzo **https**: il modo più semplice e gratuito è GitHub Pages.

1. Crea un account su github.com (se non ce l'hai).
2. **New repository** → nome per esempio `fma-texture` → *Public* → *Create*.
3. **Add file → Upload files** → trascina i 5 file di questa cartella → *Commit*.
4. **Settings → Pages** → *Source: Deploy from a branch* → branch `main`, cartella `/ (root)` → *Save*.
5. Dopo 1-2 minuti l'app è su `https://TUONOME.github.io/fma-texture/`.
6. Sul telefono apri quell'indirizzo con **Chrome (versione 148 o successiva)** →
   menu ⋮ → **Installa app** (o "Aggiungi a schermata Home").

Per usarla: collega la XIAO al telefono con un cavo **USB-C ↔ USB-C** (o un adattatore OTG),
apri l'app → **+ USB** → scegli la scheda → consenti l'accesso.
Lo schermo resta acceso finché la scheda è collegata.

Per aggiornare l'app: ricarica i file modificati su GitHub; il telefono prende la nuova
versione alla prossima apertura con internet.

## Uso
- **Devices**: forza, intensità e frequenza della trama, stato (SLIDING / still),
  KB/s ricevuti e campioni persi. *Learn background*: tieni il sensore fermo e senza
  contatto per 2 s (lo fa anche da solo all'avvio e dopo ogni sollevamento).
- **Signals**: grafici nel tempo; le zone colorate sono i tratti di scorrimento.
  *Speed* (mm/s) → calcola il periodo spaziale della trama in mm.
- **Map**: frequenza vs intensità, un colore per ogni *Label* → vedi se le superfici si separano.
- **Spectrum**: spettro in tempo reale contro il fondo appreso + **impostazioni dell'analisi**
  (forza di contatto, soglia di scorrimento, ecc.), salvate nel browser.
- **Record / CSV**: grandezze calcolate (20 righe/s) con l'etichetta.
  **Raw**: salva il flusso grezzo (microfono in WAV, accelerometro e forza in CSV) per analisi offline
  o per addestrare un classificatore.
- Comandi alla scheda: `t` tara, `r` rimuovi tara, `i` info.

Funziona ancora anche con gli sketch precedenti che inviano testo (`force:..,temp:..` o `forza,temp`).
