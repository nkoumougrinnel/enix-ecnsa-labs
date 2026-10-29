# Créer un document professionnel avec les modèles ECNSA

Ces modèles servent à produire des devoirs clairs et professionnels sans
repartir d’une page vide. Ils partagent la même identité visuelle et un même
fil de rédaction : **question ou objectif → observation → preuve → explication
→ action ou conclusion**.

Un document professionnel n’est pas un document rempli de tableaux et de
termes complexes. Il permet au lecteur de comprendre le sujet, de vérifier les
faits et de suivre le raisonnement, même s’il débute en réseau ou en sécurité.

## Quel modèle choisir ?

| Modèle | À utiliser pour… | Organisation conseillée |
|---|---|---|
| `template-mini-evaluation.tex` | Répondre à quelques questions pratiques | Réponse directe, démarche, preuve utile, interprétation, synthèse |
| `template-etude-de-cas.tex` | Analyser une situation et proposer des priorités | Contexte, périmètre, constats, risques, plan d’action, conclusion |
| `template-exercice-individuel.tex` | Traiter un exercice argumenté ou une consigne de cours | Méthode, réponses justifiées, mesures, conclusion personnelle |
| `template-livrable.tex` | Remettre un rapport de laboratoire ou un document de référence | Synthèse, périmètre, résultats, preuves, recommandations, limites, annexes |

Pour un compte rendu de laboratoire comme ceux des chapitres 1 et 2, le modèle
**Livrable** est généralement le plus adapté. Pour un devoir court construit
autour de scénarios de risque, choisir **Étude de cas**. Supprimer les parties
qui ne servent pas au sujet plutôt que de conserver des pages vides.

## Une présentation cohérente, quatre mises en page

Les quatre documents partagent la palette bleu nuit/turquoise, la police, les
titres et les légendes. La page et la densité s’adaptent toutefois à
l’exercice :

| Profil | Marges gauche/droite | Haut/bas | Usage |
|---|---:|---:|---|
| Mini-évaluation | 1,8 cm | 2,1 / 1,8 cm | Réponse courte ; bandeau de titre sur la première page, sans garde séparée |
| Étude de cas | 2,0 cm | 2,3 / 2,1 cm | Analyse, risques et actions |
| Exercice individuel | 2,2 cm | 2,4 / 2,2 cm | Place pour détailler une démarche et argumenter |
| Livrable | 2,2 cm | 2,6 / 2,5 cm | Rapport long avec tableaux techniques, garde, sommaire et annexes |

Les marges réservent l’espace du numéro de page en bas. Garder les réglages du
profil : ne modifier `geometry` que si une consigne de remise l’exige.
Ces valeurs sont des choix de présentation, pas une exigence officielle ENIX.

La garde reprend le code de formation et le chapitre. Remplir ces informations
à chaque devoir rend les PDF identifiables et donne à voir la progression d’un
chapitre au suivant. Le lien du dépôt Git est affiché sur la garde lorsque
`\liengit` est renseigné. Les modifier avant `\begin{document}` :

```latex
\contextedevoir{ACX401.1 — ECNSA}
   {Chapitre 3 — Sécurité des couches 1 et 2}
```

Pour une mini-évaluation, utiliser le bandeau compact plutôt qu’une garde
séparée, afin de réserver la place aux réponses.

## Démarrer en cinq étapes

1. Copier le fichier `.tex` correspondant dans le dossier du devoir, par exemple
   `chapitre-03/rapport/rapport.tex`.
2. Remplacer les champs entre crochets, comme `[Titre du livrable]`, et mettre à
   jour le type, les auteurs, le sujet et la date dans `\fairepagegarde`.
3. Écrire d’abord le contenu dans l’ordre logique : contexte, méthode, résultats,
   preuves, interprétation et suites. Supprimer les exemples qui ne s’appliquent pas.
4. Placer les images dans un dossier `images/` ou `captures/` au même niveau
   que le document. Utiliser des noms explicites et masquer les secrets.
5. Compiler deux fois, relire le PDF et vérifier sommaire, figures, tableaux,
   renvois et marges.

Les modèles trouvent automatiquement le dossier `templates/` depuis les
emplacements courants du dépôt. Compile le document depuis son dossier pour
que les chemins relatifs des images, comme `images/preuve-1.png`, fonctionnent.

## Comment expliquer un constat simplement

Suivre ces questions pour chaque résultat important :

1. **Qu’est-ce que j’ai cherché ?** Décrire l’objectif ou la question.
2. **Qu’ai-je fait ?** Nommer la commande, le filtre, l’outil ou la source.
3. **Qu’ai-je observé ?** Donner le fait précis, sans supposer sa cause.
4. **Quelle preuve permet de le vérifier ?** Citer une capture, un résultat ou
   un extrait lisible.
5. **Qu’est-ce que cela signifie ?** Traduire l’observation en langage simple
   et expliquer pourquoi elle compte.
6. **Que faut-il faire ensuite ?** Proposer une action proportionnée et une
   façon de vérifier qu’elle fonctionne.

Par exemple, une capture seule ne suffit pas : la légende indique ce qu’elle
montre, puis le texte explique le constat et sa conséquence. Distinguer toujours
un fait observé d’un risque hypothétique ou d’une information qui reste à vérifier.

## Repères de mise en forme

- **Titres et couleurs :** bleu nuit pour la structure, turquoise pour guider la
  lecture. Les styles sont partagés ; ne les reformater pas devoir par devoir.
