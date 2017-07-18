---
title: "Guide pratique d’affectation d’applications aux groupes"
titleSuffix: Intune on Azure
description: "Une fois que vous avez ajouté une application à Intune, vous souhaiterez l’attribuer à des groupes d’utilisateurs ou d’appareils."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 059c6d2c65c78b6a94f93c26d606abe0451edbbb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Guide pratique pour attribuer des applications à des groupes avec Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Une fois que vous avez ajouté une application à Intune, vous pouvez l’affecter à des utilisateurs et des appareils.

Les applications peuvent être affectées aux appareils, qu’ils soient gérés par Intune ou non. Utilisez le tableau suivant pour vous aider à comprendre les différentes options pour attribuer des applications aux utilisateurs et aux appareils :

||||
|-|-|-|-|
|&nbsp;|Appareils inscrits avec Intune|Appareils non inscrits avec Intune|
|Attribuer aux utilisateurs|Oui|Oui|
|Attribuer aux appareils|Oui|Non|
|Attribuer des applications encapsulées ou incorporer le SDK Intune (pour les stratégies de protection d’application)|Oui|Oui|
|Attribuer des applications en tant qu’applications disponibles|Oui|Oui|
|Attribuer des applications en tant qu’applications requises|Oui|Non|
|Désinstallation d’applications|Oui|Non|
|Les utilisateurs finaux installent les applications disponibles à partir de l’application Portail d’entreprise|Oui|Non|
|Les utilisateurs finaux installent les applications disponibles à partir du portail d’entreprise web|Oui|Oui|

> [!NOTE]
> Actuellement, vous pouvez affecter des applications iOS et Android (applications métier ou achetées sur une boutique) pour les appareils qui ne sont pas inscrits avec Intune.

## <a name="how-to-assign-an-app"></a>Comment affecter une application

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de Services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Applications mobiles**.
1. Dans la charge de travail **Applications mobiles**, choisissez **Gérer** > **Applications**.
2. Dans la liste du panneau d’applications, cliquez sur l’application que vous souhaitez affecter.
3. Dans le panneau <*Nom de l’application*> - **Vue d’ensemble**, choisissez **Gérer** > **Affectations**.
4. Choisissez **Sélectionner des groupes** puis, dans le panneau **Sélectionner des groupes**, sélectionnez les groupes Azure AD auxquels vous souhaitez affecter l’application.
5. Pour chaque application que vous choisissez, choisissez un **Type d’affectation** pour l’application :
    - **Disponible** : les utilisateurs effectuent l’installation de l’application à la demande à partir de l’application ou du site web de portail d’entreprise.
    - **Non applicable** : l’application n’est pas installée ni affichée dans le portail d’entreprise.
    - **Requis** : l’application est installée sur les appareils dans les groupes sélectionnés.
    - **Désinstaller** : l’application est désinstallée des appareils dans les groupes sélectionnés.
    - **Disponible avec ou sans inscription** : affectez cette application à des groupes d’utilisateurs dont les appareils ne sont pas inscrits avec Intune.
6. Une fois que vous avez terminé, choisissez **Enregistrer**.

L’application est maintenant affectée au groupe que vous avez sélectionné.

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Résolution des conflits entre les intentions d’application

Parfois, la même application est affectée à plusieurs groupes, mais avec des intentions différentes. Dans ces cas-là, utilisez le tableau ci-dessous pour comprendre l’intention résultante.

||||
|-|-|-|
|Intention du groupe 1|Intention du groupe 2|Intention résultante|
|Utilisateur obligatoire|Utilisateur disponible|Obligatoire et disponible|
|Utilisateur obligatoire|Utilisateur non disponible|Obligatoire|
|Utilisateur obligatoire|Désinstallation utilisateur|Obligatoire|
|Utilisateur disponible|Utilisateur non disponible|Non disponible|
|Utilisateur disponible|Désinstallation utilisateur|Désinstaller|
|Utilisateur non disponible|Désinstallation utilisateur|Désinstaller
|Utilisateur obligatoire|Appareil obligatoire|Toutes deux existent, la passerelle traite Obligatoire 
|Utilisateur obligatoire|Désinstallation appareil|Toutes deux existent, la passerelle résout Obligatoire 
|Utilisateur disponible|Appareil obligatoire|Toutes deux existent, la passerelle résout Obligatoire (Obligatoire et Disponible)
|Utilisateur disponible|Désinstallation appareil|Toutes deux existent, la passerelle résout Disponible.<br>L’application apparaît dans le portail d’entreprise.<br>Dans le cas où l’application est déjà installée (en tant qu’application obligatoire avec intention précédente), elle est désinstallée.<br>Mais si l’utilisateur clique sur Installer dans le portail d’entreprise, l’application est installée et l’intention de désinstallation n’est pas honorée.|
|Utilisateur non disponible|Appareil obligatoire|Obligatoire|
|Utilisateur non disponible|Désinstallation appareil|Désinstaller|
|Désinstallation utilisateur|Appareil obligatoire|Toutes deux existent, la passerelle résout Obligatoire|
|Désinstallation utilisateur|Désinstallation appareil|Toutes deux existent, la passerelle résout Désinstallation|
|Appareil obligatoire|Désinstallation appareil|Obligatoire|
|Utilisateur obligatoire et disponible|Utilisateur disponible|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Désinstallation utilisateur|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Utilisateur non disponible|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Appareil obligatoire|Toutes deux existent Obligatoire et disponible
|Utilisateur obligatoire et disponible|Appareil non disponible|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Désinstallation appareil|Toutes deux existent, la passerelle résout Obligatoire. Obligatoire et disponible
|Utilisateur non disponible|Appareil non disponible|Non disponible|
|Utilisateur disponible|Appareil non disponible|Disponible|
|Utilisateur obligatoire|Appareil non disponible|Obligatoire|
|Utilisateur disponible sans inscription|Utilisateur obligatoire et disponible|Obligatoire et disponible
|Utilisateur disponible sans inscription|Utilisateur obligatoire|Obligatoire
|Utilisateur disponible sans inscription|Utilisateur non disponible|Non disponible
|Utilisateur disponible sans inscription|Utilisateur disponible|Disponible|
|Utilisateur disponible sans inscription|Appareil obligatoire|Obligatoire et disponible sans inscription|
|Utilisateur disponible sans inscription|Appareil non disponible|Disponible sans inscription|
|Utilisateur disponible sans inscription|Désinstallation appareil|Désinstaller et disponible sans inscription.<br>Si l’utilisateur n’a pas installé l’application à partir du portail d’entreprise, la désinstallation est honorée.<br>Si l’utilisateur installe l’application à partir du portail d’entreprise, l’installation est prioritaire par rapport à la désinstallation.|

>[!NOTE]
>Pour les applications de l’App Store iOS gérées uniquement, quand vous les ajoutez à Intune et que vous les affectez comme Obligatoire, elles sont créées automatiquement avec des intentions Obligatoire et Disponible.

## <a name="next-steps"></a>Étapes suivantes

Consultez la page [Guide pratique pour surveiller des applications](apps-monitor.md) pour plus d’informations pour vous aider à contrôler les affectations de l’application.