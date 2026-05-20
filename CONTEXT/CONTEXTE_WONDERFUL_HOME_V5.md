# CONTEXTE PROJET WONDERFUL HOME
**Version** : 5.0 (Newsletter, Tweaks ultra-étendus, déploiement Vercel + Pages)
**Dernière mise à jour** : 2026-05-20, 16:00

---

## IDENTITÉ DU PROJET

**Nom** : Wonderful Home
**Type** : Landing page luxe pour marque de parfumerie d'intérieur
**Positionnement** : Parfumerie artisanale française, créée à Grasse en 1998
**Fondatrice** : **Anaïs Camizuli** (à utiliser pour toute signature)
**Ton** : Luxe discret, intemporel, sensorialité raffinée
**Fichier principal** : `index.html` (renommé depuis "Wonderful Home.html" en V4.1)

---

## URLS LIVE

- 🌐 **Vercel (canonical)** : https://wonderful-home.vercel.app/
- 🌐 **GitHub Pages (backup)** : https://blancjulien3.github.io/wonderful-home/
- 📦 **Repo GitHub** : https://github.com/blancjulien3/wonderful-home (PUBLIC depuis V5)

Les 2 URLs sont synchronisées automatiquement à chaque `git push` sur `main`.

---

## COLLECTIONS (3 PARFUMS — inchangé depuis V4)

1. **Musc Blanc** — Musc, cachemire, fleur de coton · €68
2. **Pink Love** (anciennement "Linge Frais") — Bergamote, lavande, lin séché · €68
3. **Wood** — Cèdre, vétiver, cuir fumé · €74

---

## DESIGN SYSTEM — DÉFAUT V5

```
Atmosphère : Aube      Tempérament : Maison    Or : Maison
Accent     : Champagne Police titres : Cardo   Police corps : Manrope
Hauteur    : Aérée     Largeur     : Standard  Coins : Vifs
Surface    : Lisse     Motion      : Pleines
Cards      : Cadre     Boutons     : Contour   Séparateurs : Plume
Sceau hero : Logo WH   Densité     : 3 cols
```

> Le défaut est appliqué via 2 mécanismes :
> 1. `<body data-...>` (évite le FOUC avant JS)
> 2. `TWEAK_DEFAULTS` dans le `<script>` (source de vérité au runtime)

### Palette couleurs (base)
- `--ivory:#F5F0E8` · `--ivory-2:#EDE5D7` · `--ivory-3:#E4DAC6`
- `--ink:#1A1814` · `--ink-2:#3A352D` · `--ink-3:#6E6557`
- `--gold:#D9C28A` (champagne, défaut V5) · `--gold-deep:#A89766`

### Typographies chargées (Google Fonts)
- Serif (6) : Cormorant Garamond, Playfair Display, EB Garamond, Cardo, Lora, Crimson Pro
- Sans (6) : Jost, Inter, DM Sans, Manrope, Outfit, Public Sans
- Mono : JetBrains Mono

---

## STRUCTURE DU SITE (8 sections après V5)

| # | Section | ID | Notes |
|---|---|---|---|
| 1 | Navigation | — | Sticky top, logo WH centré (image rendue dans la nav) |
| 2 | **Hero** | `header.hero` | Image salon haussmannien fixe en background (Ken Burns CSS subtil), overlay ivory 12-42%, h1 "Wonderful / Home", sceau hero avec logo WH, signature "Fondée à Grasse · 1998 · Parfumerie d'intérieur" |
| 3 | Marquee | `.strip` | Bandeau défilant |
| 4 | Collections | `#collections` | 3 cartes produits |
| 5 | Sticky Collections | `#fragrances` | 3 panneaux sticky pleine page |
| 6 | Notes olfactives | `#notes` | Grille 3×2 sombre (Jasmin/Cèdre/Musc Blanc/Figue/Vétiver/Rose) |
| 7 | Ambiances | `#ambiances` | Scroller horizontal 4 cartes (mobile : padding 40px) |
| 8 | Story | `#story` | Grasse / 1998 / signature **Anaïs Camizuli, Fondatrice** |
| 9 | Témoignages | `#testimonials` | 3 colonnes desktop, 1 col mobile |
| 10 | **Newsletter** | `#shop` | Remplace l'ancienne CTA "Parfumez l'instant" — form email + 4 bénéfices |
| 11 | Footer | — | 4 colonnes |

