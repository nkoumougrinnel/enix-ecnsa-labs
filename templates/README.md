# Templates LaTeX — ECNSA

Modèles prêts à l'usage pour les quatre types de documents produits
pendant le parcours ECNSA. Copier le fichier `.tex` voulu dans le
dossier du devoir, remplacer les champs `[entre crochets]` et compiler.

---

## Quel modèle choisir ?

| Modèle | Usage | Limite indicative |
|---|---|---:|
| `template-mini-evaluation.tex` | Répondre à quelques questions pratiques | ~5 pages |
| `template-etude-de-cas.tex` | Analyser une situation et proposer des priorités | ~2 pages |
| `template-exercice-individuel.tex` | Traiter un exercice argumenté ou une consigne de cours | ~5 pages |
| `template-livrable.tex` | Rapport de laboratoire complet, sans limite de pages | — |

---

## Structure des fichiers

```
templates/
├── preamble-commun.tex              # Packages partagés par tous les modèles
├── preamble-mini-evaluation.tex     # Marges et espacement mini-éval (2,2 cm)
├── preamble-etude-de-cas.tex        # Marges et espacement étude de cas (2 cm)
├── preamble-exercice-individuel.tex # Marges compactes exercice individuel (1,7 cm)
├── preamble-livrable.tex            # Marges, fancyhdr et hyperref livrable (2,2 cm)
├── template-mini-evaluation.tex     # Modèle mini-évaluation
├── template-etude-de-cas.tex        # Modèle étude de cas
├── template-exercice-individuel.tex # Modèle exercice individuel
└── template-livrable.tex            # Modèle livrable / rapport
```

Les préambules ne sont pas à modifier pour un usage normal.
Les réglages spécifiques à un devoir se font directement dans le fichier `.tex`.

---

## Démarrer en quatre étapes

1. **Copier** le fichier `.tex` dans le dossier du devoir
   (ex. `chapitre-03/mini-evaluation/mini-evaluation.tex`).
2. **Remplir** tous les champs `[entre crochets]` : titre, auteur, classe, date.
3. **Rédiger** le contenu dans les sections existantes ; supprimer ou dupliquer
   les blocs selon le sujet.
4. **Compiler** avec `pdflatex` depuis le dossier du devoir.

> Pour un livrable avec table des matières, compiler **deux fois** afin que
> le sommaire soit à jour.

---

## Détail par modèle

### Mini-évaluation

- Police 11 pt, marges 2,2 cm, `\pagestyle{plain}`.
- Titre centré via `\maketitle`, numéro de page centré en bas.
- Structure : sections numérotées + listes `itemize` avec points en gras.

### Étude de cas

- Police 11 pt, marges 2 cm, `\pagestyle{plain}`.
- Sections numérotées manuellement (`\section*{1. …}`) pour coller à l'original.
- Structure : classement des constats (tableau) → scénarios de risques → plan d'action (tableau).

### Exercice individuel

- Police **10 pt**, marges 1,7 cm (le plus compact), `\pagestyle{plain}`.
- Structure : objet et périmètre → obligations/constats → mesures → tableau de synthèse.

### Livrable

- Police 11 pt, marges 2,2 cm.
- **Page de garde** intégrée directement dans le document (logo optionnel,
  titre, auteurs, date centrés verticalement).
- **`fancyhdr` actif** : `[Nom du scénario / client]` à gauche, `ECNSA` à droite,
  numéro de page centré en bas. La page de garde elle-même n'a pas d'en-tête.
- **`hyperref` actif** : liens PDF cliquables (URLs, références internes).
- **`longtable`** disponible pour les grands inventaires multi-pages.
- `\tableofcontents` fourni mais commenté — décommenter si > 6-7 sections
  (nécessite une deuxième passe de compilation).
- Structure : résumé → périmètre → constats + preuves → plan d'action → annexes.

---

## Conventions de rédaction

- **Tableaux :** `tabularx` + `booktabs` (`\toprule`, `\midrule`, `\bottomrule`).
  Pas de traits verticaux, pas de `\hline`.
- **Captures :** placer dans `images/` au même niveau que le `.tex`.
  Un cadre de substitution s'affiche si l'image est absente (pas d'erreur de compilation).
- **Légendes :** chaque figure et tableau doit avoir une `\caption` qui décrit
  ce que l'image ou le tableau montre, pas juste son titre.
- **Données sensibles :** ne jamais laisser de mots de passe, clés ou données
  personnelles dans les captures ou configurations publiées.

---

## Compiler

```bash
# Depuis le dossier du devoir :
pdflatex livrable.tex

# Pour le livrable avec table des matières (deux passes) :
pdflatex livrable.tex && pdflatex livrable.tex
```

Les modèles trouvent automatiquement le dossier `templates/` depuis les
emplacements `../../templates/`, `../templates/` ou `templates/` — ils
fonctionnent depuis n'importe quel sous-dossier du dépôt.

---

## Checklist avant remise

- [ ] Le PDF compile sans erreur.
- [ ] Tous les champs `[entre crochets]` ont été remplacés.
- [ ] Chaque constat s'appuie sur une preuve (capture, résultat de commande).
- [ ] Les images sont lisibles et correctement légendées.
- [ ] La table des matières est à jour (si présente).
- [ ] Aucune donnée sensible n'est visible dans le PDF.
