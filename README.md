# TurnTable — Visualiseur 360°

Visualiseur web pour faire pivoter un bâtiment à partir d'une séquence d'images
(« object movie » / turntable). Deux séries sont incluses : **Toiture** et
**Rez-de-chaussée**.

## Fonctionnalités

- Rotation par **glisser** (souris / tactile) et par **flèches** (clic ou maintien).
- **Auto-rotation** légère au démarrage, qui s'arrête à la première interaction.
- **Boucle infinie** dans les deux sens.
- **Sélecteur de série** (Toiture / Rez-de-chaussée) ; l'angle de vue est conservé
  d'une série à l'autre.
- Préchargement avec barre de progression ; la 2ᵉ série se charge à la demande.
- Position et série mémorisées entre les visites (localStorage).
- Navigation au clavier (← / →) en bonus.

## Structure

```
index.html             # le visualiseur (= « Visualiseur 360.html »)
Visualiseur 360.html   # copie identique, nom lisible
toit/                  # série Toiture        : toiture360_0000.webp … _0099.webp
rdc/                   # série Rez-de-chaussée : rdc_0000.webp        … _0099.webp
```

## Utilisation

Ouvrir `index.html` dans un navigateur, ou publier le dépôt via **GitHub Pages**
(Settings → Pages → branche `main`, dossier `/root`).

## Configuration des séries

Dans `index.html`, en haut du script :

```js
const COMMON = { pad: 4, start: 0, count: 100, ext: 'webp' };
const SERIES = [
  { key:'toiture', label:'Toiture',         folder:'toit/', prefix:'toiture360_' },
  { key:'rdc',     label:'Rez-de-chaussée', folder:'rdc/',  prefix:'rdc_' },
];
```

Pour ajouter un niveau (R+1, etc.), ajoutez une entrée dans `SERIES` (avec son
dossier et préfixe) et un bouton correspondant dans le bloc `.series` du HTML.

## Note sur le poids

Les images sont déjà optimisées (1400 px, WebP) : ~8–9 Mo par série, soit ~17 Mo
au total. Les rendus d'origine (2000 px JPEG) ne sont pas inclus dans le dépôt.