---

## NEWSLETTER (nouvelle V5)

- Stamp "Restez en contact" + titre "Recevez nos / nouveautés."
- Form inline : `<input type="email">` + `<button>S'inscrire</button>`
- Validation regex côté client + feedback en italique doré
- Stockage temporaire dans `localStorage["wh-newsletter"]`
- **À brancher** sur Brevo / Mailchimp / Formspree pour collecter réellement les emails

---

## SYSTÈME TWEAKS (refonte massive V4 → V5)

### Inventaire des leviers (17 + 12 presets)

**Couleurs (3)**
- Accent : 12 options (or, champagne, cuivre, rose, sauge, terre cuite, bleu nuit, anthracite, olive, lin, brique, indigo)
- Atmosphère : aube / crépuscule / nuit
- Or (intensité) : voilé / maison / éclatant

**Typographie (4)**
- Police titres : 6 options (cormorant, playfair, ebgaramond, cardo, lora, crimson)
- Police corps : 6 options (jost, inter, dmsans, manrope, outfit, publicsans)
- Tempérament : murmure / maison / couture
- Initiale (ampersand) : & / et / ×

**Mise en page (3)**
- Hauteur (rythme vertical) : aérée / standard / resserrée
- Largeur container : étroite / standard / large
- Coins : vifs / doux / arrondis (**N'affecte PAS le sceau hero**, qui reste rond)

**Matière & mouvement (2)**
- Surface : lisse / grain / vélin
- Animations : coupées / discrètes / pleines

**Détails éditoriaux (5 nouveaux en V5)**
- Style cards : cadre / sans cadre / ombré / surélevé
- Style boutons : contour / plein / souligné / pilule
- Séparateurs : ligne / losange / étoile / plume
- Sceau hero : logo / étoile / initiale / sans
- Densité produits : 2 / 3 / 4 colonnes

**12 PRESETS prêts en 1 clic**
Maison, Boudoir, Atelier, Grasse, Minuit, Terre cuite, Lavande, Versailles, Riviera, Atelier 1900, Cuir & Cheminée, Botanique, Couture, Lin

### Accès au panneau (production)
- **Bouton flottant : MASQUÉ** (`.tweaks-trigger{display:none !important}`)
- **Panneau : MASQUÉ par défaut** (`.tweaks-panel{display:none}`)
- **Raccourci secret : touche `T`** — invoque le panneau via `body.tweaks-summoned`
- **Esc / ✕** : ferme

### Persistance
- Chaque modif sauvegardée dans `localStorage["wh-tweaks-v1"]`
- Au chargement : `TWEAK_DEFAULTS` puis merge avec localStorage
- Bouton "Réinitialiser" : `localStorage.removeItem` + retour aux defaults
- Bouton "Exporter ↗" : copie la config JSON dans le presse-papier

> ⚠️ Le localStorage est **par navigateur, par device**. Pour qu'un design devienne global (visible par tous), il faut hardcoder dans `TWEAK_DEFAULTS` + `<body data-*>`.

### Réactiver le panneau définitivement
Supprimer les 2 règles `display:none` en tête de la section "TWEAKS SYSTEM — DÉSACTIVÉ" dans le CSS.

---

## ASSETS IMAGES

### Images servies en URL (relatives)
- `images/hero-bg.jpg` (518 Ko, salon haussmannien doré) — background du hero

### Images embedded base64 dans le HTML
- `logo.png` (monogramme WH) — nav + sceau hero
- 3 produits (musc-sf, pink-sf, wood-sf) — cards Collections + sticky panels
- 4 ambiances JPEG (~250 Ko) — section Ambiances
- 1 grasse.jpg — section Story

---

## FICHIERS TECHNIQUES

### Fichier principal : `index.html`
- **Lignes** : ~2530
- **Taille** : ~2.54 Mo
- **Scripts inline** : UI, tweaks system (avec persistance), newsletter
- **CSS** : tout inline dans `<style>`

### Structure du projet (V5)
```
WONDERFUL-HOME/
├── .git/                       # repo public, branch main
├── .claude/                    # config Claude (gitignored)
├── .gitignore                  # exclut .DS_Store, .bak, CAPTURE D'ÉCRAN/
├── CAPTURE D'ÉCRAN/            # screenshots de travail (gitignored)
├── CONTEXT/
│   ├── CHECKLIST_WONDERFUL_HOME_V5.md
│   ├── CONTEXTE_WONDERFUL_HOME_V5.md (ce fichier)
│   └── INSTRUCTIONS_WONDERFUL_HOME_V3.md (règles inchangées)
├── CLAUDE.md                   # instructions projet pour Claude
├── images/
│   ├── ambiance-*.jpg (4)
│   ├── grasse.jpg
│   ├── hero-bg.jpg             # ★ utilisé par le hero (URL relative)
│   ├── logo.png                # ★ embedded base64
│   ├── musc-sf.png / pink-sf.png / wood-sf.png
│   └── bougie.png / diffuseur.png / hero-glass-sf.png (réserve)
└── index.html                  # ★ fichier principal (~2.5 Mo)
```

---

## DÉPLOIEMENT

### Workflow auto-deploy
1. Modifier `index.html` localement
2. `git add -A && git commit -m "..." && git push`
3. **GitHub Pages** : ~1 min pour build + live
4. **Vercel** : ~1 min également (auto-deploy connecté au repo)

### Gestion du repo
- Visibilité : **PUBLIC** (passé en public en V5 pour activer GitHub Pages)
- Branch prod : `main`
- Pas de force-push, pas de --amend après push

---

## CHANGEMENTS V4 → V5 (20 commits, ~3h)

### Système Tweaks
- Bouton trigger flottant + raccourci T (V4)
- **Étension massive** : 6→12 presets, 8→12 accents, 4→6 polices serif, 4→6 sans (V5)
- **5 nouveaux leviers** : cards / boutons / séparateurs / sceau / densité (V5)
- **Persistance localStorage** wh-tweaks-v1 (V5)
- **Masqué en prod** + raccourci T pour réactivation (V5)

### Hero
- Gallery crossfade 4 ambiances → image salon haussmannien fixe (V5)
- Logo WH dans le sceau (cercle agrandi 78px, anneau dashed retiré)
- Sides "Édition 2026 / N°07 / Livraison offerte" supprimés
- Overlay allégé (35-70% → 12-42%) pour révéler l'image

### Sections
- Section CTA "Parfumez l'instant" → Newsletter (form email + 4 bénéfices)
- Fondatrice : "Émilie Laurent (Maître Parfumeur)" → "Anaïs Camizuli (Fondatrice)"
- Vétiver / Rose : descriptions raccourcies à 2 lignes
- "&" retiré du nom de marque partout

### Mobile (nombreux fixes)
- Notes head : grid 3-col → 1-col empilé
- Ambiances scroller : padding-left 24 → 40px + ::after symétrique
- Écart testimonials → newsletter : forcé !important contre overrides hauteur
- Collections head : margin-bottom 80 → 32px sur mobile
- Swipe horizontal : `overflow-x:hidden` + `touch-action:pan-y` body + `pan-x` scroller
- Image hero remplacée (nouvelle version `hero-section-test.png` → compressée en JPEG)

### Infrastructure
- Renommé "Wonderful Home.html" → "index.html"
- Removed `vercel.json` (plus de rewrite nécessaire)
- Repo passé en PUBLIC
- GitHub Pages activé (URL alternative)

---

## PRINCIPES DESIGN (inchangés)

### ✅ Ce qu'on fait
- Luxe discret, intemporalité, sensorialité, respiration, hiérarchie typo
- Animations subtiles (jamais flashy)

### ❌ Ce qu'on évite
- Couleurs flashy, gradients criards, surcharge, UI générique SaaS

---

## RÉFÉRENCES UTILES (lignes index.html V5)

- Body data-attributes hardcoded : ligne 1414
- Hero (CSS) : ~95-240 (incl. background gallery + overlay)
- Tweaks CSS overrides : ~970-1140 (atmosphère / tempérament / or / hauteur / corners / motion / cards / buttons / separators / seal / density)
- Tweaks PANEL CHROME : ~1310 puis
- Tweaks HTML panel : ~1900-2110
- Newsletter HTML : ~1793-1820
- TWEAK_DEFAULTS (JS) : ~2255
- PRESETS (JS) : ~2295
- Persistance localStorage : ~2273

---

**Contact projet** : Julien (entrepreneur, Marseille)
**Timezone** : Europe/Paris
**Version docs** : 5.0
