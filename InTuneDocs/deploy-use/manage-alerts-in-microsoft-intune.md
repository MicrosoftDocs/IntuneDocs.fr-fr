---
title: "Gérer les alertes | Microsoft Intune"
description: "Utilisez l’espace de travail Alertes dans Intune pour évaluer l’état d’intégrité global des appareils de votre organisation."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74dc4ce4-21da-4f40-a07f-3eea34561eee
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pbala
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: b84a6e353103f35ad62fb95052c44581dd439963


---

# <a name="manage-alerts-in-microsoft-intune"></a>Gérer les alertes dans Microsoft Intune
Utilisez l’espace de travail **Alertes** de la console d’administration Intune pour évaluer l’état d’intégrité global des appareils de votre organisation et pour identifier les problèmes.

## <a name="view-active-alerts"></a>Afficher les alertes actives

Obtenez des informations générales et des données de synthèse sur les alertes actives.

#### <a name="to-view-active-alerts"></a>Affichage des alertes actives

Dans la console d’administration Intune, suivez l’une de ces séries d’étapes :

-  **Pour afficher des informations générales sur les alertes**, notamment sur les trois premières alertes et le nombre total d’alertes actives, choisissez **Vue d’ensemble du système**. Choisissez les liens de ces alertes pour afficher des informations plus détaillées.

-  **Pour afficher des données de synthèse pour les alertes**, choisissez **Alertes** > **Vue d’ensemble**. Dans la page **Vue d’ensemble des alertes**, la zone **Résumé des types d’alerte** affiche un résumé des alertes. Les alertes critiques sont répertoriées en premier. Choisissez les liens de ces alertes pour afficher des informations plus détaillées.

        > [!NOTE]
        > In some cases, an alert type might appear more than once in the **Alerts Type Summary** list.
        >
        > For example, two instances of the Logical Free Disk Space alert type might be listed:
        >
        > -   3 Logical Free Disk Space
        > -   2 Logical Free Disk Space
        >
        > This occurs when the same alert type is generated for different devices that run different operating systems. In the example, the 3 Logical Free Disk Space alert type might have been generated by a computer that runs Windows 7. The 2 Logical Free Disk Space alert type might have been generated by a computer that runs Windows Vista.

-   **Pour afficher toutes les alertes actives**, choisissez **Alertes** > **Toutes les alertes**. Dans la page **Alertes** figure une liste de toutes les alertes actives. La page comporte ces colonnes :

    -   **Nom**. Il s’agit du nom du type d’alerte qui a généré l’alerte.

    -   **Source**. Cette colonne comporte un lien vers la source de l’alerte. Si le seuil d’affichage du type d’alerte est défini sur **Afficher tout**, ce lien affiche un seul appareil. Si le seuil d’affichage du type d’alerte est défini sur une valeur, ce lien affiche la liste de tous les appareils concernés par cette alerte.

    -   **Dernière mise à jour**. Indique l’heure de dernière modification de l’alerte. Si une alerte est fermée, la date et l’heure de sa fermeture sont affichées.

    -   **Gravité**. Cette colonne indique la gravité de l’alerte.

## <a name="view-notice-board-alerts"></a>Afficher les alertes du panneau d’affichage
Les alertes du panneau d’affichage fournissent des annonces de service importantes. Elles peuvent fournir des informations sur une mise à niveau de service ou une planification de maintenance imminente, ou sur l’état d’une panne.

#### <a name="to-view-and-manage-notice-board-alerts"></a>Pour afficher et gérer les alertes du panneau d'affichage

1.  Dans la console d’administration Intune, choisissez **Vue d’ensemble du système**.

2.  Le cas échéant, les informations importantes concernant le service sont affichées dans la zone **Panneau d’affichage**.

3.  Pour exporter une alerte du panneau d’affichage vers un fichier HTML ou CSV (valeurs séparées par des virgules), dans la console d’administration Intune, choisissez **Alertes** > **Toutes les alertes** >    **Remarques**. Sélectionnez une alerte, choisissez l’icône **Exporter la liste**, puis suivez les instructions.

## <a name="review-intune-system-status"></a>Examiner l’état du système Intune
Dans l’espace de travail **Vue d’ensemble du système**, vous pouvez consulter les récapitulatifs d’**État du système** relatifs à Endpoint Protection, aux mises à jour, à l’intégrité de l’Agent, à la stratégie et aux catégories de logiciels pour identifier les problèmes et donner la priorité à ceux nécessitant votre attention immédiate. Les messages d’erreur générés quand le système est interrompu mènent à la synthèse **État du service**. La synthèse **État du service** donne des détails sur le problème de chaque emplacement et indique l’heure et la date de la dernière mise à jour de la synthèse du système.

#### <a name="to-view-the-status-of-your-subscription"></a>Pour afficher l'état de votre abonnement

1.  Dans la console d’administration Intune, choisissez **Vue d’ensemble du système**.

2.  Explorez la zone **État du système** pour connaître l’état des différents composants de Microsoft Intune.

  Une grande partie des éléments sont liés pour que vous puissiez afficher plus d’informations. Par exemple, sous **Endpoint Protection**, si vous choisissez le nombre d’instances, vous pouvez afficher l’espace de travail **Endpoint Protection**, avec la liste des programmes malveillants détectés. Si vous choisissez le nombre d’appareils, vous pouvez afficher l’espace de travail **Groupes** avec une liste des appareils sur lesquels des programmes malveillants ont été détectés.

## <a name="close-and-reactivate-alerts"></a>Fermer et réactiver des alertes
Les alertes Intune restent actives jusqu’à ce que l’un des événements suivants se produise :

-   Le problème qui a causé la génération de l’alerte est résolu.

-   L'alerte est fermée manuellement.

-   Cinq jours s’écoulent après la génération de l’alerte. Après 45 jours, l’alerte expire et se ferme automatiquement.

Les alertes qui sont marquées comme fermées sont définitivement supprimées au bout de 90 jours.

#### <a name="to-manually-close-an-alert"></a>Fermeture manuelle d'une alerte

Dans la console d’administration Intune, suivez l’une de ces séries d’étapes :

- **Pour fermer une alerte à partir de la liste Alertes**, choisissez **Alertes** > **Toutes les alertes**. Sélectionnez une alerte, puis choisissez **Fermer l’alerte**.

- **Pour fermer une alerte sur un appareil spécifique**, choisissez **Groupes** > **Tous les appareils**. Sélectionnez un appareil et choisissez **Afficher les propriétés**. Ensuite, sous l’onglet **Alertes**, sélectionnez une alerte, puis choisissez **Fermer l’alerte**.

- **Pour fermer une alerte du panneau d’affichage**, choisissez **Vue d’ensemble du système**. Choisissez le **X** situé en regard de l’alerte du panneau d’affichage.

#### <a name="to-view-and-reactivate-closed-alerts"></a>Pour afficher et réactiver des alertes fermés

1.  Dans la console d’administration Intune, choisissez **Alertes** > **Toutes les alertes**.

2.  Dans la liste **Filtres**, choisissez **Fermée**.

    Les noms et les informations supplémentaires sur les alertes apparaissent dans le volet de la liste de gestion. Les détails de l’alerte sélectionnée apparaissent dans le volet de visualisation.

3.  Pour réactiver l’alerte sélectionnée, choisissez **Réactiver l’alerte**.

### <a name="see-also"></a>Voir aussi
[Recevoir des alertes Microsoft Intune](../deploy-use/get-notified-by-alerts.md)



<!--HONumber=Dec16_HO2-->

