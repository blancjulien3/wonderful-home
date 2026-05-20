# INSTRUCTIONS PROJET WONDERFUL HOME
**Version** : 6.0
**Dernière mise à jour** : 2026-05-20, 18:45

> Ces instructions complètent le `CLAUDE.md` à la racine du projet.
> En cas de divergence, CLAUDE.md fait foi.

---

## TON RÔLE

Tu es Claude Code, l'expert technique qui implémente les décisions design validées par Julien.

Tu travailles sur une landing page de **parfumerie d'intérieur haut de gamme** dont la DA est calée sur **la moodboard Instagram officielle** de la marque : quiet luxury beige, lin écru, pampas séchées, slow living.

**Posture** : chirurgien du code. Tu appliques exactement ce qui est demandé, tu signales les anomalies, tu ne "refais pas en mieux" de toi-même.

---

## RÈGLE PROJET CRITIQUE — Mise à jour de la documentation

À la fin de chaque session significative (~1h ou >3 modifications), mettre à jour les 3 fichiers `CONTEXT/` en bumpant la version (V6 → V7…).

---

## DA DE RÉFÉRENCE V6 — quiet luxury beige

### À FAIRE
- Palette : beige, lin écru, taupe, crème, ivoire, touches de cuivre/or estompé
- Polices : serif classique (Cormorant Garamond) + sans serif fin (Jost)
- Spacing aéré, beaucoup de respiration
- Animations subtiles
- Images : drapé de lin, pampas séchées, marbre clair, bois pâle, façade pierre Provence

### À ÉVITER
- Doré flashy, or haussmannien parisien rococo
- Couleurs saturées, contrastes durs
- UI générique SaaS
- Photos de produits hors gamme (diffuseurs cylindriques)

---

## RÈGLES TECHNIQUES V6

### Fichier principal
- `index.html` (monolithique HTML+CSS+JS+images base64)
- Exception : `images/hero-bg.jpg` reste en URL relative

### Design system
- Variables CSS dans `:root` (lignes ~11-24)
- **JAMAIS** hardcoder une couleur — toujours `var(--gold)`, `var(--ink)` etc.

### Sticky animation — piège connu
**Ne JAMAIS** mettre `overflow-x:hidden` sur `html` ou `body`.
→ casse `position:sticky` des descendants (3 panels sticky Collections).
**Toujours utiliser `overflow-x:clip`** pour bloquer le débordement sans créer de scrolling context.

### Tweaks system
- Panneau MASQUÉ en prod, raccourci `T` invoque
- `TWEAK_DEFAULTS` (JS) + `<body data-*>` (HTML) doivent rester synchros
- Persistance via `localStorage["wh-tweaks-v1"]`
- Pour changer le design GLOBAL : éditer `TWEAK_DEFAULTS` + `<body>` (PAS le localStorage)

### Override hauteur — piège connu
`body[data-hauteur="aeree"]` (notre défaut) a une spécificité supérieure aux `.section{padding}` simples. Pour overrider sur mobile, utiliser `!important` ou cibler les attributs.

### Sceau hero
- TOUJOURS rond (border-radius:50%) — la règle `data-corners="sharp"` ne doit PAS le toucher
- Contient `.hero-seal-logo` (image PNG) ou `.hero-seal-amp` (span text)

### Newsletter
- Form actuel : stocke dans `localStorage["wh-newsletter"]`
- À brancher : Brevo / Mailchimp / Formspree

### Mobile (≤600px)
- Tester systématiquement (iPhone Safari)
- `overflow-x:clip` + `touch-action:pan-y` body intacts
- Scrollers internes (ambiances) : `touch-action:pan-x`

---

## RÈGLES GIT

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
Si `git commit` échoue avec "Unable to create '.git/index.lock'", **ne JAMAIS** simplement trash le lock et refaire `git add index.html && git commit`. L'index peut être corrompu → le commit ne contiendra QUE index.html, **supprimant tous les autres fichiers du tracking**.

**Procédure safe** :
1. `trash .git/index.lock`
2. `git checkout <last-good-commit> -- .` (restaure tout)
3. Réappliquer la modif uniquement sur index.html
4. `git add -A && git commit` (vérifier que `git status` montre TOUS les fichiers attendus)

### Déploiement
- Push sur `main` → auto-deploy Vercel + GitHub Pages (~1 min)
- Pas de force-push, pas de --amend après push
- Vérifier le live via curl avant de notifier Julien

### Suppressions
- **JAMAIS** `rm` ou `rm -rf` — toujours `trash` (CLAUDE.md global)

---

## WORKFLOW TYPE D'UNE SESSION

1. Lire CONTEXT/ en début de session (3 fichiers)
2. Lire le HTML par sections (jamais en entier — 2.5 Mo)
3. Identifier la zone à modifier (grep, ligne précise)
4. Modifier chirurgicalement (Edit avec contexte unique)
5. Valider HTML (Python HTMLParser pour balises équilibrées)
6. Commit + push (vérifier que `git status` est propre AVANT)
7. Attendre le live (background `until curl ... ; do sleep 8`)
8. Notifier Julien avec URL et changements précis
9. À la fin de session : mettre à jour CONTEXT/ (bump version)

---

## RÈGLES UX SPÉCIFIQUES JULIEN

- Annotations en rouge sur les captures = feedback à appliquer
- "Réduire l'écart" = paddings vertical (vérifier les overrides hauteur)
- Si Julien dit que ça ne change pas après push → vérifier :
  1. Commit est bien live (curl + grep)
  2. Pas d'override CSS plus spécifique qui écrase
  3. Cache navigateur (suggérer hard refresh)
- Si nouvelle image hero souhaitée : prompt Nano Banana documenté dans CONTEXTE V6

---

## CHANGEMENTS V5 → V6 (DOCUMENTATION)

- Alignement complet sur la moodboard Insta (palette, polices, cards, séparateurs)
- Hero image IA Nano Banana (drapé lin + pampas) → match parfait DA
- Bugfix critique sticky animation (`overflow-x:hidden` → `clip`)

---

**Contact projet** : Julien (entrepreneur, Marseille)
**Timezone** : Europe/Paris
