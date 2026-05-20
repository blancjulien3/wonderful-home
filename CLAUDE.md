# Wonderful Home — Instructions projet

## Identité

Landing page de parfumerie haut de gamme française (Wonderful Home, créée à Grasse en 1998).
Fichier principal : `Wonderful Home.html` (monolithique : HTML + CSS + JS + images base64).
Ton : luxe discret, intemporel, sensoriel.

## Règle critique — Mise à jour de la documentation

**À la fin de chaque session de travail significative (~1h cumulée ou plus de 3 modifications substantielles), tu dois IMPÉRATIVEMENT mettre à jour les fichiers `CONTEXT/` :**

- `CONTEXT/CONTEXTE_WONDERFUL_HOME_V*.md` — état du projet, design system, phases
- `CONTEXT/CHECKLIST_WONDERFUL_HOME_V*.md` — progression réelle des tâches
- `CONTEXT/INSTRUCTIONS_WONDERFUL_HOME_V*.md` — workflow et règles d'intervention

Procédure :

1. Au début de la session, lis les 3 docs CONTEXT pour reprendre l'état.
2. Pendant le travail, garde mentalement la liste des changements effectués.
3. Avant de terminer la session (ou après ~1h cumulée), **mets à jour les docs** :
   - Incrémenter le numéro de version (`V2` → `V3` → `V4`…) dans l'entête
   - Mettre à jour la date `Dernière mise à jour : YYYY-MM-DD, HH:MM`
   - Refléter exactement l'état réel du fichier HTML (lignes, sections, images, animations)
   - Marquer les tâches accomplies, en cours, restantes
   - Noter les décisions prises et leur justification

Si tu termines une session sans avoir mis à jour la doc, tu commences la session suivante en aveugle. Cette règle existe pour permettre la continuité entre conversations.

## Règles techniques (héritées de INSTRUCTIONS V2, toujours en vigueur)

- **Principe de chirurgie** : modifier uniquement ce qui est explicitement demandé, localiser précisément avant éditer, valider après chaque modification.
- **Variables CSS du design system** : ne jamais hardcoder une couleur (`#C9A84C`) — toujours `var(--gold)`. Exception assumée : `.tweaks-panel` (lignes ~944-1024) reste hardcodé pour rester lisible quelle que soit l'atmosphère.
- **Images** : compresser AVANT base64 (sips ou équivalent). Lifestyle JPEG < 250 Ko, produit PNG < 100 Ko. Toujours `alt` renseigné, `loading="lazy"` sauf hero.
- **`image-slot.js`** : a été supprimé du dépôt (n'était jamais chargé). Ne pas le recréer.
- **Suppression de fichiers** : utiliser `trash` (jamais `rm`), conformément au CLAUDE.md global de l'utilisateur.

## État du fichier après audit (18 mai 2026)

- Taille : 2.46 MB (avant audit : 14.27 MB, −83 %)
- 12 images base64 (avant : 15 ; 3 orphelines supprimées)
- 5 JPEG lifestyle recompressés (qualité 75, max 1600 px)
- Particules dorées : 8 fonctionnelles (avant : 4 visibles seulement)
- Section Journal remplie (3 cartes éditoriales)
- Breakpoints responsives : 960px + 600px
- `prefers-reduced-motion` actif
- Meta SEO + Open Graph présents
- `<html lang="fr">`

## Workflow type

1. **Lire CONTEXT/** au début de la session (3 fichiers).
2. **Lire le HTML** par sections (jamais en entier — fichier de 2.5 MB).
3. **Identifier** la zone à modifier (grep, ligne précise).
4. **Modifier** chirurgicalement avec Edit.
5. **Valider** structure HTML (balises équilibrées, fichier ouvert sans erreur).
6. **Documenter** : à la fin de session, mettre à jour CONTEXT/.

## Tâches restantes connues (mai 2026)

Voir `CONTEXT/CHECKLIST_WONDERFUL_HOME_V3.md` pour la liste à jour.
