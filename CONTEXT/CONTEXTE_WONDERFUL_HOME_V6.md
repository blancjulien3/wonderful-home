# CONTEXTE PROJET WONDERFUL HOME
**Version** : 6.0 (Alignement DA Instagram + image hero IA + fix sticky)
**Dernière mise à jour** : 2026-05-20, 18:45

---

## IDENTITÉ DU PROJET

**Nom** : Wonderful Home
**Type** : Landing page luxe pour marque de parfumerie d'intérieur
**Positionnement** : Parfumerie artisanale française, créée à Grasse en 1998
**Fondatrice** : **Anaïs Camizuli** (à utiliser pour toute signature)
**Ton** : Quiet luxury beige · slow living · Diptyque / Le Labo / Aesop
**Fichier principal** : `index.html`

---

## DA DE RÉFÉRENCE (V6)

La direction artistique du site est calée sur **la moodboard Instagram officielle de Wonderful Home** (capture de profil + grille de posts) :

- Palette dominante : **beige naturel, lin écru, taupe doux, crème pâle**, légères touches de cuivre/or estompé
- Visuels récurrents : drapé de lin froissé, pampas séchées, fleurs séchées beige, marbre clair, bois pâle, façade pierre Provence
- Typographie : serif classique espacé pour les titres en CAPS, sans serif fin pour le UI
- Atmosphère : aérée, lumineuse, "quiet luxury"
- **Pas de doré flashy**, **pas d'or haussmannien parisien**, **pas de couleurs saturées**

> ⚠️ Pour toute future image hero ou ambiance : doit matcher cette DA. Photos de produits hors gamme (diffuseurs en bouteille verre généralistes) sont à éviter — utiliser uniquement les 3 produits actuels (Musc Blanc / Pink Love / Wood en spray flacon) ou des photos d'ambiance pure sans produit identifiable.

---

## URLS LIVE

- 🌐 **Vercel (canonical)** : https://wonderful-home.vercel.app/
- 🌐 **GitHub Pages (backup)** : https://blancjulien3.github.io/wonderful-home/
- 📦 **Repo GitHub** : https://github.com/blancjulien3/wonderful-home (PUBLIC)

Auto-deploy à chaque `git push` sur `main` (~1 min chacun).

---

## COLLECTIONS (3 PARFUMS)

1. **Musc Blanc** — Musc, cachemire, fleur de coton · €68
2. **Pink Love** — Bergamote, lavande, lin séché · €68
3. **Wood** — Cèdre, vétiver, cuir fumé · €74

---

## DESIGN SYSTEM — DÉFAUT V6

```
Atmosphère : Aube         Tempérament : Maison    Or : Voilé  ← V6 changé
Accent     : Lin (V6 ★)   Police titres : Cormorant Garamond (V6 ★)
Police corps : Jost (V6 ★)
Hauteur    : Aérée        Largeur     : Standard  Coins : Vifs
Surface    : Lisse        Motion      : Pleines
Cards      : Sans cadre (V6 ★)   Boutons : Contour   Séparateurs : Ligne (V6 ★)
Sceau hero : Logo WH      Densité     : 3 cols
```

**Changements V5 → V6 (alignement DA)** :
- Accent : `champagne` → `lin` (`#B8A88E` beige neutre, moins doré)
- Or intensité : `maison` → `voile` (estompe les accents dorés)
- Police titres : `cardo` → `cormorant` (plus éditorial CAPS)
- Police corps : `manrope` → `jost` (plus de personnalité)
- Cards : `frame` → `borderless` (épuré slow living)
- Séparateurs : `quill` → `line` (sobre)

### Palette V6 effective
- `--ivory:#F5F0E8` · `--ivory-2:#EDE5D7` · `--ivory-3:#E4DAC6`
- `--ink:#1A1814` · `--ink-2:#3A352D` · `--ink-3:#6E6557`
- `--gold:#B8A88E` (lin) · `--gold-deep:#85775F`

---

## HERO V6 — IMAGE GÉNÉRÉE PAR NANO BANANA

L'image background du hero (`images/hero-bg.jpg`, 371 Ko JPEG, 1920px) est une **création IA** générée sur Nano Banana / Gemini à partir du prompt suivant (à reproduire si nouvelle régénération souhaitée) :

```
Photographie éditoriale haut de gamme pour une marque de parfumerie
d'intérieur de luxe française. Composition horizontale 16:9, lumière
naturelle douce du matin venant de la gauche. Sujet : un drapé de lin
naturel écru beige reposant sur un comptoir en marbre travertin pâle,
avec un petit bouquet de pampas séchées et fleurs séchées beige dans
un vase crème translucide aux formes minimales. Tons : beige chaud,
écru, crème, taupe doux, ivoire, légers reflets cuivre estompés.
INTERDICTION : aucun produit, aucun flacon, aucun diffuseur, aucune
bougie, aucune étiquette, aucun logo. Atmosphère : quiet luxury,
slow living, Diptyque / Le Labo / Aesop. Profondeur de champ faible,
ombres douces, qualité magazine, 16:9 4K.
```

