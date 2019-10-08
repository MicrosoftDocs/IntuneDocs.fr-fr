---
title: Configurer l’intégration de Wandera Mobile Threat Protection à Intune
titleSuffix: Intune on Azure
description: Comment configurer la solution Wandera Mobile Threat Protection à Microsoft Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bf8fd189e50a704e96fc24d0804c5c5d6f91bb4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728219"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Intégrer Wandera Mobile Threat Protection à Intune  

Suivez les étapes ci-dessous pour intégrer la solution Wandera Mobile Threat Defense à Intune.  

## <a name="before-you-begin"></a>Avant de commencer  

Avant de commencer le processus d’intégration de Wandera à Intune, veillez à disposer des prérequis suivants :
- Abonnement Microsoft Intune  
- Informations d’identification d’administrateur Azure Active Directory pour accorder les autorisations suivantes :  
  - Connexion et lecture de profil utilisateur  
  - Accès à l’annuaire en tant qu’utilisateur connecté  
  - Lecture des données de l’annuaire  
  - Envoi des informations d’appareil à Intune  

- Abonnement Wandera :
  - Un ou plusieurs comptes Wandera concédés sous licence pour EMM Connect  
  - Un compte disposant des privilèges de super-administrateur dans Wandera  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Autorisation de l’application une application Wandera Mobile Threat Defense  

Le processus d’autorisation de l’application Wandera Mobile Threat Defense :  
- Autoriser le service Wandera Mobile Threat Defense à communiquer avec Intune des informations relatives à l’état d’intégrité de l’appareil.  
- Wandera se synchronise avec l’appartenance au groupe d’inscription Azure AD pour remplir la base de données de son appareil.  
- Autoriser le portail d’administration Wandera RADAR à utiliser l’authentification unique (SSO) Azure AD.  
- Autoriser l’application Wandera Mobile Threat Defense à se connecter avec l’authentification unique Azure AD.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Configurer l’intégration de Wandera Mobile Threat Defense  
La configuration d’*EMM Connect* pour Wandera nécessite un processus de configuration à usage unique que vous effectuez dans les consoles Intune et Wandera. Ce processus de configuration prend environ 15 minutes. Vous pouvez terminer la configuration sans coordination avec votre compte technique Wandera ou le représentant du support technique.  

### <a name="enable-support-for-wandera-in-intune"></a>Activer la prise en charge de Wandera dans Intune
1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) puis accédez à **Conformité des appareils** > **Protection contre les menaces mobiles** > et sélectionnez **Ajouter**.

2. Dans la page **Ajouter un connecteur**, utilisez la liste déroulante et sélectionnez **Wandera**. Ensuite, sélectionnez **Créer**.  

