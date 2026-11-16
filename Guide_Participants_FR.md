# Mission Contoso - Parcours guidé des participants

Construisez votre rapport Power BI avec VS Code, GitHub Copilot, le plug-in
`powerbi-authoring` et Power BI Desktop.
**Formulez vos propres prompts :** précisez votre objectif, donnez le contexte
utile et vérifiez les résultats de l'IA. Ce guide donne des orientations,
pas des demandes prêtes à copier.
Entraidez-vous, mais chaque participant construit son propre projet.

Conservez les sources intactes et ne partagez jamais de secrets ou de jetons.
Le rapport est en anglais et les montants en USD.

## 1. Analyser les fichiers Excel

- Comprendre le contenu des fichiers, ce que représente une ligne et les liens entre tables.
- Repérer les périodes, clés et problèmes de qualité ; comparer avec le dictionnaire fourni.
- Enregistrer les observations dans un fichier.

## 2. Concevoir le modèle de données

- Proposer un schéma en étoile avec des faits, dimensions et relations clairement définis.
- Tenir compte du détail des ventes et des objectifs magasin-mois, sans dupliquer les objectifs.
- Valider le modèle avant de le construire ; enregistrer sa conception dans un fichier.

## 3. Importer les données et enregistrer le projet PBIP

- Importer les cinq sources Excel, vérifier les types et rendre leur emplacement configurable.
- Enregistrer le projet au format PBIP, avec les dossiers du modèle et du rapport.
- Ouvrir le projet dans Power BI Desktop et vérifier que les données chargées correspondent aux sources.

## 4. Créer la table de dates et les relations

- Ajouter un calendrier continu et créer les relations validées dans le même PBIP.
- Vérifier que les filtres magasin et date agissent sur les ventes et les objectifs.
- Comparer les objectifs sur des mois, trimestres ou années complets ; aucun objectif produit/client n'est fourni.

## 5. Créer et vérifier les indicateurs

- Définir le CA, la marge brute historique, le taux de marge, les commandes, les clients et la croissance annuelle.
- Ajouter les objectifs, écarts et taux d'atteinte sur des périmètres comparables, avec des formats clairs.
- Vérifier les résultats indépendamment : coûts des transactions, commandes distinctes et taux de marge calculé sur les totaux.

## 6. Concevoir et créer les pages du rapport

- Préparer les pages du rapport Power BI ; valider le plan avant de construire.
- Créer des visuels lisibles, des filtres utiles et une navigation claire ; contrôler le rendu réel dans Power BI Desktop.
- Enregistrer le plan dans un fichier et les modifications du rapport dans le PBIP existant.

## 6A. Modélisation avancée : sécurité au niveau des lignes (RLS)

- Créer des rôles de sécurité pour chacun des sept pays des magasins.
- Tester chaque rôle avec **Afficher comme** dans Power BI Desktop, pas avec un segment ; vérifier les ventes et les objectifs.
- Conserver les rôles dans le PBIP et noter ce qui reste non protégé, notamment les données maîtres clients et les fichiers locaux modifiables.

## 6B. Modélisation avancée : traductions du modèle

- Ajouter les traductions des métadonnées en français, italien et espagnol, sans changer les noms techniques ni les calculs.
- Enregistrer le glossaire dans un fichier, le valider et vérifier les traductions stockées.
- Garder le rapport en anglais ; ces traductions ne traduisent ni les pages ni les valeurs des données.

## 7. Mener l'enquête et tester le rapport

- Explorer les cinq indices de la mission et vérifier les chiffres, filtres et comparaisons.
- Distinguer les faits des hypothèses ; retenir trois constats, deux actions et une limite.
- Enregistrer les preuves dans un fichier et faire relire le rapport par un autre participant.

## 7A. Publier dans un espace de travail Fabric - Exercice manuel

- Publier manuellement depuis Power BI Desktop dans l'espace autorisé.
- Vérifier le rapport et le modèle publiés ; conserver leurs liens, l'ID du workspace et l'ID du modèle.

## 8. Documenter le rapport Power BI

Compléter un même fichier Markdown en trois étapes, à partir du projet réellement créé.

- Documenter Power Query : sources, requêtes, paramètres, code M et transformations.
- Documenter le modèle : tables, colonnes, relations, calendrier, indicateurs DAX, RLS et traductions.
- Documenter le rapport : pages, visuels, champs utilisés, filtres, interactions et navigation ; préciser les contrôles réalisés et les limites.

## 9. Créer une Fabric App - Optionnel

- Activer le [Fabric Core MCP Server](https://learn.microsoft.com/en-us/rest/api/fabric/articles/mcp-servers/core-remote/get-started-core) dans VS Code ; créer une app séparée, connectée au modèle publié.
- Valider un plan, puis construire les trois pages une par une, avec des visuels, filtres et une navigation adaptés au web.
- Déployer manuellement après la première page puis à la fin ; vérifier dans Fabric les interactions et les valeurs par rapport au rapport.

## 10. Utiliser GitHub Copilot pour faciliter le développement d'un Fabric data agent - Optionnel

Revenir au dossier racine et au chat de création du rapport ; l'app n'est pas nécessaire.

- Créer manuellement l'agent ; copier les instructions préparées par Copilot, puis publier l'agent.
- Faire proposer cinq questions par Copilot et calculer les réponses sur le modèle ; enregistrer le tout dans Excel.
- Ajouter le [MCP du data agent](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-mcp-server#connect-from-visual-studio-code) dans VS Code ; tester les cinq questions et enregistrer les réponses dans Excel.

## 11. Préparer la présentation du groupe