---

## STRUCTURE DU SITE (inchangée depuis V5)

| # | Section | ID | État V6 |
|---|---|---|---|
| 1 | Navigation | — | Logo WH centré |
| 2 | Hero | `header.hero` | Image IA (drapé lin + pampas), overlay 12-42%, sceau logo |
| 3 | Marquee | `.strip` | OK |
| 4 | Collections | `#collections` | Cards sans cadre (V6) |
| 5 | Sticky Collections | `#fragrances` | **Animation sticky RÉPARÉE V6** (cf bugfix) |
| 6 | Notes olfactives | `#notes` | OK (Vétiver/Rose raccourcis) |
| 7 | Ambiances | `#ambiances` | Mobile padding 40px |
| 8 | Story | `#story` | Signature Anaïs Camizuli |
| 9 | Témoignages | `#testimonials` | 3 col desktop |
| 10 | Newsletter | `#shop` | Form email + 4 bénéfices |
| 11 | Footer | — | OK |

---

## BUGFIX CRITIQUE V6 — STICKY ANIMATION

**Problème** : depuis V5 (où on avait ajouté `body{overflow-x:hidden}` pour bloquer le swipe latéral mobile), les 3 panels sticky de la section Collections (Musc / Pink / Wood) n'animaient plus au scroll.

**Cause** : `overflow-x:hidden` sur `html`/`body` crée un nouveau "scrolling context", ce qui **casse `position:sticky`** des descendants (qui sticky alors à ce nouveau context au lieu du viewport).

**Fix** : remplacé par `overflow-x:clip`. La propriété `clip` empêche le débordement visuel SANS créer de scrolling context → `position:sticky` continue de marcher au viewport.

> ⚠️ Si futur swipe horizontal mobile remontre des problèmes, ne JAMAIS revenir à `overflow-x:hidden` sur html/body. Toujours `clip`.

---

## SYSTÈME TWEAKS (inchangé depuis V5)

### Inventaire
- **17 leviers** + **12 presets**
- Couleurs (3) · Typographie (4) · Mise en page (3) · Matière&motion (2) · Détails éditoriaux (5)
- Polices : 6 serif + 6 sans Google Fonts chargées

### Accès production
- Bouton flottant MASQUÉ + Panel MASQUÉ par défaut
- **Touche `T`** invoque le panneau (raccourci secret)
- **Esc / ✕** ferme
- Persistance localStorage : `wh-tweaks-v1`
- Reset clear le localStorage

### Pour modifier le design GLOBAL (vu par tous visiteurs)
1. Éditer `TWEAK_DEFAULTS` dans le `<script>`
2. Éditer `<body data-*>` au même titre
3. Pas via localStorage (qui est local/per-device)

---

## ASSETS IMAGES

### URL relative
- `images/hero-bg.jpg` (371 Ko, IA Nano Banana, drapé lin + pampas)

### Base64 dans le HTML
- `logo.png` (monogramme WH) — nav + sceau hero
- 3 produits PNG, 4 ambiances JPG, 1 grasse.jpg

### Sources en réserve dans `images/`
- bougie.png, diffuseur.png, hero-glass-sf.png (non utilisés)
- ambiance-*.jpg (originaux 1.8 Mo chacun, versions compressées dans `compressed/`)

---

## CHANGEMENTS V5 → V6 (3 commits, ~1h)

### Alignement DA Instagram
- Diagnostic charte : quiet luxury beige (pas doré parisien)
- Accent : champagne → lin (#B8A88E)
- Or intensité : maison → voilé
- Police titres : Cardo → Cormorant Garamond
- Police corps : Manrope → Jost
- Cards : Cadre → Sans cadre
- Séparateurs : Plume → Ligne

### Hero image
- Étape 1 : test avec `ambiance-salon.jpg` (mais produit diffuseur hors gamme)
- Étape 2 : test avec `grasse.jpg` (champ de jasmin coucher de soleil — pas DA)
- Étape 3 : génération IA Nano Banana sur prompt fourni → image parfaite

### Bugfix sticky animation
- `html,body{overflow-x:hidden}` → `overflow-x:clip`
- Position:sticky des panels Musc/Pink/Wood retrouve son comportement

---

## PROCHAINE ACTION RECOMMANDÉE

**🎯 Tester le rendu live avec la nouvelle DA** sur ordi + iPhone

Si l'image hero IA fonctionne bien avec le texte "Wonderful Home"
superposé : commit final, ready to ship.

Sinon : régénérer une variante sur Nano Banana avec composition
plus à gauche (vase décalé) pour laisser plus de respiration centrale.

---

**Contact projet** : Julien (entrepreneur, Marseille)
**Timezone** : Europe/Paris
**Version docs** : 6.0
