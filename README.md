# Wiki analytique de la présidentielle française 2027

Un vault [Obsidian](https://obsidian.md) maintenu par un agent LLM (Claude), conçu pour suivre et analyser la course à l'élection présidentielle française de 2027.

## Principe

L'utilisateur dépose des sources brutes (articles de presse, analyses, clippings web) dans `raw/`. L'agent LLM lit, résume, croise et structure l'information dans un wiki interconnecté sous `wiki/`. Le résultat est un graphe de connaissances navigable dans Obsidian, avec provenance traçable et contradictions explicitement signalées.

**L'humain curate. La machine structure.**

## Structure du vault

```
/
├── CLAUDE.md          # contrat / schéma du wiki — conventions que l'agent suit
├── index.md           # catalogue : chaque page wiki listée avec résumé d'une ligne
├── log.md             # journal chronologique append-only de toute l'activité
├── raw/               # sources brutes (IMMUTABLE — jamais modifiées)
│   └── assets/        # images téléchargées via Obsidian
└── wiki/              # couche LLM — entièrement gérée par l'agent
    ├── overview.md    # synthèse vivante de haut niveau
    ├── sources/       # une page par source ingérée (résumé + takeaways)
    ├── entities/      # personnes, partis, organisations, médias
    ├── concepts/      # idées, mécaniques électorales, thématiques
    └── answers/       # analyses filées (comparaisons, synthèses, scénarios)
```

## Couverture actuelle

| Catégorie  | Pages | Exemples                                                    |
|------------|------:|-------------------------------------------------------------|
| Sources    |    11 | Guardian, HuffPost France, franceinfo, ICI Radio France     |
| Entités    |    67 | Attal, Bardella, Le Pen, Philippe, Mélenchon, Faure, etc.  |
| Concepts   |     7 | bloc central, primaires, sondages T-1 an, calendrier 2027  |
| Réponses   |     1 | « Qui sera le prochain président ? » — synthèse T-1 an     |

## Workflows

### Ingest — ajouter une source

Déposer un fichier dans `raw/` puis demander à l'agent de l'ingérer. Il va :
1. Lire la source et discuter les takeaways avant d'écrire
2. Créer une page source dans `wiki/sources/`
3. Créer ou mettre à jour les pages entités et concepts concernées
4. Mettre à jour `overview.md`, `index.md` et `log.md`

Un ingest touche typiquement 5 à 15 pages.

### Query — poser une question

L'agent synthétise une réponse à partir du wiki existant, avec wikilinks comme citations. Si l'analyse mérite d'être conservée, elle est filée dans `wiki/answers/`.

### Lint — vérifier la cohérence

Détecte les contradictions, pages orphelines, liens cassés, index désynchronisé et lacunes à combler.

## Conventions clés

- **Provenance propre** — les pages wiki citent `wiki/sources/`, jamais `raw/` directement
- **Contradictions explicites** — jamais reconciliées silencieusement, toujours flaggées avec les deux sources
- **Biais source documenté** — chaque page source note l'orientation du média
- **Langue** — français par défaut, anglais si l'utilisateur bascule
- **Nommage** — `kebab-case.md`, pas d'espaces, pas de dates dans les noms de fichiers

## Prérequis

- [Obsidian](https://obsidian.md) (recommandé pour la navigation et le graph view)
- [Claude Code](https://claude.ai/code) comme agent wiki (le schéma est dans `CLAUDE.md`)

## Utilisation

```bash
# Ouvrir le vault dans Obsidian
# Lancer Claude Code dans le répertoire du vault
cd ***
claude

# Exemples de commandes
# "ingest le fichier dans raw/2026-04-20-lemonde-xxx.md"
# "qui sont les candidats déclarés à droite ?"
# "lint le wiki"
```

## Licence

Usage personnel. Les sources brutes dans `raw/` restent la propriété de leurs éditeurs respectifs.
