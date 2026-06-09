<div align="center">

# 💎 Gem Cert Pricer

**Calcolatore di valore gemme e costo certificati gemmologici**

Strumento professionale per gemologi e operatori del distretto orafo **Tarì** (Marcianise, Campania).
Quotazione in tempo reale del valore di una gemma, del metallo e del costo del certificato — per pietre sciolte e gioielli montati.

[**▶ Apri l'app**](https://alessandro-sequino.github.io/gem-cert-pricer/)

🇮🇹 Italiano · 🇬🇧 English · 📱 Installabile come app (PWA) · 🔒 Tariffe private, mai nel repository

</div>

---

## Panoramica

Gem Cert Pricer è un'applicazione web **single-file** (un solo `index.html` con CSS e JavaScript inline, zero build) pensata per il lavoro quotidiano al banco: selezioni una gemma, imposti peso, qualità e montatura, e ottieni immediatamente valore stimato e costo del certificato, con il rapporto cert/valore che ti dice se la certificazione è conveniente.

Funziona interamente nel browser — **nessun server, nessun account, nessun dato che lascia il dispositivo**. I prezzi vivono nel `localStorage` del browser e possono essere esportati/importati come file `.gcp.json` per spostarli tra dispositivi.

---

## ✨ Funzionalità

| Modulo | Descrizione |
|---|---|
| **Calcolatore** | Valore gemma + metallo + costo certificato in tempo reale; composizione multi-pietra con preset (Solitario, Halo, Tennis, Trilogy) |
| **Catalogo** | Portfolio gioielli editabile con riepilogo costi ed export CSV |
| **Tariffe / Prezzi** | Tabelle DGR/DJR per 5 categorie gemme × fasce di peso × 3 tipologie cliente |
| **Formula certificato** | Tre modalità: **Standard**, **Semplice** (espressioni in stile Excel), **Avanzata** (funzione JavaScript) |
| **Analisi** | Rapporto costo-certificato / valore sull'intero catalogo |
| **Database prezzi** | Prezzi di riferimento del distretto Tarì — 48 gemme |
| **Scansione DB** | Confronto cert/valore su tutte le gemme a parametri fissi, ordinabile |
| **Dati** | Import / Export del tariffario personalizzato `.gcp.json` |

**Esperienza:** interfaccia bilingue commutabile in-app, tema chiaro "warm ivory + champagne gold", tipografia fluida, transizioni curate, accessibilità (focus visibile, skip-link, `prefers-reduced-motion`, contrasti AA) e layout responsive da desktop a smartphone.

---

## 🔒 Dati personali separati dal codice

L'app è pubblicata **senza prezzi reali**: ogni operatore carica il proprio tariffario privato, che non finisce mai nel repository.

```
1. Configura  →  pagina "Tariffe" — inserisci fasce, K, fattori tennis, contorni…
2. Esporta    →  pagina "Dati" → "Esporta come .gcp.json"
3. Salva      →  conserva il file su cloud privato, USB, ecc.
4. Importa    →  apri l'app su qualsiasi dispositivo → "Importa dati"
```

Usa [`sample-pricing.gcp.json`](sample-pricing.gcp.json) come template vuoto da compilare.

### Formato `.gcp.json`

```json
{
  "version": 16,
  "format": "gcp-pricing-v1",
  "meta": { "description": "Il mio tariffario" },
  "data": {
    "PRICE_TABLE": { "diam": {…}, "prec": {…}, "color": {…}, "org": {…}, "sint": {…} },
    "PRICE_TIERS_DIAM":  [ {"max": 0.14}, …, {"max": null} ],
    "PRICE_TIERS_COLOR": [ {"max": 0.49}, …, {"max": null} ],
    "DJR_MATRIX":   [ {"l": "< 1.00 ct", "max": 0.99, "p": [...]}, … ],
    "DJR_K_COLOR":  1.10,
    "K_MONTATO":    { "diam": {"base": 1.35, …}, … },
    "TENNIS_FACTOR":{ "diam": {"base": 55, …}, … },
    "CONTORNO_TIERS": [...],
    "certParams":   {"xe": 40, "xl_sm": 1.5, "xl_lg": 22, "xs_sm": 11, "xs_lg": 16, "csec": 25},
    "QUOT":         {"base": 600, "media": 1800, "alta": 4000},
    "metalPrices":  {"Oro 18k (750‰)": 43, …}
  }
}
```

> `{"max": null}` è la serializzazione JSON di `Infinity` — indica l'ultima fascia di peso; l'app la riconverte automaticamente.

---

## 🚀 Installazione e uso

### Uso online
Apri direttamente il link: **[alessandro-sequino.github.io/gem-cert-pricer](https://alessandro-sequino.github.io/gem-cert-pricer/)**.

### Esecuzione in locale
Essendo un singolo file statico, basta servirlo da una cartella:

```bash
git clone https://github.com/Alessandro-Sequino/gem-cert-pricer.git
cd gem-cert-pricer
python3 -m http.server 8080      # poi apri http://localhost:8080
```

> Aprire `index.html` con doppio clic (`file://`) funziona, ma il manifest PWA non si carica per via delle restrizioni CORS dei browser: per l'esperienza completa usa un piccolo server statico come sopra.

### 📱 Installare come app sul telefono
L'app è una **PWA**: nessuno store, installazione diretta dal browser.

- **Android (Chrome):** apri il link → menu **⋮** → *Aggiungi a schermata Home*
- **iPhone (Safari):** apri il link → **Condividi** (□↑) → *Aggiungi a schermata Home*

---

## 📐 Formula del certificato

```
PIETRA SCIOLTA (DGR — Diamond/Gem Grading Report)
  Cert = PRICE_TABLE[categoria][cliente][fascia_ct]
         + Laser (€1.5 se <1ct · €22 se ≥1ct)
         + Seal  (€11  se <1ct · €16 se ≥1ct)
         × (1 + express%) se urgente

  Categorie: diam · prec · color · org · sint
  Clienti:   T1 (base) · T2 (speciale) · T3 (large)

GIOIELLO BASE (anello / pendente / orecchini)
  Cert = DGR_pietra × K_MONTATO[cat][cliente]
         + forfait_contorno[fascia_peso_secondarie]

GIOIELLO TENNIS (bracciale / collana)
  Cert = peso_tot_ct × TENNIS_FACTOR[cat][cliente]

DJR (Diamond/Jewellery Report — gioiello montato)
  Cert = DJR_MATRIX[fascia_peso_tot][fascia_n_pietre]
         × DJR_K_COLOR (se gemma colorata)
```

La modalità **Formula** consente di sovrascrivere questo motore con espressioni Excel-style o con una funzione JavaScript personalizzata.

---

## 🗂 Struttura del progetto

```
gem-cert-pricer/
├── index.html              # L'intera applicazione: HTML + CSS + JS inline (multi-pagina, i18n, motore di calcolo)
├── manifest.json           # Manifest PWA (nome, icone, tema, display standalone)
├── icon-192.png            # Icona PWA
├── sample-pricing.gcp.json # Template vuoto del tariffario da compilare
└── README.md
```

**Architettura di `index.html`:**
- **Design system a token** — scala tipografica e di spaziatura fluide (`clamp()`), palette warm-ivory/champagne-gold, tema chiaro con supporto `prefers-color-scheme: dark`.
- **SPA multi-pagina** — navigazione client-side tra le sezioni, niente reload.
- **Motore di calcolo + i18n** — listini, motore formule (Standard/Semplice/Avanzata) e dizionario IT/EN in JavaScript vanilla.
- **Dipendenze esterne (CDN):** [Chart.js](https://www.chartjs.org/) per i grafici, [Lucide](https://lucide.dev/) per le icone. Nessun framework, nessun passo di build.

---

## 🛠 Tecnologie

HTML5 · CSS3 (custom properties, grid, container-aware layout) · JavaScript vanilla (ES6+) · PWA (manifest + localStorage) · Chart.js · Lucide.

---

## Crediti

Creato da **Alessandro Sequino**.
Database prezzi di riferimento: distretto orafo **Tarì** 2025, Campania.
