# CHECKLIST PROJET WONDERFUL HOME
**Dernière mise à jour** : 2026-05-20, 16:00
**Version** : 5.0 (Newsletter + Tweaks étendus + Déploiement double)

---

## ÉTAT ACTUEL DU PROJET

- **Fichier principal** : `index.html` (renommé depuis "Wonderful Home.html")
- **Taille** : ~2.54 Mo · ~2530 lignes
- **Déploiement live** :
  - Vercel : https://wonderful-home.vercel.app/
  - Pages : https://blancjulien3.github.io/wonderful-home/
- **Repo GitHub** : https://github.com/blancjulien3/wonderful-home (PUBLIC)
- **Auto-deploy** : actif sur les 2 plateformes via `git push main`

---

## PHASES TERMINÉES

### ✅ Phase 1 — Fondations
- 3 PNG produits, design system, structure HTML

### ✅ Phase 2 — Animations hero
- Particules dorées, marquee, scroll-cue, sceau hero

### ✅ Phase 3 — Compléments visuels
- 4 ambiances, grasse.jpg, recompressions

### ✅ Phase 4 — Audit V3 (mai 18)
- Meta SEO, `<html lang>`, refonte particules, recompression JPEG 14→2.5Mo

### ✅ Phase 5 — Refonte V4 (mai 20 matin)
- Hero gallery 4 ambiances crossfade
- Témoignages 3 colonnes desktop
- Polish hover cards produits

### ✅ Phase 6 — Tweaks system V5 (mai 20 après-midi)
- Bouton flottant + raccourci T (initial)
- Extension : 12 presets / 12 accents / 6+6 polices / 5 nouveaux leviers
- Persistance localStorage (`wh-tweaks-v1`)
- Panneau MASQUÉ en prod, raccourci T pour invoquer

### ✅ Phase 7 — Identité brand (V5)
- Logo WH dans nav + sceau hero
- "&" retiré du nom (était "Wonderful & Home" → "Wonderful Home")
- Fondatrice : Anaïs Camizuli (Fondatrice)

### ✅ Phase 8 — Hero éditorial (V5)
- Gallery crossfade → image salon haussmannien fixe (Ken Burns)
- Overlay allégé 12-42%
- Sides "Édition / Livraison" retirés
- Sceau : cercle 78px avec logo WH (anneau dashed retiré)

### ✅ Phase 9 — Newsletter (V5)
- CTA "Parfumez l'instant" remplacée par section Newsletter
- Form email + 4 bénéfices abonné
- Validation JS + stockage local
- ⏳ À brancher : Brevo / Mailchimp / Formspree (au choix de Julien)

### ✅ Phase 10 — Déploiement (V5)
- GitHub repo créé (privé puis passé public)
- Vercel auto-deploy connecté
- GitHub Pages activé (URL alternative)
- vercel.json supprimé (rewrite plus nécessaire)
- Fichier renommé en `index.html`

### ✅ Phase 11 — Polish mobile (V5)
- Section Notes head : layout cassé → empilé
- Ambiances scroller : padding-left 40px + ::after symétrique
- Témoignages → Newsletter : écart resserré (!important contre overrides hauteur)
- Collections head : margin-bottom mobile divisé par 2.5
- Swipe horizontal : overflow-x:hidden + touch-action:pan-y body + pan-x scroller
- Image hero remplacée

---

## CE QUI RESTE À FAIRE

### 🟢 Phase 12 — Production-ready (priorité haute)
- ⏳ Brancher la newsletter sur un fournisseur réel (Brevo recommandé, FR + gratuit)
- ⏳ Favicon (actuellement aucune)
- ⏳ Liens nav vrais (`#collections`, `#fragrances`, `#shop` ok mais "Boutique" pointe vers la newsletter, ambigu)
- ⏳ Page mentions légales / CGV / cookies (cités dans le footer mais sans page)

