# Parcours ECNSA — Laboratoires CamTrust Bank

Ce dépôt rassemble mes travaux pratiques réalisés pendant la formation
ECNSA (ENIX Certified Network Security Associate) de l’Académie ENIX.

J’y conserve mes configurations, mes captures réseau et mes rapports
pour suivre ma progression et retrouver les étapes de chaque lab.

## Le parcours

Les travaux s’appuient sur le réseau fictif de CamTrust Bank.
Au fil des chapitres, l’infrastructure évolue avec les notions abordées
et les configurations mises en place.

Selon les sujets, les labs portent sur l’analyse du réseau,
la configuration des équipements, leur sécurisation ou la vérification
des solutions déployées. Les rapports présentent la démarche suivie,
les résultats obtenus et les difficultés rencontrées.

## Organisation du dépôt

Un dossier est consacré à chaque chapitre. Selon les besoins du lab,
il peut contenir :

- `README.md` : présentation du travail et indications pour le consulter.
- `rapport/` : sources LaTeX et illustrations.
- `captures/` : captures réseau utilisées pour les analyses.
- `configs/` : configurations des équipements et des services.
- `eve-ng/` : exports du laboratoire.

Les chapitres sont ajoutés au fur et à mesure de la formation.
Les participants et leurs contributions sont précisés dans les travaux
concernés lorsqu’ils sont réalisés à plusieurs.

## Environnement de travail

Les laboratoires sont réalisés sous EVE-NG, hébergé dans une VM
sur VMware Workstation.

L’environnement comprend notamment :

- Cisco IOSv et IOSvL2 ;
- MikroTik CHR ;
- VyOS ;
- Ubuntu Server ;
- VPCS.

Wireshark est utilisé pour l’analyse du trafic et LaTeX pour la rédaction
des rapports. Les outils et versions propres à chaque lab sont indiqués
dans son dossier.

## Cadre des travaux

CamTrust Bank est une organisation fictive. Les tests présentés
sont réalisés dans le laboratoire pédagogique, sur les équipements
du périmètre étudié.

Les captures et configurations peuvent contenir des données de test :
leur diffusion doit être vérifiée avant toute publication.
Les images système des équipements ne sont pas incluses dans le dépôt.

Ce dépôt est un espace de travail étudiant, et non un dépôt officiel
de l’Académie ENIX.