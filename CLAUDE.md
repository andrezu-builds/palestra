# Palestra UL PPL

PWA (pagina web installabile sul telefono) che mostra i 28 esercizi del programma UL+PPL in 5 giorni,
con un'animazione 2D/3D dell'esecuzione e dei muscoli lavorati, il registro dei pesi e il peso corporeo.
Pubblicata con GitHub Pages (per ora dal branch `modello-3d`).

## File
- `index.html` — tutta l'app: UI, motore 2D (tra `// ===ENGINE START===` e `// ===ENGINE END===`),
  oggetto `EX` con i 28 esercizi, `DAYS`, `WEEK`, registro pesi, peso corporeo, timer di recupero, backup.
  Contiene `APP_VERSION`.
- `sw.js` — service worker cache-first. `VERSION` e la lista `FILES` dei file messi in cache.
- `modello3d.js` — motore 3D (Three.js): carica `models/atleta.glb`, retargeting, IK, prese delle mani,
  pantaloncini, colorazione dei muscoli, attrezzi, telecamera.
- `esercizi3d.js` — `POSE3`: pose A/B, attrezzi (`eq`) e telecamera per ogni esercizio.
- `vendor/three-lite.js` — Three.js ridotto (bundle esbuild con GLTFLoader).
- `models/atleta.glb` — modello umano MakeHuman/MPFB2 (CC0, vedi `models/LICENZA.txt`).

## Regole
- Deve funzionare OFFLINE (in palestra non c'è internet): niente CDN o risorse esterne.
- Ogni modifica pubblicata: aumentare insieme `VERSION` in `sw.js` e `APP_VERSION` in `index.html`.
- Ogni file nuovo va aggiunto a `FILES` in `sw.js`.
- Non cambiare le chiavi di localStorage (`palestra-log-v1`, `palestra-peso-v1`, `mode`, `day`, `metric`,
  `pcRange`, `hint3d`, `tmEnd`, `tmDur`): contengono i dati dell'utente.
- Testi dell'interfaccia in italiano.
- Lavorare su `modello-3d`, poi fare merge in `main`.

## Da fare
- Merge di `modello-3d` in `main` e GitHub Pages da `main`.
- Rifiniture 3D: orlo dei pantaloncini seghettato, dita lunghe nella presa dei manubri su panca inclinata,
  scarpe/vestiti.
