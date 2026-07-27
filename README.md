# Distretto Turistico della Valpolicella

Portale turistico a 360° del territorio della Valpolicella: luoghi, cantine, ospitalità e
percorsi, con la distinzione tra **Valpolicella Classica storica** e zona allargata.

Sito statico in un **unico file** (`index.html`): nessuna build, nessuna dipendenza.
Realizzato da **MBR Servizi by Maimeri Informatica**.

---

## 🚀 Anteprima in locale

Non serve installare nulla: apri semplicemente `index.html` con un doppio clic nel browser.

Se preferisci un piccolo server locale (consigliato per i test):

```bash
# con Python (già presente su Mac/Linux)
python3 -m http.server 8000
# poi apri http://localhost:8000
```

---

## 📦 Mettere il progetto su GitHub

1. Crea un nuovo repository vuoto su GitHub (es. `distretto-turistico-valpolicella`),
   **senza** README/‌.gitignore (li hai già qui).
2. Da terminale, dentro questa cartella:

```bash
git init
git add .
git commit -m "Primo commit: portale Distretto Turistico della Valpolicella"
git branch -M main
git remote add origin https://github.com/TUO-UTENTE/distretto-turistico-valpolicella.git
git push -u origin main
```

Sostituisci `TUO-UTENTE` con il tuo nome utente GitHub.

---

## 🌐 Pubblicare il sito (gratis)

### Opzione 1 — GitHub Pages (la più semplice)

**Metodo automatico (già configurato):** è incluso il workflow
`.github/workflows/deploy.yml`. Dopo il primo `push` su `main`:

1. Vai su **Settings → Pages** del repository.
2. In *Build and deployment → Source* scegli **GitHub Actions**.
3. Attendi che l'Action finisca: il sito sarà online su
   `https://TUO-UTENTE.github.io/distretto-turistico-valpolicella/`.

**Metodo manuale (alternativo):** Settings → Pages → *Deploy from a branch* →
branch `main`, cartella `/ (root)` → Save.

### Opzione 2 — Render (render.com)

1. Su Render: **New → Static Site** e collega il repository GitHub.
2. Impostazioni:
   - **Build Command:** *(lascia vuoto)*
   - **Publish Directory:** `.`
3. Deploy. In alternativa, il file `render.yaml` incluso permette il deploy via *Blueprint*.

### Opzione 3 — Netlify

Trascina la cartella su [app.netlify.com/drop](https://app.netlify.com/drop) **oppure**
collega il repo: la configurazione è già in `netlify.toml` (publish = `.`).

### Opzione 4 — Vercel

Importa il repository su Vercel: riconosce automaticamente un sito statico (nessuna build).

---

## ✏️ Personalizzazione

Tutti i contenuti e lo stile sono in `index.html`.

- **Testi, luoghi, cantine, hotel, percorsi:** sono nelle rispettive sezioni `<section>`.
- **Colori e font:** in cima al file, nel blocco `:root { ... }` del `<style>`.
- I dati di cantine e strutture sono **segnaposto di esempio** ("Esempio A/B…"):
  sostituiscili con l'elenco reale degli associati.

---

## 🗂️ Struttura

```
.
├── index.html                     # il portale (tutto qui dentro)
├── README.md                      # questo file
├── LICENSE                        # licenza
├── .nojekyll                      # evita l'elaborazione Jekyll su GitHub Pages
├── .gitignore
├── netlify.toml                   # config Netlify
├── render.yaml                    # config Render
├── vercel.json                    # config Vercel
└── .github/workflows/deploy.yml   # deploy automatico su GitHub Pages
```

---

© 2026 MBR Servizi by Maimeri Informatica. Vedi `LICENSE`.
