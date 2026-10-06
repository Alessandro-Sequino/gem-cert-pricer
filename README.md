<div align="center">

# 💎 Gem Cert Pricer

**Stima istantanea del costo dei certificati gemmologici**

Strumento per gemologi e operatori del distretto orafo **Tarì** (Marcianise, Campania).
Inserisci la caratura e confronta subito il prezzo del certificato sui tre tier T1 · T2 · T3.

[**▶ Apri l'app**](https://alessandro-sequino.github.io/gem-cert-pricer/)

📱 Installabile come app (PWA) · 🔒 Tariffe private, mai nel repository

</div>

---

## Panoramica

Gem Cert Pricer è un'applicazione web **single-file** (un solo `index.html` con CSS e JavaScript inline, zero build, zero dipendenze JS) pensata per il lavoro al banco.

Funziona interamente nel browser: **nessun server, nessun account, nessun dato che lascia il dispositivo**. Le tariffe vivono nel `localStorage` del browser e si spostano tra dispositivi con un file `.gcp.json`.

| Schermata | Descrizione |
|---|---|
| **Home** | Pagina iniziale con i tre percorsi di stima |
| **Stima certificato** | Pietra sciolta · Montato · Tennis, con confronto T1/T2/T3 e fasce evidenziate |
| **Tariffe** | Editor delle tabelle di prezzo, import/export `.gcp.json` |

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

TENNIS
  In arrivo
```

---

## 🔒 Tariffe separate dal codice

L'app è pubblicata **senza prezzi**: ogni operatore importa il proprio tariffario privato, che non finisce mai nel repository (`*.gcp.json` è in `.gitignore`).

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
      "center": [ … ],
      "halo":   [ … ]
    },
    "tennis": []
  }
}
```

- `max` — limite superiore della fascia in ct (incluso); `null` = fascia aperta
- `t` — prezzi per T1, T2, T3
- `perCt` — `true` se il prezzo è in €/ct e va moltiplicato per la caratura

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

**Sul telefono (PWA):** Android/Chrome → menu ⋮ → *Aggiungi a schermata Home* · iPhone/Safari → Condividi → *Aggiungi a schermata Home*.

---

## 🗂 Struttura

```
gem-cert-pricer/
├── index.html              # L'intera applicazione (HTML + CSS + JS inline)
├── manifest.json           # Manifest PWA
├── icon-192.png / icon-512.png
├── sample-pricing.gcp.json # Template vuoto del tariffario
└── README.md
```

---

## Crediti

Creato da **Alessandro Sequino** · distretto orafo **Tarì**, Campania.

**Ultimo aggiornamento:** ottobre 2026
