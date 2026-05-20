# CHECKLIST PROJET WONDERFUL HOME
**Dernière mise à jour** : 2026-05-20, 18:45
**Version** : 6.0 (Alignement DA Insta + hero IA + fix sticky)

---

## ÉTAT ACTUEL

- `index.html` ~2.54 Mo · ~2530 lignes
- Live : https://wonderful-home.vercel.app/ + https://blancjulien3.github.io/wonderful-home/
- Repo : github.com/blancjulien3/wonderful-home (PUBLIC)
- Auto-deploy actif

---

## PHASES TERMINÉES

✅ Phase 1-11 (cf V5 — fondations → polish mobile)
✅ **Phase 12 — Alignement DA Insta (V6)** :
   - Diagnostic moodboard, palette beige naturel
   - Accent Lin (au lieu de Champagne)
   - Or voilé
   - Cormorant + Jost (titres + corps)
   - Cards sans cadre, séparateurs ligne
   - Image hero IA générée Nano Banana (drapé lin + pampas)
   - Bugfix sticky animation (overflow-x:clip)

---

## CE QUI RESTE À FAIRE

### 🟢 Phase 13 — Production-ready (priorité haute)
- ⏳ Brancher la newsletter sur un fournisseur (Brevo recommandé)
- ⏳ Favicon
- ⏳ Liens nav vrais (Boutique pointe vers la newsletter actuellement, à clarifier)
- ⏳ Pages mentions légales / CGV / cookies (footer cite ces liens mais sans page cible)

### 🟢 Phase 14 — Optimisations
- ⏳ Audit Lighthouse (cible perf >85, a11y >95)
- ⏳ Lazy-loading systématique des images base64
- ⏳ Réduire le poids HTML : extraire les images base64 non essentielles vers fichiers
- ⏳ Trier `images/` : supprimer bougie.png, diffuseur.png, hero-glass-sf.png si vraiment inutilisés

### 🟢 Phase 15 — Sémantique
- ⏳ Search `<a>` → `<button>`
- ⏳ `<noscript>` fallback pour les `.reveal`

### 🟢 Phase 16 — Hygiène projet
- ⏳ Déplacer `CAPTURE D'ÉCRAN/` hors projet (35+ Mo)
- ⏳ Documenter le nouveau prompt Nano Banana en cas de besoin

---

## RÉCAPITULATIF

| Phase | Statut | Progression |
|-------|--------|-------------|
| 1-11 (V1→V5) | ✅ | 100% |
| 12 — DA Insta (V6) | ✅ | 100% |
| 13 — Production-ready | ⏳ | 0% (4 items) |
| 14 — Optimisations | ⏳ | 0% |
| 15 — Sémantique HTML | ⏳ | 0% |
| 16 — Hygiène projet | ⏳ | 0% |

**Progression globale : ~90%**

---

## DESIGN DÉFAUT V6 (référence rapide)

```js
const TWEAK_DEFAULTS = {
  atmosphere: "aube",
  temperament: "maison",
  or: "voile",                    // ← V6
  initiale: "ampersand",
  hauteur: "aeree",
  surface: "lisse",
  accent: "lin",                  // ← V6 (était champagne)
  "font-serif": "cormorant",      // ← V6 (était cardo)
  "font-sans": "jost",            // ← V6 (était manrope)
  corners: "sharp",
  width: "standard",
  motion: "full",
  card: "borderless",             // ← V6 (était frame)
  button: "outlined",
  separator: "line",              // ← V6 (était quill)
  seal: "logo",
  density: "3"
};
```

---

## PROCHAINE ACTION

**🎯 Validation visuelle finale** sur ordi + iPhone avec la DA V6.

Si tout OK → attaquer Phase 13 (Brevo newsletter + favicon + mentions légales).

Si retouches : signaler avec captures annotées.

---

## NOTES DE SUIVI

### 2026-05-20 (soir) — V6 alignement DA
- Diagnostic moodboard Insta : quiet luxury beige
- 7 ajustements DA (palette + polices + cards + séparateurs)
- Hero image générée IA (Nano Banana sur prompt détaillé)
- Bugfix sticky : `overflow-x:hidden` → `clip` (cassait position:sticky)

### 2026-05-20 (après-midi) — V5 Tweaks étendus + Newsletter
- 17 leviers + 12 presets + persistance localStorage
- Section CTA → Newsletter
- Logo WH dans nav + sceau
- Fondatrice Anaïs Camizuli
- Multiples fixes mobile

### 2026-05-20 (matin) — V4 Refonte initiale
- Hero typo + sceau (suppression flacon test)
- Témoignages 3 colonnes
- Polish hover cards

### 2026-05-18 — V3 Audit
- Meta SEO, particules réparées, recompression JPEG

---

**Légende** :
- ✅ Complété en live
- ⏳ À faire
- 🟢 Débloqué, prêt à démarrer
