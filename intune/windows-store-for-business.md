---
title: "Gérer les applications à partir du Windows Store pour Entreprises"
titleSuffix: Intune on Azure
description: "Découvrez comment synchroniser les applications dans Intune depuis Windows Store pour Entreprises, puis les affecter et assurer leur suivi."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: de6ed7623e33a50bdf8452cbf1bad9c648b13d04
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Guide pratique pour gérer les applications que vous avez achetées dans le Windows Store pour Entreprises avec Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


[Windows Store pour Entreprises](https://www.microsoft.com/business-store) propose un lieu dans lequel vous pouvez trouver et acheter des applications pour votre organisation, individuellement ou par lots. En connectant le Windows Store à Microsoft Intune, vous pouvez gérer les applications achetées en volume depuis le portail Intune. Exemple :
* Vous pouvez synchroniser la liste des applications que vous avez achetées dans le Store avec Intune.
* Les applications qui sont synchronisées apparaissent dans la console d’administration Intune. Vous pouvez les affecter comme toute autre application.
* Vous pouvez effectuer un suivi du nombre de licences disponibles et de la quantité de licences utilisée dans la console d’administration Intune.
* Intune bloque l’attribution et l’installation des applications s’il n’y a pas suffisamment de licences disponibles.

## <a name="before-you-start"></a>Avant de commencer

Passez en revue les informations suivantes avant de commencer la synchronisation et l’attribution des applications à partir du Windows Store pour Entreprises :

- Configurez Intune comme autorité de gestion des appareils mobiles pour votre organisation.
- Vous devez avoir créé un compte sur Windows Store pour Entreprises.
- Une fois que vous avez associé un compte Windows Business Store avec Intune, vous ne pouvez pas basculer sur un autre compte ultérieurement.
- Les applications achetées depuis le Store ne peuvent pas être manuellement ajoutées ou supprimées d’Intune. Elles peuvent uniquement être synchronisées avec Windows Store pour Entreprises.
- Intune synchronise les applications sous licence en ligne et hors connexion que vous avez achetées à partir du Windows Store pour Entreprises.
- Seules les applications hors connexion qui sont gratuites peuvent être synchronisées avec Intune.
- Les appareils doivent être joints aux services de domaine Active Directory ou à un espace de travail pour pouvoir utiliser cette fonctionnalité.
- Les appareils inscrits doivent utiliser la version 1511 de Windows 10 ou version ultérieure.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Associer votre compte Windows Store pour Entreprises à Intune
Avant d’activer la synchronisation dans la console Intune, vous devez configurer votre compte de Store pour utiliser Intune comme outil de gestion :
1. Veillez à vous connecter à Business Store avec le compte de locataire que vous utilisez pour accéder à Intune.
2. Dans Business Store, choisissez **Paramètres** > **Outils de gestion**.
3. Sur la page Outils de gestion, choisissez **Ajouter un outil de gestion**, puis sélectionnez **Microsoft Intune**.

> [!NOTE]
> Auparavant, vous ne pouviez associer qu’un seul outil de gestion pour affecter des applications au Windows Store pour Entreprises. Désormais, vous pouvez associer plusieurs outils de gestion au Windows Store, par exemple, Intune et Configuration Manager.

Vous pouvez maintenant continuer et configurer la synchronisation dans la console Intune.

## <a name="configure-synchronization"></a>Configuration de la synchronisation

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de Services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Applications mobiles**.
1. Dans le panneau **Mobile Apps**, choisissez **Installation** > **Windows Store pour Entreprises**.
2. Cliquez sur **Activer**.
3. Si ce n’est déjà fait, cliquez sur le lien pour vous inscrire au Windows Store pour Entreprises et associer votre compte comme détaillé précédemment.
5. Dans la liste déroulante **Langue**, choisissez la langue d’affichage des applications du Windows Store pour Entreprises dans le portail Intune. Quelle que soit la langue dans laquelle elles sont affichées, elles sont installées dans la langue de l’utilisateur final quand elles sont disponibles.
6. Cliquez sur **Synchroniser** pour récupérer les applications que vous avez achetées dans le Windows Store dans Intune.

## <a name="synchronize-apps"></a>Synchroniser les applications

1. Dans la charge de travail **Applications mobiles**, choisissez **Installation** > **Windows Store pour Entreprises**.
2. Cliquez sur **Synchroniser** pour récupérer les applications que vous avez achetées dans le Windows Store dans Intune.

## <a name="assign-apps"></a>Attribuer des applications

Vous affectez des applications à partir du Windows Store de la même façon que vous affectez toute autre application Intune. Pour plus d’informations, consultez [Guide pratique pour attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md). Toutefois, au lieu d’affecter les applications à partir de la page **Toutes les applications**, affectez-les à partir de la page **Applications sous licence**.

Les applications hors connexion peuvent cibler des groupes d’utilisateurs, des groupes d’appareils ou des groupes contenant des utilisateurs et des appareils.
Les applications hors connexion peuvent être installées pour un utilisateur spécifique sur un appareil ou pour tous les utilisateurs sur un appareil. 


Lorsque vous affectez une application Windows Store pour Entreprises, une licence est utilisée par chaque utilisateur qui installe l’application. Si vous avez utilisé toutes les licences disponibles pour une application affectée, vous ne pouvez plus affecter d’autres copies. Effectuez l’une des actions suivantes :
* Désinstallez l’application de certains appareils.
* Réduisez la portée de l’attribution actuelle pour cibler uniquement les utilisateurs pour lesquels vous avez suffisamment de licences.
* Achetez plus de copies de l’application dans Windows Store pour Entreprises.

