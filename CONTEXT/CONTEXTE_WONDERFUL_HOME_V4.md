# CONTEXTE PROJET WONDERFUL HOME
**Version** : 4.0 (refonte Hero + Témoignages 3 colonnes)
**Dernière mise à jour** : 2026-05-20, 12:30

---

## IDENTITÉ DU PROJET

**Nom** : Wonderful Home
**Type** : Landing page luxe pour marque de parfumerie haut de gamme
**Produit phare** : Musc Blanc (parfum d'intérieur)
**Positionnement** : Parfumerie artisanale de Grasse, créée en 1998
**Ton** : Luxe discret, intemporel, sensorialité raffinée

---

## COLLECTIONS (3 PARFUMS)

### 1. Musc Blanc (hero product des cards Collections)
- **Notes** : Musc, cachemire, fleur de coton
- **Couleur dominante** : Doré profond (#C98C3C)
- **Prix** : €68
- **Image** : musc-sf.png

### 2. Pink Love (anciennement "Linge Frais", renommé en V3)
- **Notes** : Bergamote, lavande, lin séché
- **Couleur dominante** : Rose poudré
- **Prix** : €68
- **Image** : pink-sf.png

### 3. Wood
- **Notes** : Cèdre, vétiver, cuir fumé
- **Couleur dominante** : Boisé sombre
- **Prix** : €74
- **Image** : wood-sf.png

---

## DESIGN SYSTEM

### Palette couleurs
```css
--ivory:#F5F0E8       /* Fond principal */
--ivory-2:#EDE5D7     /* Surfaces secondaires */
--ivory-3:#E4DAC6     /* Bordures, séparateurs */
--ink:#1A1814         /* Texte principal */
--ink-2:#3A352D       /* Texte secondaire */
--ink-3:#6E6557       /* Texte tertiaire */
--gold:#C9A84C        /* Accents */
--gold-deep:#A8862F   /* CTA, highlights */
--sand:#C9BBA0        /* Neutre chaud */
```

**Règle** : jamais de couleur hardcodée. Exception assumée : `.tweaks-panel`.

### Typographie
```css
--serif:'Cormorant Garamond' /* titres, signatures */
--sans:'Jost'                /* body, UI, navigation */
--mono:'JetBrains Mono'      /* numéros, captions */
```

### Système de tweaks (6 leviers)
- **Atmosphère** : aube / crépuscule (défaut) / nuit
- **Tempérament** : murmure / maison / couture
- **Or** : voilé / maison / éclatant
- **Initiale** : & / et / ×
- **Hauteur** : aérée / standard / resserrée
- **Surface** : lisse / grain / vélin

---

## STRUCTURE DU SITE (refonte V4)

| # | Section | ID | Notes |
|---|---|---|---|
| 1 | Navigation | — | Sticky top, blur au scroll |
| 2 | **Hero (refait V4)** | `header.hero` | 3 colonnes typo pure, sceau doré central, signature "Fondée à Grasse", **plus de flacon** |
| 3 | Marquee | `.strip` | Bandeau défilant |
| 4 | Collections | `#collections` | 3 cartes produits (hover unifié V4 : image + swatch scale) |
| 5 | Sticky Collections | `#fragrances` | 3 panneaux sticky pleine page (Musc / Pink Love / Wood) |
| 6 | Notes olfactives | `#notes` | Grille 3×2 sombre |
| 7 | Ambiances | `#ambiances` | Scroller horizontal 4 cartes |
| 8 | Story | `#story` | Grasse / 1998 / signature parfumeur |
| 9 | **Témoignages (refait V4)** | `#testimonials` | **3 colonnes côte-à-côte sur desktop**, hairlines verticales, 1 col mobile |
| 10 | CTA | `#shop` | Coffret découverte |
| 11 | Footer | — | 4 colonnes + newsletter |

---

## REFONTE V4 (2026-05-20) — DÉTAIL

### Hero — composition éditoriale pure
- ❌ Suppression du flacon test (`<img id="hero-bottle">`) qui dupliquait le Musc Blanc des Collections
- ❌ Suppression de tout le CSS `.bottle-stage` (~32 lignes) et de l'animation `bottleEntrance`
- ❌ Suppression du JS parallax `.bottle-stage` (mort)
- ✅ Ajout `.hero-mark` : composition triple (rule + sceau circulaire doré 64px + rule) après la tagline
- ✅ Sceau central : cercle 64px, bordure dorée, anneau intérieur dashed, ampersand italic 32px gold-deep, animation `sealGlow` 6s
- ✅ Signature : "Fondée à Grasse · 1998 · Parfumerie d'intérieur" en sans 10px letter-spacing .34em
- ✅ Centre du hero : `justify-content:center` (vs `flex-start`) pour balance verticale
- ✅ JS scroll : nouveau fade/parallax léger sur `.hero-mark` (préserve l'animation reveal à scroll=0)
- ✅ Responsive : breakpoint 600px adapté (seal 56px, signature 9px letter-spacing .28em)

### Témoignages — grid 3 colonnes
- ❌ Suppression des `<span class="divider">` losanges
- ✅ Layout : `grid-template-columns:repeat(3,1fr)` (vs `flex-direction:column`)
- ✅ Hairlines verticales entre colonnes via `blockquote + blockquote::before` (gradient gold)
- ✅ Le `.mark` (guillemet ouvrant) ajouté aux 3 témoignages pour cohérence
- ✅ Quote font-size : `clamp(18px,1.4vw,22px)` (vs 26-38px) pour s'adapter au format colonne
- ✅ Cite : `<em>` (nom) en bloc au-dessus, ville en sous-ligne
- ✅ Témoignage 2 : "Linge Frais" → "Pink Love" (cohérence renommage)
- ✅ Responsive ≤960px : `grid-template-columns:1fr`, hairlines passent en horizontales, quote bumps à clamp(22-28px)

### Polish design
- ✅ Cards produits : hover unifié (image scale 1.04 + swatch scale 1.06 + box-shadow douce)
- ✅ Alt orphelin "Linge Frais" corrigé en "Pink Love" sur sticky panel

### Nettoyage code
- ~50 lignes de CSS mort supprimées (`.bottle-stage`, `bottleEntrance`, breakpoints associés)
- 1 bloc JS parallax mort supprimé

---

## ASSETS IMAGES — ÉTAT RÉEL (V4)

### Images intégrées en base64 (11 au total, ~2.4 MB)

> Note V4 : `hero-glass-sf.png` (le flacon hero test) reste embarqué dans les sources `images/` mais n'est plus utilisé dans le HTML.

**Produits cartes** (3) : `musc-sf.png`, `pink-sf.png`, `wood-sf.png`
**Produits sticky panels** (3) : mêmes 3 images dupliquées
**Ambiances lifestyle** (4 JPEG ~250 Ko chacun) : salon, chambre, entrée, bain
**Story** (1 JPEG) : grasse.jpg ~361 Ko

---

## FICHIERS TECHNIQUES

### Fichier principal : `Wonderful Home.html`
- **Lignes** : ~1799 (V3 : ~1880, V4 : −80 lignes par suppression code mort)
- **Taille** : ~2.40 Mo (V3 : 2.46 Mo)
- **Scripts inline** : UI interactions + tweaks system + scroll fade hero-mark
- **CSS** : tout inline dans `<style>`

### Structure du projet (V4)
```
WONDERFUL-HOME/
├── .claude/
├── CAPTURE D'ÉCRAN/             # 21 Mo screenshots — à déplacer
├── CONTEXT/
│   ├── CHECKLIST_WONDERFUL_HOME_V4.md
│   ├── CONTEXTE_WONDERFUL_HOME_V4.md  (ce fichier)
│   └── INSTRUCTIONS_WONDERFUL_HOME_V3.md  (règles inchangées depuis V3)
├── CLAUDE.md
├── images/
└── Wonderful Home.html
```

### Backup V2 supprimé en V4
- `Wonderful Home.html.bak` (14 Mo) → reste à supprimer après validation visuelle V4 (item ouvert)

---

## PRINCIPES DESIGN (inchangés)

### ✅ Ce qu'on fait
- Luxe discret, intemporalité, sensorialité, respiration, hiérarchie typo, animations subtiles

### ❌ Ce qu'on évite
- Animations flashy, couleurs saturées, surcharge, UI générique, iconographie littérale

---

## RÉFÉRENCES UTILES (V4)

- CSS variables : lignes 11-24
- Hero (CSS) : lignes ~100-200 (h1, tagline, hero-mark, hero-seal, hero-signature)
- Particules : lignes ~225-250 (CSS) + ~1100 (HTML)
- Témoignages (CSS) : lignes ~688-725
- Témoignages (HTML) : lignes ~1480-1500
- Tweaks system : lignes ~770-1020 (CSS) + ~1680+ (JS)
- Scroll fade hero-mark : ligne ~1588

---

**Contact projet** : Julien (entrepreneur, Marseille)
**Timezone** : Europe/Paris
**Version docs** : 4.0
