<div align="center">

# 💎 Gem Cert Pricer

**Stima istantanea del costo dei certificati gemmologici**

Strumento per gemologi e operatori del distretto orafo **Tarì** (Marcianise, Campania).
Pietre sciolte, gioielli montati (gemma di colore o lab-grown) e bracciali tennis.
Inserisci la caratura e confronta subito il prezzo del certificato sui tre tier T1 · T2 · T3.

[**▶ Apri l'app**](https://alessandro-sequino.github.io/gem-cert-pricer/)

🇮🇹 Italiano · 🇬🇧 English · 📱 Installabile come app (PWA) · 🔒 Tariffe private, mai nel repository

</div>

---

## Panoramica

Gem Cert Pricer è un'applicazione web **single-file** (un solo `index.html` con CSS e JavaScript inline, zero build, nessuna dipendenza da caricare: il generatore di codici QR è incluso nel file) pensata per il lavoro al banco.

L'interfaccia è in **italiano e inglese**: la lingua si sceglie dal selettore IT/EN in alto, parte da quella del browser e viene ricordata.

Funziona interamente nel browser: **nessun server, nessun account, nessun dato che lascia il dispositivo**. Le tariffe vivono nel `localStorage` del browser e si spostano tra dispositivi con un file `.gcp.json`.

| Schermata | Descrizione |
|---|---|
| **Home** | Pagina iniziale con i tre percorsi di stima |
| **Stima certificato** | Pietra sciolta · Montato (gemma di colore o lab-grown) · Tennis, con confronto T1/T2/T3 e fasce evidenziate |
| **Tariffe** | Editor delle tabelle di prezzo, import/export `.gcp.json` |
| **Clienti** | Database clienti: tier di riferimento e per categoria, prezzi su misura, link personale da inviare su WhatsApp; QR del negozio e richieste via WhatsApp |

### Versione aziendale e versione pubblica

- **Aziendale** — chi importa il tariffario completo vede i tre tier, le tariffe e la pagina **Clienti**. A ogni cliente si assegna un **tier di riferimento**, se serve un **tier diverso per categoria** (es. T1 sui diamanti e T3 sulle gemme di colore) e, sopra a questi, eventuali **prezzi su misura** per singola fascia (o per il supplemento della pietra centrale).
- **Pubblica (cliente)** — dalla scheda di un cliente si invia su WhatsApp (o si copia) il suo **link personale**. Chi lo apre vede solo i propri prezzi, in un'unica colonna: niente tier, niente tariffe aziendali, niente altri clienti. Il listino resta salvato sul suo dispositivo finché non riceve un link aggiornato.

### QR del negozio: richiesta del listino via WhatsApp

Un unico QR, **uguale per tutti**, si espone in negozio (Clienti → *QR del negozio*, con nome del negozio e numero WhatsApp):

```
1. Il cliente inquadra il QR esposto  →  pagina «Richiedi il tuo listino»
2. Compila nome e contatti            →  si apre WhatsApp con la richiesta già scritta verso il negozio
3. In Clienti → «Da richiesta WhatsApp» incolli il messaggio  →  il cliente è creato con nome, telefono e note
4. Scegli tier o prezzi su misura e premi «Invia su WhatsApp»  →  il cliente riceve il suo link personale
5. Il cliente apre il link            →  l'app si attiva con il suo listino
```

Sei sempre tu a decidere quale listino agganciare: il QR del negozio non contiene prezzi, solo nome e numero WhatsApp del negozio. Non serve nessun server.

Il link contiene solo i prezzi effettivi di quel cliente, compressi, e li trasporta nel frammento `#` dell'indirizzo, che il browser non invia al server. Dall'app aziendale il pulsante **Anteprima** mostra esattamente ciò che vedrà il cliente.

---

## 🖼 Schermate

> Le schermate usano un tariffario **dimostrativo**: prezzi e nomi dei clienti sono inventati.

![Pagina iniziale](docs/screenshots/home.webp)

### Stima del certificato

<table>
  <tr>
    <td width="50%"><b>Pietra sciolta</b> — fascia di caratura evidenziata e confronto T1 · T2 · T3<br><br><img src="docs/screenshots/sciolto.webp" alt="Stima pietra sciolta"></td>
    <td width="50%"><b>Montato lab-grown</b> — peso totale dei diamanti + supplemento pietra centrale<br><br><img src="docs/screenshots/lab.webp" alt="Stima montato lab-grown"></td>
  </tr>
  <tr>
    <td width="50%"><b>Tennis</b> — fascia del peso totale, elenco compatto espandibile<br><br><img src="docs/screenshots/tennis.webp" alt="Stima tennis"></td>
    <td width="50%"><b>Tariffe</b> — tabelle modificabili, import/export del tariffario privato<br><br><img src="docs/screenshots/tariffe.webp" alt="Pagina tariffe"></td>
  </tr>
</table>

**Montato con gemma di colore** — pietra centrale + contorno in diamanti, con la griglia completa centrale × contorno:

![Stima montato con gemma di colore](docs/screenshots/montato.webp)

### Clienti e versione pubblica

<table>
  <tr>
    <td width="50%"><b>Database clienti</b> — tier di riferimento, tier per categoria e prezzi su misura<br><br><img src="docs/screenshots/clienti.webp" alt="Elenco clienti"></td>
    <td width="50%"><b>Scheda cliente</b> — tier per categoria, prezzi su misura fascia per fascia e invio del link su WhatsApp<br><br><img src="docs/screenshots/cliente.webp" alt="Scheda cliente con prezzi su misura"></td>
  </tr>
  <tr>
    <td width="50%"><b>Vista del cliente</b> — aperta dal link personale: un solo prezzo, senza tier né tariffe<br><br><img src="docs/screenshots/pubblica.webp" alt="Versione pubblica vista dal cliente"></td>
    <td width="50%"><b>English</b> — interfaccia bilingue con selettore IT/EN<br><br><img src="docs/screenshots/english.webp" alt="Interfaccia in inglese"></td>
  </tr>
</table>

**QR del negozio** — da stampare ed esporre; chi lo inquadra richiede il listino su WhatsApp:

<table>
  <tr>
    <td width="68%"><img src="docs/screenshots/negozio.webp" alt="QR del negozio nella pagina Clienti"></td>
    <td width="32%"><img src="docs/screenshots/m-richiesta.webp" alt="Pagina di richiesta del listino da smartphone"></td>
  </tr>
</table>

**Da smartphone** — home, stima con totale sempre visibile e vista del cliente:

<p align="center">
  <img src="docs/screenshots/m-home.webp" alt="Home da smartphone" width="250">
  &nbsp;
  <img src="docs/screenshots/m-montato.webp" alt="Stima montato da smartphone" width="250">
  &nbsp;
  <img src="docs/screenshots/m-pubblica.webp" alt="Vista cliente da smartphone" width="250">
</p>

---

## 📐 Come si calcola il prezzo

Ogni tabella è un elenco di **fasce di caratura** con limite superiore incluso («fino a»). L'ultima fascia è aperta e di norma usa un prezzo **per carato**. Ogni fascia ha un prezzo per ciascuno dei tre tier.

```
PIETRA SCIOLTA
  Cert = tariffa[diamante | gemma di colore][fascia caratura][tier]
         (ultima fascia: €/ct × caratura)

MONTATO — gemma di colore centrale + contorno in diamanti
  Cert = tariffa_centrale[fascia caratura centrale][tier]
       + supplemento_contorno[fascia caratura totale contorno][tier]
         (contorno = 0 ct → nessun supplemento)

PREZZO CLIENTE (versione pubblica)
  per ogni fascia: prezzo su misura del cliente, se presente,
                   altrimenti il prezzo del tier della categoria
                   (tier per categoria, se impostato, altrimenti tier di riferimento)
  categorie: diamanti sciolti · gemme di colore sciolte · montato gemma di colore
             (centrale + contorno) · montato lab-grown (+ supplemento) · tennis

MONTATO LAB-GROWN
  Cert = tariffa_lab[fascia peso totale diamanti][tier]
       + supplemento pietra centrale[tier]   (solo se presente)

TENNIS — diamanti naturali
  Cert = tariffa_tennis[fascia peso totale diamanti][tier]
```

---

## 🔒 Tariffe separate dal codice

L'app è pubblicata **senza prezzi**: ogni operatore importa il proprio tariffario privato, che non finisce mai nel repository (`*.gcp.json` è in `.gitignore`). Il file aziendale contiene anche il database clienti: esportalo per farne una copia di sicurezza o spostarlo su un altro dispositivo.

```
1. Compila   →  pagina "Tariffe", oppure parti da sample-pricing.gcp.json
2. Esporta   →  "Esporta" scarica tariffario-AAAA-MM-GG.gcp.json
3. Importa   →  su qualsiasi dispositivo: "Importa .gcp.json"
```

### Formato `.gcp.json`

```json
{
  "format": "gcp-pricing-v2",
  "version": 2,
  "data": {
    "loose": {
      "diam":  [ {"max": 0.14, "t": [0, 0, 0]}, …, {"max": null, "t": [0, 0, 0], "perCt": true} ],
      "color": [ … ]
    },
    "mounted": {
      "center":    [ … ],
      "halo":      [ … ],
      "lab":       [ … ],
      "labCenter": [0, 0, 0]
    },
    "tennis": [ … ],
    "clients": [
      {"id": "…", "name": "Rossi Gioielli", "tier": 1, "tiers": {"diam": 0, "color": 2},
       "note": "", "phone": "393331234567",
       "overrides": {"loose.diam": {"0.49": 35}, "mounted.labCenter": 9}}
    ],
    "shop": {"name": "Il mio negozio", "phone": "39 333 1234567"}
  }
}
```

- `max` — limite superiore della fascia in ct (incluso); `null` = fascia aperta
- `t` — prezzi per T1, T2, T3
- `perCt` — `true` se il prezzo è in €/ct e va moltiplicato per la caratura
- `labCenter` — supplemento fisso per la pietra centrale nel montato lab-grown (T1, T2, T3)
- `clients` — database clienti: `tier` di riferimento (0 = T1, 1 = T2, 2 = T3), `tiers` per categoria (`diam`, `color`, `mounted`, `lab`, `tennis`; facoltativo), `phone` WhatsApp e `overrides`, prezzi su misura indicizzati per tabella e limite della fascia (`"open"` per l'ultima fascia aperta)
- `shop` — nome e numero WhatsApp del negozio usati dal QR da esporre

I file del formato precedente (`gcp-pricing-v1`) non sono più compatibili.

---

## 🚀 Uso

**Online:** [alessandro-sequino.github.io/gem-cert-pricer](https://alessandro-sequino.github.io/gem-cert-pricer/)

**In locale:**

```bash
git clone https://github.com/Alessandro-Sequino/gem-cert-pricer.git
cd gem-cert-pricer
python3 -m http.server 8080      # poi apri http://localhost:8080
```

### 📲 Installare l'app

L'app è una **PWA**: si installa dal browser, senza store, e si apre in una finestra sua.
La pagina **[Installa l'app](https://alessandro-sequino.github.io/gem-cert-pricer/#/installa)** mostra il pulsante di installazione (Chrome ed Edge) e le istruzioni per ogni dispositivo.

![Pagina Installa l'app](docs/screenshots/installa.webp)

- **Computer, Chrome:** icona *Installa* a destra nella barra degli indirizzi, oppure menu ⋮ → *Trasmetti, salva e condividi* → *Installa pagina come app*
- **Computer, Edge:** menu ⋯ → *App* → *Installa questo sito come app*
- **Mac, Safari:** menu *File* → *Aggiungi al Dock* (l'app nel Dock ha dati separati da Safari: reimporta lì il tariffario)
- **Android, Chrome:** menu ⋮ → *Installa app*
- **iPhone, Safari:** Condividi → *Aggiungi alla schermata Home*

Tariffe e clienti restano nel browser in cui li hai caricati: dopo l'installazione, se non li vedi, importa il file `.gcp.json` da *Tariffe*.

---

## 🗂 Struttura

```
gem-cert-pricer/
├── index.html              # L'intera applicazione (HTML + CSS + JS inline, incluso il generatore QR)
├── manifest.json           # Manifest PWA
├── icon-192.png / icon-512.png
├── sample-pricing.gcp.json # Template vuoto del tariffario
├── docs/screenshots/       # Schermate usate nel README (prezzi e clienti dimostrativi)
└── README.md
```

---

## Crediti

Creato da **Alessandro Sequino** · distretto orafo **Tarì**, Campania.
Codici QR generati con [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) di Kazuhiko Arase (licenza MIT). «QR Code» è un marchio registrato di DENSO WAVE INCORPORATED.

**Ultimo aggiornamento:** ottobre 2026
