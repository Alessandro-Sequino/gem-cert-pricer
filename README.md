# Gem Cert Pricer

**Calcolatore di valore gemme e costo certificati gemmologici**
Strumento professionale per gemologi e operatori del distretto orafo **Tarì, Campania**.

→ **[Apri l'app] https://alessandro-sequino.github.io/gem-cert-pricer/** ← 

---

## ✨ Funzionalità

| Modulo | Descrizione |
|---|---|
| **Calcolatore** | Valore gemma + metallo + costo certificato in tempo reale |
| **Catalogo** | Portfolio gioielli con export CSV |
| **Tariffe** | Tabelle DGR/DJR per 5 categorie gemme × 3 tipologie cliente |
| **Formula** | Modalità Standard / Semplice (Excel-style) / Avanzata (JS) |
| **Analisi** | Rapporto costo-certificato / valore per l'intero catalogo |
| **Database** | Prezzi di riferimento Tarì 2025 — 48 gemme |
| **Scansione DB** | Confronto cert/valore su tutte le gemme con parametri fissi |
| **Dati** | Import / Export tariffario personalizzato `.gcp.json` |

**Lingua:** 🇮🇹 Italiano · 🇬🇧 English (commutabile in-app)
**Dispositivi:** Desktop · Tablet · 📱 Mobile (responsive, installabile come app)

---

## 🔒 Dati personali separati dal codice

L'app è pubblicata **senza prezzi reali**. Ogni operatore carica il proprio tariffario privato — che non finisce mai nel repository.

```
1. Configura  →  pagina "Tariffe" — inserisci fasce, K, fattori tennis…
2. Esporta    →  pagina "Dati" → "Esporta come .gcp.json"
3. Salva      →  conserva il file su cloud privato, USB, ecc.
4. Importa    →  apri l'app su qualsiasi dispositivo → "Importa dati"
```

### Formato `.gcp.json`

```json
{
  "version": 16,
  "format": "gcp-pricing-v1",
  "meta": { "description": "Il mio tariffario" },
  "data": {
    "PRICE_TABLE": { "diam": {...}, "prec": {...}, "color": {...}, "org": {...}, "sint": {...} },
    "PRICE_TIERS_DIAM":  [ {"max": 0.14}, ..., {"max": null} ],
    "PRICE_TIERS_COLOR": [ {"max": 0.49}, ..., {"max": null} ],
    "DJR_MATRIX":   [ {"l": "< 1.00 ct", "max": 0.99, "p": [...]}, ... ],
    "DJR_K_COLOR":  1.10,
    "K_MONTATO":    { "diam": {"base": 1.35, ...}, ... },
    "TENNIS_FACTOR":{ "diam": {"base": 55,   ...}, ... },
    "CONTORNO_TIERS": [...],
    "certParams":   {"xe": 40, "xl_sm": 1.5, "xl_lg": 22, "xs_sm": 11, "xs_lg": 16, "csec": 25},
    "QUOT":         {"base": 600, "media": 1800, "alta": 4000},
    "metalPrices":  {"Oro 18k (750‰)": 43, ...}
  }
}
```

> `{"max": null}` è la serializzazione JSON di `Infinity` — indica l'ultima fascia di peso. L'app lo converte automaticamente.

---

## 📱 Installare come app sul telefono

L'app funziona come **PWA (Progressive Web App)**: nessuno store, installazione diretta dal browser.

**Android (Chrome):**
1. Apri il link dell'app nel browser
2. Menu (⋮) → *Aggiungi a schermata Home*

**iPhone (Safari):**
1. Apri il link dell'app in Safari
2. Tocca il tasto **Condividi** (□↑) → *Aggiungi a schermata Home*

---

## 📐 Formula certificato Std.

```
PIETRA SCIOLTA (DGR — Diamond/Gem Grading Report)
  Cert = PRICE_TABLE[categoria][cliente][fascia_ct]
         + Laser (€1.5 se <1ct · €... se ≥1ct)
         + Seal  (€11  se <1ct · €... se ≥1ct)
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

---

## Crediti

Creato da **Alessandro Sequino**