3. Dans le volet Protection contre les menaces mobiles, sélectionnez le connecteur MTD **Wandera** dans la liste des connecteurs pour ouvrir le volet *Modifier le connecteur*. Sélectionnez **Open the Wandera admin console** (Ouvrir la console d’administration Wandera) pour ouvrir [RADAR](https://radar.wandera.com/login), la console d’administration Wandera, puis connectez-vous. 

4. Dans la console Wandera, accédez à **Paramètres** > **Intégration EMM**, puis sélectionnez l’onglet **EMM Connect**. Utilisez la liste déroulante *Fournisseur EMM* et sélectionnez *Microsoft Intune*.

   ![Sélectionner Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. Sélectionnez **Accorder des autorisations** pour ouvrir une connexion au portail Intune. Connectez-vous à l’aide de vos informations d’identification d’administrateur Intune, cochez la case, puis **acceptez** la demande d’autorisation.  

   ![Accepter les autorisations](./media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera termine la connexion et vous renvoie à la console d’administration RADAR. Répétez le processus pour **accorder** l’accès à d’autres configurations, si nécessaire.  

   ![Intégrations et autorisations](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. Dans la console RADAR, copiez le nom du groupe **SyncOnly** qui apparaît sous **Étiquette EMM**. Vous utiliserez ce nom pour configurer un groupe dans Intune en vue de la synchronisation avec Wandera.

   ![Intégrations et autorisations](./media/wandera-mtd-connector-integration/sync-group-name.png) 

8. Retournez à la console [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et modifiez le connecteur MTD Wandera. Définissez les boutons bascules disponibles sur **On**, puis **enregistrez** la configuration.  

   ![Activer Wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune et Wandera sont maintenant connectés.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Configurer les applications Wandera et un groupe de synchronisation  
Pour déployer Wandera, vous allez ajouter à Intune les applications mobiles Wandera pour les plateformes (iOS et Android), puis les attribuer à un groupe spécifique en vue de la synchronisation ; le groupe *SyncOnly*. 

Les sections et procédures suivantes vous guident tout au long de ce processus.

Pour plus d’informations sur ce processus Wandera, connectez-vous à Wandera [RADAR](https://radar.wandera.com/login). Accédez à **Paramètres** > **Intégration EMM**, sélectionnez l’onglet **Application push**, puis sélectionnez **Microsoft Intune**. L’onglet Application push affichent des instructions mises à jour spécifiques à Intune.  

### <a name="add-the-wandera-apps"></a>Ajouter les applications Wandera  
Créez des applications client dans Intune pour déployer l’application Wandera sur des appareils iOS et Android. Consultez [Ajouter des applications MTD](mtd-apps-ios-app-configuration-policy-add-assign.md) pour obtenir les procédures et des détails personnalisés spécifiques aux applications Wandera.  

Après avoir créé les applications, revenez ici pour créer le groupe de synchronisation et attribuer les applications.  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Créer le groupe de synchronisation et attribuer les applications

1. Obtenez le nom du groupe **SyncOnly** qui apparaît sous **Étiquette EMM** dans la console Wandera RADAR. Peut-être avez-vous enregistré ce nom à l’étape 7 lors de la [prise en charge de Wandera dans Intune](#enable-support-for-wandera-in-intune). Utilisez ce nom comme nom du groupe dans Intune pour la synchronisation Wandera.  

2. Dans la console Intune, accédez à **Groupes** et sélectionnez **Nouveau groupe**. Spécifiez la commande suivante pour configurer le groupe de synchronisation qui sera utilisé par Wandera :
   - **Type de groupe** : **Sécurité**
   - **Nom du groupe** : Spécifiez le nom **SyncOnly** que vous avez récupéré à partir de la console d’administration Wandera RADAR.

   ![configurer le groupe de synchronisation](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Sélectionnez **Membres** et attribuez des groupes qui incluent les appareils iOS et Android que vous souhaitez utiliser avec Wandera.

4. Sélectionnez **Créer** pour enregistrer le groupe.

Pour plus d'informations, consultez [Déployer des applications](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Attribuer les applications Wandera au groupe de synchronisation  
Répétez la procédure suivante pour l’application Wandera que vous avez créée pour iOS et Android.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) puis accédez à **Applications clientes** > **Applications**, puis sélectionnez l’application Wandera.  

2. Sélectionnez **Attributions** puis **Ajouter un groupe**.  

3. Dans le volet *Ajouter un groupe*, pour *Type d’attribution*, sélectionnez **Requis**.

4. Choisissez **Groupes inclus**, puis **Sélectionner les groupes à inclure**. Spécifiez le groupe que vous avez créé pour la synchronisation Wandera, puis cliquez sur **Sélectionner** > **OK** > **OK**. Sélectionnez **Enregistrer** pour terminer l’attribution du groupe.  
 

## <a name="next-steps"></a>Étapes suivantes  
Maintenant que vous avez configuré l’intégration, vous pouvez commencer à configurer des stratégies, configurer l’accès conditionnel avancé, et afficher des rapports dans la console d’administration Wandera. Pour en savoir plus sur la gestion et la configuration Wandera, consultez le [guide de prise en main du centre de support](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) dans la documentation Wandera.  
 