#  NeuroTrace : Détection et Traçabilité Sécurisée des Tumeurs Cérébrales (IA & Blockchain)

![Statut](https://img.shields.io/badge/Statut-En_développement-orange)
![IA](https://img.shields.io/badge/IA-Opérationnelle-brightgreen)
![Blockchain](https://img.shields.io/badge/Blockchain-En_cours-yellow)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-red)
![Hyperledger Fabric](https://img.shields.io/badge/Hyperledger_Fabric-2.5-blue)

##  Description du Projet

**NeuroTrace** est une solution innovante qui combine l'**Intelligence Artificielle (IA)** et la **Blockchain** pour analyser des images IRM cérébrales tout en garantissant la traçabilité et la vérification de l'intégrité des données et des résultats produits.

Le système répond à une problématique majeure en imagerie médicale : *Comment garantir a posteriori qu'une image et son analyse n'ont pas été modifiées ?*

Pour cela, le projet repose sur une séparation stricte des rôles :
-  **L'IA** effectue l'analyse et la classification de l'image (Détection de tumeurs : gliome, méningiome, hypophyse, ou absence).
-  **La Blockchain** ne classifie jamais. Elle enregistre uniquement les empreintes cryptographiques (SHA-256) et l'historique pour garantir la provenance et l'intégrité, **sans jamais stocker les images médicales directement sur le registre**.

## ⚙️ Pipeline Fonctionnel

Le flux de travail de NeuroTrace s'articule autour des étapes suivantes :

1. **Ingestion** : Réception de l'image IRM et attribution d'un identifiant pseudonymisé (ex. `CASE_001`).
2. **Prétraitement** : Recadrage, redimensionnement (224x224), normalisation et amélioration du contraste (CLAHE).
3. **Analyse IA** : Classification via un modèle de Deep Learning (CNN/ResNet) avec score de confiance.
4. **Validation** : Application de règles métier (Accepté, Révision requise ou Rejeté selon la confiance et la qualité).
5. **Explicabilité (XAI)** : Génération d'une carte de chaleur (Grad-CAM) pour visualiser les zones d'intérêt.
6. **Hachage** : Calcul de l'empreinte SHA-256 de chaque artefact (image, prédiction, validation).
7. **Blockchain** : Enregistrement des empreintes et de la chaîne de provenance sur Hyperledger Fabric.
8. **Vérification** : Contrôle ultérieur de l'intégrité (détection de toute modification).

##  État d'Avancement

| Module | Statut | Détails |
| :--- | :---: | :--- |
| **Prétraitement & Data** | ✅ Terminé | Nettoyage, splits, gestion des doublons. |
| **Modèle IA (Classification)** | ✅ Terminé | Entraînement et évaluation (Accuracy, F1-Score, etc.). |
| **Explicabilité (Grad-CAM)** | ✅ Terminé | Génération des heatmaps. |
| **Hachage (SHA-256)** | ✅ Terminé | Module de calcul et vérification des empreintes. |
| **Réseau Blockchain** | 🔄 **En cours** | Déploiement du réseau de test Hyperledger Fabric. |
| **Smart Contract (Chaincode)** | 🔄 **En cours** | Développement des fonctions d'enregistrement et de vérification. |
| **API Backend & Orchestrateur** | ⏳ À venir | Intégration FastAPI et des agents spécialisés. |
| **Interface Web** | ⏳ À venir | Interface de démonstration (HTML/CSS/JS). |

>  **Note sur la Blockchain** : L'architecture globale a été pensée de manière modulaire. Le module de hachage étant opérationnel, l'intégration avec le réseau Hyperledger Fabric est actuellement en cours de développement. Le pipeline IA est déjà pleinement fonctionnel et testé indépendamment.

