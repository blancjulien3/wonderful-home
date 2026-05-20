# CHECKLIST PROJET WONDERFUL HOME
**Dernière mise à jour** : 2026-05-20, 12:30
**Version** : 4.0 (refonte Hero + Témoignages 3 colonnes + polish hover)

---

## ÉTAT ACTUEL DU PROJET

**Fichier** : Wonderful Home.html
**Taille** : 2.40 Mo (V3 : 2.46 Mo)
**Lignes** : ~1799 (V3 : ~1880 ; −80 lignes par suppression code mort)
**Images intégrées** : 11 base64 (V3 : 12 ; flacon hero supprimé)
**Système de tweaks** : ✅ Actif (6 leviers)

---

## PHASE 1 — FONDATIONS ✅ TERMINÉE

- ✅ 3 PNG produits intégrés (musc, pink, wood)
- ✅ Système de tweaks JS fonctionnel
- ✅ Structure HTML stable
- ✅ Design system cohérent

---

## PHASE 2 — ANIMATIONS HERO ✅ TERMINÉE (refondue V4)

- ❌ V3 : Intro cinématique flacon (`bottleEntrance`, 3.2s cubic-bezier) → **retirée en V4**
- ✅ 8 particules dorées (`pulse`)
- ✅ Drip animation scroll-cue
- ✅ Marquee infinite scroll
- ✅ **V4** : Animation `sealGlow` 6s sur le sceau central
- ✅ **V4** : Scroll fade léger sur `.hero-mark`

---

## PHASE 3 — COMPLÉMENTS VISUELS ✅ TERMINÉE

- ✅ 4 ambiances JPEG intégrées + recompression
- ✅ `grasse.jpg` intégré dans Story + recompression
- ⏭️  `bougie.png` / `diffuseur.png` — réservés, pas utilisés

---

## PHASE 4 — AUDIT & POLISH ✅ TERMINÉE (V3)

- ✅ `<html lang>` corrigé en `fr`
- ✅ Meta description + OG + Twitter Card
- ✅ Sélecteurs particules cassés réparés
- ✅ 5 JPEG recompressés (14.27 → 2.46 Mo)
- ✅ Breakpoint 600px + `prefers-reduced-motion`
- ✅ Nettoyage projet (scripts Python, `.DS_Store`)

---

## PHASE 5 — REFONTE V4 ✅ TERMINÉE (2026-05-20)

### Hero — composition éditoriale
- ✅ Suppression `<img id="hero-bottle">` (flacon test)
- ✅ Suppression CSS `.bottle-stage` + animation `bottleEntrance` (code mort)
- ✅ Suppression JS parallax `.bottle-stage` (code mort)
- ✅ Création `.hero-mark` (rule + sceau circulaire 64px + rule)
- ✅ Création `.hero-signature` (Fondée à Grasse · 1998 · Parfumerie d'intérieur)
- ✅ Animation `sealGlow` (lueur dorée respirante)
- ✅ Re-centrage vertical du `.hero .center`
- ✅ Scroll fade léger sur `.hero-mark` (préserve reveal à scroll=0)
- ✅ Responsive 600px adapté

### Témoignages — grid 3 colonnes desktop
- ✅ Layout `grid` au lieu de `flex column`
- ✅ Hairlines verticales entre les 3 colonnes (gradient gold)
- ✅ Suppression des `<span class="divider">` losanges
- ✅ Quote font-size adapté au format colonne (clamp 18-22px)
- ✅ `.mark` ajouté aux 3 témoignages (cohérence visuelle)
- ✅ Responsive ≤960px : 1 colonne + hairlines horizontales

### Polish
- ✅ Hover cards produits unifié (img + swatch + box-shadow)
- ✅ Alt orphelin "Linge Frais" → "Pink Love" corrigé

---

## PHASE 6 — POLISH RESTANT (avant présentation)

### À vérifier visuellement (test navigateur)
- ⏳ Hero : balance visuelle après suppression du flacon (composition harmonieuse ?)
- ⏳ Témoignages : 3 colonnes lisibles sur 1440px, 1280px, 1024px
- ⏳ Témoignages : retour propre en 1 colonne sous 960px
- ⏳ Tweaks system : tester les 6 leviers avec la nouvelle composition Hero
- ⏳ Hover cards produits : transition fluide image+swatch

### Sémantique / SEO (optionnel pour démo)
- ⏳ `<form>` autour newsletter + `<label>` + `type="email"`
- ⏳ Search `<a>` → `<button>`
- ⏳ Favicon

### Hygiène projet
- ⏳ Supprimer `Wonderful Home.html.bak` (14 Mo) après validation V4
- ⏳ Déplacer `CAPTURE D'ÉCRAN/` (21 Mo) hors projet

---

## PHASE 7 — DÉPLOIEMENT (À FAIRE)

- ⏳ Push GitHub (skill `github-init`)
- ⏳ Déploiement Vercel
- ⏳ Test URL prod multi-devices
- ⏳ Vérification OG tags

---

## RÉCAPITULATIF

| Phase | Statut | Progression |
|-------|--------|-------------|
| 1 — Fondations | ✅ | 100% |
| 2 — Animations hero | ✅ refondu V4 | 100% |
| 3 — Compléments visuels | ✅ | 95% |
| 4 — Audit & polish V3 | ✅ | 100% |
| 5 — Refonte V4 | ✅ | 100% |
| 6 — Polish restant (présentation) | ⏳ | 0% |
| 7 — Déploiement | ⏳ | 0% |

**Progression globale : ~85%**

---

## PROCHAINE ACTION

**🎯 Présenter le site** — la refonte V4 est en place :
- Hero typo pure avec sceau éditorial
- Témoignages en 3 colonnes
- Hover cards unifié

Si feedback visuel demande ajustements → Phase 6
Sinon → Phase 7 (déploiement)

---

## NOTES DE SUIVI

### 2026-05-20, 12:30 — Refonte V4
- Session demandée pour finaliser le site avant présentation
- Audit complet effectué (1)
- Hero refait : flacon supprimé, sceau éditorial créé (2)
- Témoignages restructurés en 3 colonnes desktop (3)
- Polish hover cards + corrections orphelines (4)
- Code mort nettoyé (~50 lignes CSS + 1 bloc JS)
- Docs CONTEXT bumpées V3 → V4

### 2026-05-18, 14:50 — Audit V3
- Audit complet, 10 chantiers, 9 terminés en ~1h
- Section Journal créée puis supprimée à la demande

### 2026-05-15, 13:45 — V2
- Synchronisation phases 2 et 3 (déjà 95% faites)

---

**Légende** :
- ✅ Complété et validé
- 🟢 Débloqué, prêt à démarrer
- ⏳ En attente / à faire
- ⏭️  Reporté volontairement
