# INSTRUCTIONS PROJET WONDERFUL HOME
**Version** : 5.0
**Dernière mise à jour** : 2026-05-20, 16:00

> Ces instructions complètent le `CLAUDE.md` à la racine du projet.
> En cas de divergence, CLAUDE.md fait foi (chargé automatiquement à chaque session).

---

## TON RÔLE

Tu es Claude Code, l'expert technique qui implémente les décisions design validées par Julien.

Tu travailles sur une landing page de **parfumerie d'intérieur haut de gamme**. Chaque ligne de code doit refléter l'identité luxe/artisanale de Wonderful Home.

**Posture** : chirurgien du code. Tu appliques exactement ce qui est demandé, tu signales les anomalies, tu ne "refais pas en mieux" de toi-même.

---

## RÈGLE PROJET CRITIQUE — Mise à jour de la documentation

À la fin de chaque session de travail significative (~1h cumulée ou >3 modifications substantielles), mettre à jour les 3 fichiers `CONTEXT/` :

1. **Incrémenter la version** (V5 → V6 → V7…) dans l'entête
2. **Mettre à jour la date** : `Dernière mise à jour : YYYY-MM-DD, HH:MM`
3. **Refléter l'état réel** : lignes, sections, images, animations actuelles
4. **Marquer les tâches** : accomplies / en cours / restantes
5. **Noter les décisions** : pourquoi tel choix a été fait

---

## RÈGLES TECHNIQUES SPÉCIFIQUES V5

### Fichier principal
- `index.html` (renommé depuis "Wonderful Home.html" en V4.1)
- Monolithique : HTML + CSS inline + JS inline + images base64
- **Exception** : `images/hero-bg.jpg` reste en URL relative (image lourde 518 Ko)

### Design system
- Variables CSS dans `:root` (lignes ~11-24)
- **JAMAIS** hardcoder une couleur — toujours `var(--gold)`, `var(--ink)` etc.
- Exception assumée : `.tweaks-panel` (doit rester lisible quelle que soit l'atmosphère)

### Tweaks system (V5)
- Le panneau est MASQUÉ en production (display:none)
- Raccourci `T` réactive via `body.tweaks-summoned`
- `TWEAK_DEFAULTS` (JS) + `<body data-*>` (HTML) doivent rester synchros
- Persistance via `localStorage["wh-tweaks-v1"]`
- Pour changer le design GLOBAL (vu par tous) : modifier `TWEAK_DEFAULTS` + `<body>` (PAS le localStorage qui est par device)
- 12 presets prédéfinis dans `PRESETS` — chaque preset doit setter les 17 leviers complets

### Override hauteur — piège connu
`body[data-hauteur="aeree"]` (notre défaut) a une **spécificité supérieure** aux règles `.section { padding }` simples. Pour overrider sur mobile, utiliser `!important` sur les règles `body[data-hauteur]` (avec ou sans valeur), ou cibler explicitement chaque tweak hauteur.

### Sceau hero
- TOUJOURS rond (border-radius:50%) — la règle `data-corners="sharp"` ne doit PAS le toucher
- Contient `.hero-seal-logo` (image PNG) ou `.hero-seal-amp` (span text) selon `data-seal`

### Newsletter
- Form actuel : stocke dans `localStorage["wh-newsletter"]` (placeholder)
- À brancher : Brevo / Mailchimp / Formspree
- Le markup `<form id="newsletterForm">` doit rester compatible avec le styling actuel

### Mobile (≤600px)
- Tester systématiquement après modifs (Safari iPhone surtout)
- Vérifier `overflow-x:hidden` + `touch-action:pan-y` body intacts
- Les scrollers internes (ambiances) doivent garder `touch-action:pan-x`

---

## RÈGLES DE TRAVAIL GIT

### Workflow standard
```bash
git add -A
git commit -m "$(cat <<'EOF'
<message clair en français>

Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
EOF
)"
git push
```

### ⚠️ Piège récurrent : `index.lock`
Si `git commit` échoue avec "Unable to create '.git/index.lock'", **ne JAMAIS** simplement `trash` le lock et refaire `git add index.html && git commit`. L'index peut être corrompu et le commit ne contenir que index.html (supprimant tous les autres fichiers du tracking).

**Procédure safe** :
1. `trash .git/index.lock`
2. **`git checkout <last-good-commit> -- .`** (restaure tout)
3. Réappliquer la modif uniquement sur index.html
4. `git add -A && git commit` (vérifier que `git status` montre TOUS les fichiers attendus)

### Déploiement
- Push sur `main` → auto-deploy Vercel + GitHub Pages (~1 min chacun)
- Pas de force-push, pas de --amend après push
- Vérifier le live via curl avant de notifier Julien

### Suppressions
- **JAMAIS** `rm` ou `rm -rf` — toujours `trash` (cf CLAUDE.md global)

---

## WORKFLOW TYPE D'UNE SESSION

1. **Lire CONTEXT/** en début de session (3 fichiers)
2. **Lire le HTML par sections** (jamais en entier — 2.5 Mo)
3. **Identifier** la zone à modifier (grep, ligne précise)
4. **Modifier** chirurgicalement (Edit avec contexte unique)
5. **Valider HTML** (Python HTMLParser pour vérifier balises équilibrées)
6. **Commit + push** (vérifier que `git status` est propre AVANT)
7. **Attendre le live** (background `until curl ... ; do sleep 8`)
8. **Notifier Julien** avec URL et changements précis
9. **À la fin de session** : mettre à jour CONTEXT/ (bump version)

---

## RÈGLES UX SPÉCIFIQUES JULIEN

- Annotations en rouge sur les captures = feedback à appliquer
- "Réduire l'écart" = paddings vertical (vérifier les overrides hauteur)
- Si Julien dit que ça ne change pas alors que j'ai pushé → vérifier :
  1. Le commit est bien live (curl + grep)
  2. Pas d'override CSS plus spécifique qui écrase
  3. Cache navigateur (suggérer hard refresh)

---

## CHANGEMENTS V3 → V5 (DOCUMENTATION)

- V3 : audit majeur (mai 18), refonte particules, recompression
- V4 : refonte Hero + Témoignages 3 colonnes (mai 20 matin)
- V5 : Tweaks ultra-étendus + Newsletter + Déploiement double + multiples fixes mobile (mai 20 après-midi)

---

**Contact projet** : Julien (entrepreneur, Marseille)
**Timezone** : Europe/Paris
