# Risque de décrochage scolaire par région — Burkina Faso

Tableau de bord de décision, rapport, présentation et notice d'utilisation de l'analyse du risque de décrochage scolaire dans les 13 régions du Burkina Faso (2016-2025), avec indice de risque composite et carte d'alerte 2026.

**Version 3** : base mise à jour avec 7 variables EHCVM 2021 ; apprentissage 2017-2023, test 2024-2025.

## Résultats en bref

- **Alerte 2026 : Sahel, Est, Centre-Nord, Nord** (probabilité de risque élevé de 0,95 à 1,00).
- **Vigilance : Boucle du Mouhoun, Centre-Est** (le probit et la forêt aléatoire divergent).
- Les variables EHCVM **n'améliorent pas la prévision** ; elles sont conservées dans l'indice et les profils.
- Le modèle ne bat pas nettement la persistance : il sert à hiérarchiser les alertes, pas à les remplacer.
- Limite principale : la source ST-ESU des écoles fermées n'est pas branchée (indicateur de repli).

## Contenu du dépôt

| Chemin | Rôle |
|---|---|
| `index.html` | Tableau de bord interactif (aucune dépendance, fonctionne hors ligne) |
| `assets/data.js` | Données du tableau de bord (résultats de l'analyse, fond de carte) |
| `assets/img/` | Graphiques produits par le script R |
| `docs/Rapport_decrochage_scolaire.docx` | Rapport consolidé avec notes de bas de page |
| `docs/Presentation_decrochage_scolaire.pptx` | Présentation (12 diapositives) |
| `docs/Notice_utilisation.docx` | Notice d'utilisation |
| `analysis/03_analyse_indice_risque_alerte.R` | Script R d'analyse (graine 2026) |
| `analysis/maj_tableau_de_bord.py` | Met à jour `assets/data.js` depuis le classeur Excel produit par R |
| `sorties/journal_console_R.txt` | Journal de la dernière exécution du script |
| `data/` | Emplacement des données d'entrée (non versionnées) |

## Ouvrir le tableau de bord

- **En local** : double-cliquer sur `index.html`.
- **Sur GitHub Pages** : voir ci-dessous.

## Publier sur GitHub Pages

1. Créer un dépôt GitHub et y envoyer ces fichiers (branche `main`).
2. Dans **Settings → Pages**, choisir **Source : GitHub Actions**.
3. Le workflow `.github/workflows/pages.yml` publie le site à chaque envoi sur `main`. L'adresse apparaît dans l'onglet **Actions**.

## Mettre à jour avec de nouvelles données

1. Placer les fichiers dans `data/` (voir `data/README.md`).
2. Exécuter le script R : `source("analysis/03_analyse_indice_risque_alerte.R")` depuis la racine du dépôt.
3. `python3 analysis/maj_tableau_de_bord.py sorties_indice_risque/resultats_indice_risque.xlsx` (nécessite pandas et openpyxl).
4. Recopier les graphiques de `sorties_indice_risque/` dans `assets/img/` si besoin, puis publier.

> Le convertisseur de l'étape 3 a été testé sur un classeur reconstruit à partir des résultats de la version 3, pas sur un classeur issu d'une nouvelle exécution du script R : vérifier le tableau de bord après la première mise à jour.

## Sources et crédits

- Panel primaire et préscolaire 2016-2025 (annuaires et tableaux de bord) ; EHCVM 2021/22, INSD Burkina Faso.
- Fond de carte : geoBoundaries (Runfola et al., 2020, *PLOS ONE* 15(4), e0231866), niveau ADM1 simplifié.
- Méthodes : Venables et Ripley (2002), *MASS* ; Breiman (2001), forêts aléatoires ; OCDE/JRC (2008), indicateurs composites.

Licence : à choisir par le propriétaire du dépôt avant publication.
