# Distretto Turistico Valpolicella

Portale turistico a 360° del **Distretto Turistico Valpolicella APS**: luoghi, cantine,
ospitalità, percorsi e la *Distretto Turistico Card* negli **8 comuni** della Valpolicella
(Dolcè, Fumane, Marano, Negrar, Pescantina, San Pietro in Cariano, Sant'Ambrogio,
Sant'Anna d'Alfaedo).

Sito **statico in un unico file** (`index.html`): nessuna build, nessuna dipendenza da
installare, nessun database. Il logo e le immagini sono incorporati nel file stesso.

Realizzato da **MBR Servizi by Maimeri Informatica**.

---

## Contenuti del portale

| Sezione | Contenuto |
|---|---|
| Territorio | Gli 8 comuni, mappa e inquadramento della valle |
| Progettualità | Missione, impegni, promozioni e idee territoriali |
| Luoghi | 36 schede filtrabili per tipologia e per comune |
| Cantine | Directory di 98 cantine con ricerca e micro-schede |
| Dove dormire | 74 strutture ricettive con filtri e valutazioni |
| Percorsi | 27 itinerari a piedi, in bici, MTB e a cavallo |
| Pianifica | Costruttore di itinerari con mappa finale su Google Maps |
| Storia | Cenni storici, arte, agricoltura e bibliografia |
| Documenti | Mappe, tracce GPX e materiali scaricabili |
| La rete | Associazioni del territorio e partner |
| Card | Distretto Turistico Card: vantaggi e categorie |
| Area soci | Adesioni e convenzioni |
| Adesione | Modulo compilabile online e stampabile |

---

## Anteprima in locale

Apri `index.html` con un doppio clic: funziona anche senza connessione (tranne i caratteri
tipografici, che vengono caricati da Google Fonts).

Per un piccolo server locale:

```bash
python3 -m http.server 8000
# poi apri http://localhost:8000
```

---

## 1. Caricare il progetto su GitHub

**Il punto più importante:** `index.html` deve trovarsi nella **radice** del repository.
Aprendo il repo su GitHub devi vedere subito `index.html`, non una cartella che lo contiene.

1. Crea un repository vuoto su GitHub, **senza** aggiungere README o .gitignore.
2. Dal terminale, dentro questa cartella:

```bash
git init
git add .
git commit -m "Portale Distretto Turistico Valpolicella"
git branch -M main
git remote add origin https://github.com/TUO-UTENTE/NOME-REPO.git
git push -u origin main
```

Se preferisci non usare il terminale: nella pagina del repository vuoto scegli
**uploading an existing file** e trascina *il contenuto* della cartella, non la cartella stessa.

---

## 2. Pubblicare su GitHub Pages

Il workflow di deploy automatico è già incluso in `.github/workflows/deploy.yml`.

1. **Settings → Pages**
2. In *Build and deployment → Source* scegli **GitHub Actions**
3. Attendi il completamento (lo segui nel tab **Actions**)
4. Il sito sarà online su `https://TUO-UTENTE.github.io/NOME-REPO/`

In alternativa, senza workflow: *Settings → Pages → Deploy from a branch* → `main` → `/ (root)`.

---

## 3. Pubblicare su Render

> Su Render questo progetto è uno **Static Site**, **non** un Web Service.
> Scegliendo "Web Service" il deploy fallisce, perché Render cercherebbe un comando di avvio
> che un sito statico non ha.

### Procedura consigliata (manuale)

1. Accedi a [dashboard.render.com](https://dashboard.render.com)
2. **New +** → **Static Site**
3. Collega il repository GitHub e selezionalo
4. Compila così:

   | Campo | Valore |
   |---|---|
   | Name | `distretto-valpolicella` |
   | Branch | `main` |
   | Root Directory | *lascia vuoto* |
   | Build Command | *lascia vuoto* |
   | Publish Directory | `.` |

5. **Create Static Site** → online su `https://NOME.onrender.com`

### In alternativa: Blueprint

Il file `render.yaml` è già pronto e validato.
**New +** → **Blueprint** → seleziona il repository → conferma.

---

## 4. Altre piattaforme

- **Netlify** — trascina la cartella su [app.netlify.com/drop](https://app.netlify.com/drop),
  oppure collega il repository (configurazione già in `netlify.toml`)
- **Vercel** — importa il repository: riconosce automaticamente il sito statico
- **Hosting tradizionale** — carica i file via FTP nella cartella pubblica del dominio

---

## Risoluzione degli errori più comuni

**"Publish directory does not exist" oppure pagina "Not Found"**
`index.html` non è nella radice del repository. Verifica su GitHub: se i file sono dentro una
sottocartella, spostali nella radice oppure imposta `Root Directory` con il nome di quella
cartella nelle impostazioni del servizio.

**"Missing start command" / il servizio si riavvia in continuazione**
Hai creato un *Web Service* invece di uno *Static Site*: elimina il servizio e ricrealo.

**"error parsing render.yaml"**
Sintassi YAML non valida. Attenzione ai due punti seguiti da spazio dentro un valore non
quotato: vanno racchiusi tra virgolette.

**"Build failed" senza dettagli**
Apri il tab **Logs** del servizio: la causa reale è nelle ultime righe. Per questo progetto la
build non deve fare nulla, quindi il Build Command può restare vuoto.

**Pagina bianca o senza stile**
`index.html` è stato troncato durante il caricamento. Il file completo pesa circa 650 KB.

**Il primo accesso è lento**
Comportamento normale del piano gratuito di Render dopo un periodo di inattività.

---

## Personalizzazione

Tutto si modifica in `index.html`:

- **Colori e caratteri** — blocco `:root { ... }` all'inizio del `<style>`
- **Testi e schede** — nelle rispettive `<section>`
- **Operatori soci** — blocco `const SOCI = [...]` nello script: una riga per operatore,
  con nome e vantaggio offerto con la Card

> ⚠️ **Prima della pubblicazione definitiva:** l'elenco `SOCI` attualmente presente è
> **dimostrativo**. Va sostituito con gli aderenti reali, altrimenti si attribuisce a imprese
> vere un'adesione che non hanno. Vanno inoltre inseriti i recapiti reali al posto di
> `info@distrettovalpolicella.it` e caricati i documenti scaricabili.

---

## Struttura dei file

```
.
├── index.html                     # il portale completo
├── assets/
│   ├── logo.png                   # logo (sorgente)
│   ├── logo-white.png             # logo per fondi scuri
│   └── favicon.png                # icona del sito
├── README.md                      # questo file
├── LICENSE
├── robots.txt                     # indicazioni per i motori di ricerca
├── sitemap.xml
├── .nojekyll                      # richiesto da GitHub Pages
├── .gitignore
├── render.yaml                    # configurazione Render
├── netlify.toml                   # configurazione Netlify
├── vercel.json                    # configurazione Vercel
└── .github/workflows/deploy.yml   # deploy automatico su GitHub Pages
```

---

© 2026 Distretto Turistico Valpolicella APS · Sviluppo: MBR Servizi by Maimeri Informatica