### 🟢 Phase 13 — SEO / Performance (priorité moyenne)
- ⏳ Audit Lighthouse (cible : >85 perf, >95 a11y)
- ⏳ Lazy-loading des images embedded base64 (déjà partiellement, à compléter)
- ⏳ Réduire le poids HTML (extraire bougie.png / diffuseur.png / hero-glass-sf.png inutilisés ?)

### 🟢 Phase 14 — Sémantique HTML (priorité basse)
- ⏳ Search `<a>` → `<button>` (action, pas navigation)
- ⏳ `<noscript>` fallback pour révéler les `.reveal` si JS off

### 🟢 Phase 15 — Hygiène projet
- ⏳ Trier `images/` : déplacer les non-utilisées (`bougie.png`, `diffuseur.png`, `hero-glass-sf.png`) hors du repo
- ⏳ `CAPTURE D'ÉCRAN/` à déplacer hors projet (35+ Mo)
- ⏳ Documenter les couleurs accent custom dans CONTEXTE (palette V5)

---

## RÉCAPITULATIF

| Phase | Statut | Progression |
|-------|--------|-------------|
| 1 — Fondations | ✅ | 100% |
| 2 — Animations hero | ✅ | 100% |
| 3 — Compléments visuels | ✅ | 95% |
| 4 — Audit V3 | ✅ | 100% |
| 5 — Refonte V4 | ✅ | 100% |
| 6 — Tweaks system | ✅ | 100% |
| 7 — Identité brand | ✅ | 100% |
| 8 — Hero éditorial | ✅ | 100% |
| 9 — Newsletter | ✅ | 90% (à brancher fournisseur) |
| 10 — Déploiement | ✅ | 100% |
| 11 — Polish mobile | ✅ | 100% |
| 12 — Production-ready | ⏳ | 0% |
| 13 — SEO / Perf | ⏳ | 0% |
| 14 — Sémantique HTML | ⏳ | 0% |
| 15 — Hygiène projet | ⏳ | 0% |

**Progression globale : ~88%**

---

## DESIGN DÉFAUT V5 (à modifier dans `TWEAK_DEFAULTS` + `<body data-*>`)

```js
{
  atmosphere: "aube",
  temperament: "maison",
  or: "maison",
  initiale: "ampersand",
  hauteur: "aeree",
  surface: "lisse",
  accent: "champagne",        // ← changé en V5 (était sage)
  "font-serif": "cardo",
  "font-sans": "manrope",
  corners: "sharp",
  width: "standard",
  motion: "full",
  card: "frame",
  button: "outlined",
  separator: "quill",
  seal: "logo",                // ← rond doré + monogramme WH
  density: "3"
}
```

---

## PROCHAINE ACTION RECOMMANDÉE

**🎯 Brancher la newsletter sur Brevo** (gratuit, FR, RGPD-friendly) :
1. Créer un compte Brevo
2. Récupérer le HTML form fourni par Brevo (avec leur action URL)
3. Remplacer `<form id="newsletterForm">` par leur form, garder le styling actuel
4. Tester avec un email

---

## NOTES DE SUIVI

### 2026-05-20 (après-midi) — Refonte V5
- Tweaks ultra-étendus + persistance + panel masqué
- Hero refait avec image salon haussmannien
- Logo WH intégré (nav + sceau)
- Newsletter remplace CTA
- Anaïs Camizuli fondatrice
- Déployé Vercel + GitHub Pages
- Multiples fixes mobile (écarts, swipe, overrides hauteur)

### 2026-05-20 (matin) — Refonte V4
- Hero : suppression flacon test, composition typo + sceau
- Témoignages : 3 colonnes desktop
- Hover cards unifié
- Écarts sections resserrés

### 2026-05-18 — Audit V3
- 10 chantiers, 9 terminés en ~1h
- HTML lang fr, meta SEO, particules réparées
- 5 JPEG recompressés (14 → 2.5 Mo)

---

**Légende** :
- ✅ Complété et validé en live
- 🟢 Débloqué, prêt à démarrer
- ⏳ En attente / à faire