- **Encadrés :** `blocpedagogique` attire l’attention sur une réponse ou une
  méthode ; `blocattention` signale une précaution importante. À utiliser avec
  parcimonie.
- **Figures :** chaque capture doit être recadrée, lisible, référencée et
  accompagnée d’une légende qui décrit la preuve.
- **Tableaux :** garder peu de colonnes, avec des en-têtes explicites. Déplacer
  le détail volumineux en annexe plutôt que de réduire tout le texte.
- **Langage :** développer les sigles à leur première occurrence ; préférer
  une explication courte à une accumulation de jargon.
- **Éthique et sécurité :** ne jamais publier mots de passe, clés, jetons,
  données personnelles ni secrets contenus dans les captures ou configurations.

Les commandes `\fairepagegarde{...}`, `\filconducteur`, `blocpedagogique` et
`blocattention` sont fournies par le préambule commun. Les modèles les utilisent
déjà : pour un usage normal, il suffit de remplacer leur contenu d’exemple.

### Captures et filtres reproductibles

`\captureanalyse{label}{fichier}{filtre ou commande}{légende}` crée une figure
et affiche sous l’image le nom du fichier ainsi que le filtre ou la commande.
Le label sert aux renvois dans le texte (`\ref{fig:preuve-1}`).
`\methodeanalyse{Intitulé}{filtre ou commande}` met en évidence une méthode
sans capture. Les exemples sont à adapter au paquet réellement analysé.

Pour chaque preuve utile, noter le fichier source et, si nécessaire, le numéro
de paquet ou l’horodatage ; recopier le filtre Wireshark exact ou la commande ;
puis expliquer ce qu’on observe, ce que cela prouve et ce que cela ne permet pas
d’affirmer. Un filtre tel que `dns.qry.name == "exemple.test"` est un filtre
d’affichage Wireshark, pas une preuve en soi. Toujours retirer des sources et
images les mots de passe, clés, jetons et données personnelles.

### Tableaux et données variables

- Pour un tableau qui tient sur une page, utiliser `tabularx` et des colonnes
   `X` pour que les textes s’adaptent à la largeur.
- Placer `\tableauECNSA` juste avant un `tabularx` et `\fintableauECNSA`
   juste après pour activer puis arrêter les lignes alternées. Dans le tableau,
   garder `\toprule`, une ligne d’en-tête en gras, `\midrule` et `\bottomrule`.
- Pour des données qui débordent sur plusieurs pages, utiliser `longtable` et
   répéter l’en-tête. Éviter de réduire l’ensemble en `\scriptsize` : supprimer
   les colonnes inutiles, faire un résumé dans le corps et déplacer le détail en
   annexe.
- Si un tableau est trop large, le réorganiser ou le passer ponctuellement en
   paysage. Ne pas réduire les marges de tout le rapport pour sauver un seul tableau.
- Les profils règlent déjà la hauteur des lignes ; éviter les traits verticaux et
   les longues phrases dans des colonnes étroites.

## Repères publics du parcours ECNSA

Les pages publiques de l’Académie décrivent un cursus pratique centré sur le
réseau fictif CamTrust Bank. Pour le chapitre 1, elles énumèrent objectifs,
support, démonstration guidée, TP/lab, exercice individuel, étude de cas, quiz,
mini-évaluation, livrable, auto-évaluation et validation de compétence. Le
programme publié couvre 17 chapitres, des fondations TCP/IP et du durcissement
jusqu’à la segmentation, aux services, à la détection, à la réponse à incident,
à l’audit et au projet final Red vs Blue.

La page de certification décrit séparément un rapport de stage de 30 à 50 pages
structuré autour du contexte, de l’architecture, de l’analyse technique, des
preuves et des recommandations. **Cette longueur concerne le rapport de stage**,
pas automatiquement les quatre devoirs de chapitre. Les couleurs, marges et
structures de ces modèles sont des conventions de présentation proposées ici,
pas des consignes officielles ENIX. En cas de conflit, la consigne de l’enseignant
prévaut.

Sources officielles consultées le 29 octobre 2026 :

- [Certification ECNSA — Académie ENIX](https://academie-enix.org/certifications/enix-certified-network-security-associate/)
- [Module ACX401.1 — Sécurité des réseaux pour l’entreprise](https://academie-enix.org/modules/securite-des-reseaux-pour-lentreprise/)
- [Kung Fu Labs — Académie ENIX](https://academie-enix.org/kung-fu-labs/)

## Compiler et contrôler

Depuis le dossier contenant le rapport :

```bash
pdflatex rapport.tex
pdflatex rapport.tex
```

La seconde compilation met à jour le sommaire et les références. Avant de
remettre le document, vérifier :

- le PDF compile sans erreur et le sommaire est à jour ;
- le résumé annonce les résultats et les priorités, pas seulement le sujet ;
- chaque constat important s’appuie sur une preuve et une explication ;
- les recommandations répondent aux constats et ont un résultat vérifiable ;
- les images et tableaux sont lisibles, cités et correctement légendés ;
- les limites et les éléments qui restent à vérifier sont indiqués ;
- aucune donnée sensible n’est visible.

## Fichiers

- `preamble-commun.tex` : mise en page, palette, page de garde et encadrés communs.
- `preamble-[type].tex` : petite configuration propre à chaque format.
- `template-[type].tex` : structure de départ et exemples de rédaction.
