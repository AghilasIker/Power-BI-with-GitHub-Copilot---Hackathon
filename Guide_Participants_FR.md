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

Avant de commencer, ajouter [Fabric Core MCP Server](https://learn.microsoft.com/en-us/rest/api/fabric/articles/mcp-servers/core-remote/get-started-core)
dans VS Code et activer ses outils dans GitHub Copilot ; réutiliser la connexion si elle existe déjà.

- Vérifier les accès et outils, puis créer une app séparée du projet Power BI, connectée au modèle publié.
- Faire approuver un plan court, puis construire et vérifier les pages une par une : Executive Overview, Stores & Channels, Products & Customers.
- Après la première page, déployer manuellement dans le workspace prévu, puis ouvrir l'app directement dans le portail Fabric pour tester les filtres et comparer les valeurs avec le rapport avant de poursuivre.
- Créer une expérience web fluide et responsive, distincte du rapport ; chaque étape livre une page avec ses visuels, interactions et données.
- Redéployer manuellement l'app complète, puis vérifier les trois pages et leurs résultats réels dans l'app déployée.

## 10. Utiliser GitHub Copilot pour faciliter le développement d'un Fabric data agent - Optionnel

Cet exercice ne nécessite pas l'app.

Avant de commencer, rouvrir le dossier racine `01_Build_With_AI` dans VS Code
via **Fichier > Ouvrir un dossier**, puis reprendre dans l'historique GitHub
Copilot Chat la conversation utilisée pour créer le rapport Power BI,
et non celle de l'app.

**Prérequis :** une capacité compatible avec les data agents, les accès au
workspace/modèle et une connexion MCP autorisée dans VS Code.
Ce parcours ne nécessite pas la préparation du SDK Fabric data agent.

- Créer manuellement le data agent dans le portail Fabric, dans **le même workspace que le modèle sémantique publié** ; connecter ce modèle et sélectionner **toutes ses tables disponibles**.
- Demander à Copilot de préparer les instructions, puis les copier manuellement dans l'agent et enregistrer.
- Demander à Copilot de **proposer lui-même cinq questions métier variées à partir du modèle local ouvert dans Power BI Desktop**, puis de créer le fichier Excel avec ces questions et les réponses attendues calculées via `powerbi-modeling-mcp`.
- Publier manuellement l'agent pour activer son MCP. Copier l'URL depuis **Paramètres > Model Context Protocol**, puis ajouter ce serveur HTTP dans VS Code sous le nom `contoso-data-agent`, choisir **Workspace** comme cible de configuration et se connecter.
- Demander à Copilot de poser les cinq questions via **le MCP de cet agent**, d'enregistrer les réponses réelles dans Excel et de comparer uniquement les valeurs renvoyées aux références obtenues via `powerbi-modeling-mcp` : **PASS** si toutes correspondent dans les tolérances d'arrondi. Les avertissements d'alignement restent dans les notes sans bloquer PASS.
- Si nécessaire, corriger les instructions manuellement, republier et relancer les tests en conservant l'historique. Respecter les règles de l'entreprise concernant l'envoi de données au client MCP.

## 11. Préparer la présentation du groupe

- Sélectionner un rapport par groupe pour une **présentation de cinq minutes en anglais**.
- Démontrer trois constats, deux actions et une limite ; expliquer l'apport de l'IA et vos vérifications.
- Répéter la démonstration ; enregistrer les éventuels supports dans un fichier.
