# Site de la chorale — Partitions & Enregistrements

Site web simple (une seule page) pour que les choristes révisent leurs partitions
et, plus tard, écoutent les enregistrements voix par voix.

Inspiré de https://lamilanese.github.io/chorale_da/

## Contenu du dossier

```
site chorale/
├── index.html          ← la page du site (tout est dedans : design + code)
├── partitions/         ← les partitions PDF (déjà découpées, une par chant)
│   ├── 00-toutes-les-partitions.pdf   (le PDF complet, bouton en haut)
│   ├── 01-veni-creator.pdf
│   ├── 02-cantate-domino.pdf
│   └── ... (12 chants)
├── audio/              ← à remplir avec les MP3 (vide pour l'instant)
└── README.md           ← ce fichier
```

## Comment ça marche

- Le choriste choisit sa **voix** (Soprane / Alto / Ténor / Basse).
- Pour chaque chant, 3 boutons :
  - 👁 **Partition** : affiche le PDF (à droite sur ordinateur, dans un onglet sur mobile).
  - 🎤 **Ma voix** : écoute l'enregistrement de sa propre voix (désactivé tant qu'il n'y a pas de MP3).
  - 👥 **Ensemble** : écoute toutes les voix ensemble.

Tant qu'aucun enregistrement n'est ajouté, les boutons audio restent grisés
et un bandeau indique « enregistrements à venir ».

## Ajouter les enregistrements audio (plus tard)

1. Dépose les fichiers **MP3** dans le dossier `audio/`.
2. Ouvre `index.html`, trouve la section `const songs = [ ... ]` et remplace
   les `""` par le chemin du fichier. Exemple pour Cantate Domino :

   ```js
   { id: 2, title: "Cantate Domino", subtitle: "G. Pitoni — Psaume 149",
     sheetMusic: "partitions/02-cantate-domino.pdf",
     audio: {
       soprano: "audio/02-cantate-domino-soprano.mp3",
       alto:    "audio/02-cantate-domino-alto.mp3",
       tenor:   "audio/02-cantate-domino-tenor.mp3",
       basse:   "audio/02-cantate-domino-basse.mp3",
       tous:    "audio/02-cantate-domino-tous.mp3"
     } },
   ```

   Laisse `""` pour une voix que tu n'as pas encore enregistrée : son bouton
   restera simplement grisé.

### Noms de fichiers conseillés (pour rester organisé)

| # | Chant | Base du nom de fichier |
|---|-------|------------------------|
| 1 | Veni Creator Spiritus | `01-veni-creator-<voix>.mp3` |
| 2 | Cantate Domino | `02-cantate-domino-<voix>.mp3` |
| 3 | Introït Deus Israel | `03-introit-deus-israel-<voix>.mp3` |
| 4 | Kyrie De Angelis | `04-kyrie-de-angelis-<voix>.mp3` |
| 5 | Gloria De Angelis | `05-gloria-de-angelis-<voix>.mp3` |
| 6 | Da pacem, Domine | `06-da-pacem-domine-<voix>.mp3` |
| 7 | Sanctus | `07-sanctus-<voix>.mp3` |
| 8 | Agnus Dei | `08-agnus-dei-<voix>.mp3` |
| 9 | Ave Verum Corpus | `09-ave-verum-corpus-<voix>.mp3` |
| 10 | Vous êtes dans mon âme | `10-vous-etes-dans-mon-ame-<voix>.mp3` |
| 12 | Salve Regina | `12-salve-regina-<voix>.mp3` |

`<voix>` = `soprano`, `alto`, `tenor`, `basse` ou `tous`.

## Personnaliser le titre

Dans `index.html`, en haut :
- balise `<title>` (onglet du navigateur),
- le `<h1>` et le `<p class="subtitle">` dans le `<header>` (titre affiché).

## Mettre le site en ligne (GitHub Pages, gratuit)

1. Crée un compte sur https://github.com si tu n'en as pas.
2. Crée un dépôt (repository), par exemple `chorale-mariage`.
3. Envoie le **contenu** de ce dossier `site chorale` (pas le dossier lui-même)
   à la racine du dépôt : `index.html`, `partitions/`, `audio/`.
4. Dans le dépôt : onglet **Settings → Pages**.
5. Sous « Build and deployment », choisis **Source : Deploy from a branch**,
   branche **main**, dossier **/ (root)**, puis **Save**.
6. Au bout d'une minute, GitHub affiche l'adresse publique
   (`https://<ton-pseudo>.github.io/chorale-mariage/`) : c'est le lien à
   partager aux choristes.

À chaque fois que tu modifies un fichier et que tu l'envoies sur GitHub,
le site se met à jour tout seul.

## Tester en local (sur ton ordinateur)

Double-cliquer sur `index.html` fonctionne pour voir la page, mais l'affichage
des PDF dans le panneau de droite peut être bloqué par le navigateur.
Pour un test fidèle, lance un petit serveur depuis ce dossier :

```bash
python -m http.server 8000
```

puis ouvre http://localhost:8000 dans ton navigateur.
