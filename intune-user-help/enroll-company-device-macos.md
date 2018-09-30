---
title: Inscrire votre appareil macOS fourni par l’entreprise dans la gestion | Microsoft Docs
description: Explique comment inscrire dans Intune un appareil macOS qui a été acheté et fourni par votre organisation.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: a5808a0ac80390b76058827d2ca0870249b043b9
ms.sourcegitcommit: 11cad61c565c474a8d653181675cc1109d562626
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43241828"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>Inscrire l’appareil macOS fourni par votre organisation dans la gestion

Découvrez comment passer votre appareil macOS en mode géré dans Intune.  

Les appareils qui vous sont fournis par votre entreprise ou votre établissement scolaire sont souvent préconfigurés quand vous les recevez. Votre organisation envoie ces paramètres préconfigurés à votre appareil la première fois que vous l’activez et que vous vous connectez. Une fois la configuration de votre appareil terminée, vous recevez l’accès aux ressources de votre entreprise ou de votre établissement scolaire. 

Pour commencer la configuration de la gestion, mettez votre appareil sous tension, puis connectez-vous avec vos informations d’identification professionnelles ou scolaires. Le reste de cet article décrit les étapes à suivre et les écrans qui s’affichent quand vous parcourez l’Assistant Configuration.   

## <a name="what-is-apple-dep"></a>Qu’est-ce qu’Apple DEP ?
Il se peut que votre organisation ait acheté ses appareils par le biais du *Programme d’inscription des appareils Apple (DEP, Device Enrollment Program)*. Le programme DEP Apple permet aux organisations d’acheter de grandes quantités d’appareils iOS ou macOS. Elles peuvent ensuite configurer et gérer ces appareils dans leur fournisseur de gestion des appareils mobiles préféré, comme Intune. Si vous êtes administrateur et que vous souhaitez obtenir des informations supplémentaires sur le programme DEP Apple, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils d’Apple](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos).  

## <a name="set-up-your-macos-device"></a>Configurer votre appareil macOS  
Effectuez les étapes suivantes pour inscrire votre appareil macOS dans la gestion. Si vous utilisez votre propre appareil, plutôt qu’un appareil d’entreprise, suivez les étapes relatives aux [appareils personnels et BYOD](enroll-your-device-in-intune-macos-cp.md).  

1. Mettez sous tension votre appareil macOS. 
2. Choisissez votre **Langue**, puis cliquez sur **Continuer**.  

   ![Capture de l’écran d’accueil de l’Assistant Configuration d’un appareil macOS, affichant la liste des langues dans laquelle effectuer la sélection.](./media/macos-dep-welcome-1808.png)   
3. Choisissez une disposition du clavier. La liste affiche une ou plusieurs options en fonction de la langue sélectionnée. Pour afficher toutes les options de disposition, quelle que soit la langue sélectionnée, cliquez sur **Afficher tout**. Quand vous avez terminé, cliquez sur **Continuer**.  

   ![Capture de l’écran Disposition du clavier de l’Assistant Configuration d’un appareil macOS, affichant la liste des langues dans laquelle effectuer la sélection, une option Afficher tout décochée, un bouton Précédent et un bouton Continuer.](./media/macos-dep-keyboard-1808.png)  
4. Sélectionnez votre réseau Wi-Fi. Vous devez disposer d’une connexion Internet pour continuer l’installation. Si vous ne voyez pas votre réseau, ou si vous avez besoin de vous connecter via un réseau câblé, cliquez sur **Autres options réseau**. Quand vous avez terminé, cliquez sur **Continuer**.  

   ![Capture de l’écran de sélection de votre réseau Wi-Fi de l’Assistant Configuration d’un appareil macOS, affichant la liste des réseaux disponibles dans laquelle effectuer la sélection. Montre également un bouton Autres options réseau, un bouton Précédent et un bouton Continuer.](./media/macos-dep-wifi-1808.png)  
5. Une fois que vous êtes connecté au réseau Wi-Fi, l’écran **Gestion à distance** s’affiche. L’option Gestion à distance permet à l’administrateur de votre organisation de configurer à distance votre appareil avec les comptes, les paramètres, les applications et les réseaux exigés par l’entreprise. Avant de continuer, lisez la documentation pour comprendre comment votre appareil est géré. Puis, cliquez sur **Continuer**.  

   ![Capture de l’écran de gestion à distance de l’Assistant Configuration d’un appareil macOS, avec du texte expliquant la gestion à distance et présentant un lien vers de la documentation pour obtenir plus d’informations. Montre également un bouton Précédent et un bouton Continuer.](./media/macos-dep-remote-management-1-1808.png)  
6. Quand vous y êtes invité, connectez-vous avec votre compte professionnel ou scolaire. Une fois que vous êtes authentifié, votre appareil installe un profil de gestion. Le profil configure et active votre accès aux ressources de votre organisation.  
7. Renseignez-vous sur l’icône de données et de confidentialité d’Apple afin de pouvoir identifier par la suite le moment où des informations personnelles sont collectées. Puis, cliquez sur **Continuer**.  

   ![Capture de l’écran de données et de confidentialité de l’Assistant Configuration d’un appareil macOS, affichant une illustration de deux personnes en train de se serrer la main et décrivant l’utilisation des données personnelles d’Apple. Montre également un bouton Précédent et un bouton Continuer.](./media/macos-dep-apple-data-privacy-1808.png)  
8. Une fois votre appareil inscrit, vous pouvez avoir à exécuter des étapes supplémentaires. Les étapes qui s’affichent dépendent de la façon dont votre organisation a personnalisé l’expérience de configuration. Vous pouvez être tenu d’effectuer les opérations suivantes :
    * Vous connecter à un compte Apple
    * Accepter les conditions générales
    * Créer un compte d’ordinateur
    * Effectuer une installation rapide
    * Configurer votre Mac  
## <a name="get-the-company-portal-app"></a>Obtenir l’application Portail d’entreprise      
Accédez à l’App Store pour obtenir l’application Portail d’entreprise Intune sur votre appareil. Cette application vous permet de surveiller, de synchroniser, d’ajouter et de supprimer votre appareil de la gestion, ainsi que d’installer des applications.

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).