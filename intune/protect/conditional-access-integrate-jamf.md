---
title: Intégrer Jamf Pro à Microsoft Intune pour des raisons de conformité
titleSuffix: Microsoft Intune
description: Utilisez des stratégies de conformité Microsoft Intune avec l’accès conditionnel Azure Active Directory pour permettre de sécuriser les appareils gérés par Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722720"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Intégrer Jamf Pro à Intune pour des raisons de conformité

S’applique à : Intune dans le portail Azure

Si votre organisation utilise [Jamf Pro](https://www.jamf.com) pour gérer les Mac des utilisateurs finaux, vous pouvez vous servir des stratégies de conformité Microsoft Intune et de l’accès conditionnel Azure Active Directory pour vérifier que les appareils de votre organisation sont conformes.

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin des éléments suivants pour configurer l’accès conditionnel avec Jamf Pro :

- Jamf Pro 10.1.0 (ou une version ultérieure) ;
- [l’application Portail d’entreprise pour macOS](https://aka.ms/macoscompanyportal) ;
- des appareils macOS équipés d’OS X 10.11 Yosemite (ou une version ultérieure).

## <a name="connect-intune-to-jamf-pro"></a>Connecter Intune à Jamf Pro

Pour connecter Intune à Jamf Pro :

1. Créez une application dans Azure.
2. Autorisez l’intégration d’Intune à Jamf Pro.
3. Configurez l’accès conditionnel dans Jamf Pro.

## <a name="create-an-application-in-azure-active-directory"></a>Créer une application dans Azure Active Directory

1. Dans le [portail Azure](https://portal.azure.com), accédez à **Azure Active Directory** > **Inscriptions d’applications**, puis sélectionnez **Nouvelle inscription**. 

2. Sur la page **Inscrire une application**, spécifiez les détails suivants :
   - Dans la section **Nom**, entrez un nom d’application explicite, par exemple **Accès conditionnel Jamf**.
   - Pour la section **Types de comptes pris en charge**, sélectionnez **Comptes dans n’importe quel répertoire d’organisation**. 
   - Pour **URI de redirection**, laissez la valeur par défaut du site web, puis spécifiez l’URL pour votre instance Jamf.  

3. Sélectionnez **Inscrire** pour créer l’application et ouvrir la page **Vue d’ensemble** de cette nouvelle application.  

4. Sur la page **Vue d’ensemble** de l’application, copiez la valeur **ID d’application (client)** et enregistrez-la pour une utilisation ultérieure. Vous aurez besoin de cette valeur pour des procédures ultérieures.  

5. Sélectionnez **Certificats et clés secrètes** sous **Gérer**. Sélectionnez le bouton **Nouvelle clé secrète client**. Entrez une valeur dans **Description**, sélectionnez une option pour **Expire** et choisissez **Ajouter**.

   > [!IMPORTANT]  
   > Avant de quitter cette page, copiez la valeur de la clé secrète client et enregistrez-la pour une utilisation ultérieure. Vous aurez besoin de cette valeur pour des procédures ultérieures. Cette valeur n’est pas à nouveau disponible sans recréer l’inscription d’application.  

6. Sélectionnez **Autorisations d’API** sous **Gérer**. Sélectionnez les autorisations existantes, puis **Supprimer l’autorisation** pour les supprimer. La suppression de toute les autorisations existantes est nécessaire quand vous ajoutez une nouvelle autorisation. L’application fonctionne uniquement si elle dispose de la seule autorisation nécessaire.  

7. Pour affecter une nouvelle autorisation, sélectionnez **Ajouter une autorisation**. Sur la page **Demander des autorisations d’API**, sélectionnez **Intune**, puis sélectionnez **Autorisations d’application**. Sélectionnez uniquement la case à cocher pour **update_device_attributes**.  

   Sélectionnez **Ajouter une autorisation** pour enregistrer cette configuration.  

8. Sur la page **Autorisations d’API**, sélectionnez **Accorder le consentement administrateur pour Microsoft**, puis sélectionnez **Oui**.  

   Le processus d’inscription d’application dans Azure AD est terminé.


    > [!NOTE]
    > Si la clé secrète client arrive à expiration, vous devez créer une clé secrète client dans Azure, puis mettre à jour les données d’accès conditionnel dans Jamf Pro. Azure vous autorise à avoir les deux clés secret (l’ancienne et la nouvelle) actives afin d’éviter toute interruption de service.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Autoriser l’intégration d’Intune à Jamf Pro

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et accédez à **Microsoft Intune** > **Conformité de l’appareil** > **Gestion des appareils partenaires**.

2. Activez le connecteur de conformité de Jamf en collant l’ID d’application que vous avez enregistré au cours de la procédure précédente dans le champ **ID d’application Jamf Azure Active Directory**.

3. Sélectionnez **Enregistrer**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurer l’intégration de Microsoft Intune dans Jamf Pro

1. Dans Jamf Pro, accédez à **Gestion globale** > **Accès conditionnel**. Cliquez sur le bouton **Modifier** sous l’onglet **Intégration de macOS Intune**.

2. Cochez la case **Activer l’intégration d’Intune pour macOS**.

3. Saisissez les informations requises sur votre client Azure, notamment **Emplacement**, **Nom de domaine**, **ID d’application** et la valeur pour la *clé secrète client* que vous avez enregistrée lors de la création de l’application dans Azure AD.  

4. Sélectionnez **Enregistrer**. Jamf Pro teste vos paramètres et vérifie que tout fonctionne.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurer des stratégies de conformité et inscrire des appareils

Une fois que vous avez configuré l’intégration entre Intune et Jamf, vous devez [appliquer des stratégies de conformité aux appareils gérés par Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Déconnecter Jamf Pro et Intune 

Si vous n’utilisez plus Jamf Pro pour gérer les ordinateurs Mac de votre organisation et que vous souhaitez que les utilisateurs soient managés par Intune, vous devez supprimer la connexion entre Jamf Pro et Intune. Supprimez la connexion à l’aide de la console Jamf Pro. 

1. Dans Jamf Pro, accédez à **Gestion globale** > **Accès conditionnel**. Dans l’onglet **Intégration macOS Intune**, sélectionnez **Modifier**.
2. Décochez la case **Activer l’intégration d’Intune pour macOS**.
3. Sélectionnez **Enregistrer**. Jamf Pro envoie votre configuration à Intune et l’intégration sera interrompue.
4. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Accédez à **Microsoft Intune** > **Conformité de l’appareil** > **Gestion d’appareil partenaire** pour vérifier que l’état est maintenant **Terminé**. 

   > [!NOTE]
   > Les appareils Mac de votre organisation seront supprimés à la date (3 mois) affichée dans votre console. 

## <a name="next-steps"></a>Étapes suivantes

- [Appliquer des stratégies de conformité aux appareils gérés par Jamf](conditional-access-assign-jamf.md)
- [Données envoyées par Jamf à Intune](data-jamf-sends-to-intune.md)