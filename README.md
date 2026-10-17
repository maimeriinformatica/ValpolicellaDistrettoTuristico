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
| Cibo e vino | 98 cantine e la ristorazione del territorio, in schede filtrabili |
| Dove dormire | 74 strutture ricettive in schede filtrabili, con valutazioni |
| Percorsi | 27 itinerari a piedi, in bici, MTB e a cavallo |
| Pianifica | Costruttore di itinerari con mappa finale su Google Maps |
| Storia | Cenni storici, arte, agricoltura e bibliografia |
| Documenti | Mappe, tracce GPX e materiali scaricabili |
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

## Fotografie

Il portale usa 8 fotografie d'ambiente (vigneti, colline, cantina) prese dalla ricerca
"Valpolicella" di [Magnific](https://www.magnific.com/it/foto-vettori-gratuito/valpolicella)
(ex Freepik), tutte della categoria **gratuita**. Il meccanismo è a doppia sorgente:

1. il sito cerca prima il file locale in `assets/img/` (es. `hero.jpg`);
2. se non c'è, carica la stessa foto dall'indirizzo originale di Magnific;
3. se non arriva nemmeno quella, il riquadro fotografico sparisce da solo, senza buchi.

L'elenco dei file e degli originali è in `assets/img/LEGGIMI.txt`. **Consiglio:** scarica
le foto con un account gratuito Magnific e mettile in `assets/img/`, così il sito non
dipende da un servizio esterno. La licenza gratuita richiede l'attribuzione, già presente
nel piè di pagina. Le foto sono d'ambiente (non scatti certificati della Valpolicella):
quando il distretto avrà immagini proprie del territorio, basta sostituire gli 8 file
mantenendo gli stessi nomi.

---

### Immagini dei luoghi da Wikipedia

Le schede della sezione **Luoghi** (pievi, ville, borghi e paesaggi) caricano in automatico
la fotografia principale della voce di Wikipedia corrispondente: all'apertura della pagina
il sito interroga una sola volta l'API pubblica di Wikipedia in italiano e, dove la voce
esiste e ha un'immagine, la mostra nella scheda con il collegamento «Wikipedia ↗» alla voce
(da cui si risale ad autore e licenza dell'immagine). Se la voce manca, non ha foto o l'API
non risponde, resta l'illustrazione disegnata: la pagina non si rompe mai.

I titoli delle voci sono nell'attributo `data-wiki` di ciascuna scheda (più titoli separati
da `||`: vince il primo con immagine). Per aggiungere o correggere una voce basta modificare
quell'attributo; usare sempre titoli univoci o già disambiguati, per non rischiare la foto
di un luogo omonimo.

### Contatti da OpenStreetMap e foto Wikipedia per le attività (gratuiti, senza chiave)

Oltre a Google (facoltativo, con chiave), le sezioni **Cibo e vino** e **Dove dormire**
usano due fonti libere che non richiedono alcuna chiave né registrazione:

- **OpenStreetMap** (API Overpass): all'apertura delle sezioni il sito fa **una sola
  richiesta** e integra **telefono, sito web e — dove mappata — l'e-mail** delle attività,
  confrontando i nomi con un criterio prudente (in caso di dubbio non abbina nulla).
  I dati inseriti a mano non vengono mai toccati: OSM riempie solo i campi vuoti.
  Attribuzione «© contributori OpenStreetMap (ODbL)» già nel piè di pagina.
- **Wikipedia**: le cantine e dimore storiche che hanno una voce (Masi, Allegrini,
  Quintarelli, Serego Alighieri, Villa della Torre, Guerrieri Rizzardi…) mostrano la foto
  principale della voce, come già i Luoghi. Si aggiungono con l'attributo `data-wiki`
  sulla card.

Se una card riceve sia la foto Google sia quella Wikipedia, vale la prima arrivata
(le due integrazioni non si sovrascrivono). Il limite da sapere: **per B&B e piccole
attività senza voce Wikipedia non esiste una fonte di foto libera e automatica** —
lì le foto arrivano da Google (con chiave) o dalla gestione manuale/backend.

### Collegamento alle schede Google Business (facoltativo)

Le sezioni **Cibo e vino** e **Dove dormire** possono arricchirsi da sole con la scheda
Google di ogni attività: **foto principale**, **telefono**, **sito web**, valutazione ★ e
il collegamento «Google ↗» alla scheda. Serve una chiave della **Google Maps Platform**:

1. Su [console.cloud.google.com](https://console.cloud.google.com) crea un progetto,
   attiva la **fatturazione** e abilita **Places API (New)**.
2. Crea una **chiave API** e, in *Restrizioni della chiave*, limita l'uso ai referrer HTTP
   del tuo dominio (es. `distrettovalpolicella.it/*`, più il dominio onrender.com):
   la chiave sta nel sito pubblico, la restrizione impedisce che altri la usino.
3. In `index.html` cerca `GOOGLE_PLACES` e incolla la chiave in `key: ''`.

Come lavora: carica i dati **solo per le schede che il visitatore vede davvero**
(mai tutte e 180 insieme) e si ferma a `maxPerVisit` schede per visita (predefinito 40),
così i consumi restano dentro le quote gratuite mensili di Google; le soglie esatte sono
sulla [pagina prezzi di Google Maps Platform](https://mapsplatform.google.com/pricing/).
Le foto arrivano in diretta dai server Google come richiedono i loro termini (non vengono
copiate nel sito) e il titolare della scheda resta citato. Dove il portale ha già telefono
o sito, **i dati curati a mano non vengono toccati**: Google integra solo ciò che manca.
Se per un'attività Google trovasse la scheda sbagliata, si può fissare quella giusta
aggiungendo alla sua card l'attributo `data-gplace="PLACE_ID"`.

**Nota sull'e-mail:** le schede Google Business non espongono l'indirizzo e-mail (il dato
non esiste nella loro API): le e-mail si raccolgono con il modulo di adesione.

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
