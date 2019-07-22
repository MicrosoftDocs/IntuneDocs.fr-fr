---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ee62213c9ef23302de7fa7342569e1903514699
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341350"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>En développement pour Microsoft Intune - Juillet 2019

Pour faciliter votre préparation et votre planification, cette page liste les mises à jour et les fonctionnalités de l’interface utilisateur Intune qui sont en cours de développement, mais qui ne sont pas encore publiées. De plus :

- Si nous pensons que vous devez effectuer une action avant une modification, nous publierons un billet supplémentaire sur le Centre de messages Office.
- Quand une fonctionnalité est lancée en production, en préversion ou en disponibilité générale, la description de la fonctionnalité disparaît de cette page et de la [page Nouveautés](whats-new.md).
- Cette page et la [page Nouveautés](whats-new.md) sont mises à jour régulièrement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour les livrables et les chronologies stratégiques.

> [!Note]
> Ces éléments reflètent les attentes actuelles de Microsoft sur les fonctionnalités Intune qui apparaîtront dans une version future. Les dates et les fonctionnalités individuelles peuvent changer. Certains éléments en développement n’ont pas de description de fonctionnalité sur cette page.

**Flux RSS** : recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestion d'applications


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Notifications personnalisées pour les utilisateurs et les groupes    <!-- 16766574   -->
Vous serez bientôt en mesure d’envoyer des notifications push ad hoc personnalisées à partir de l’application Portail d’entreprise aux utilisateurs sur des appareils iOS et Android que vous gérez avec Intune. Ces notifications personnalisées ne sont pas liées à des fonctionnalités Intune particulières et peuvent être utilisées à n’importe quel motif, y compris les notifications générales que vous souhaitez envoyer à certains ou à l’ensemble de vos employés.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation <!-- 2576686 -->
Les stratégies de protection des applications Intune (application) sur les appareils Android et iOS vous permettront de contrôler le contenu des notifications d’application pour les comptes d’organisation. Cette fonctionnalité nécessite la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge l’application. Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Application Google Play disponible créant des rapports pour des profils professionnels Android <!-- 3041956  -->
Pour les installations d’applications disponibles sur les appareils avec profil professionnel Android, vous pouvez afficher l’état d’installation des applications, ainsi que la version installée des applications de Google Play managées. Pour plus d’informations, consultez [Guide pratique pour superviser les stratégies de protection des applications](app-protection-policies-monitor.md), [Gérer les appareils avec profil professionnel Android avec Intune](android-enterprise-overview.md) et [Type d’application Google Play gérée](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration des appareils


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Prise en charge des profils VPN IKEv2 pour iOS <!-- 1943438 -->
Vous pourrez créer des profils VPN pour le client VPN natif iOS en utilisant le protocole IKEv2. IKEv2 est un nouveau type de connexion dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **VPN** comme type de profil > **Paramètres**.

Ces profils VPN configurent le client VPN natif. Par conséquent, aucune application cliente VPN n’est installée ou envoyée (par push) aux appareils gérés. Cette fonctionnalité nécessite que les appareils soient inscrits auprès d’Intune (inscription MDM).

Pour afficher les paramètres VPN actuels que vous pouvez configurer, consultez [Configurer les paramètres VPN sur les appareils iOS dans Microsoft Intune](vpn-settings-ios.md).

S’applique à : iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilisez « règles d’applicabilité » lors de la création de profils de configuration d’appareil Windows 10 <!-- 2549910 -->
Vous créez des profils de configuration d’appareil Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme). Vous serez en mesure de créer une **règle d’applicabilité** pour que le profil s’applique seulement à une édition spécifique ou à une version spécifique. Par exemple, vous créez un profil qui active certains paramètres de BitLocker. Une fois que vous avez ajouté le profil, utilisez une règle d’applicabilité pour que le profil s’applique seulement aux appareils exécutant Windows 10 Entreprise.

S’applique à : 
- Windows 10 et versions ultérieures

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Paramètres avancés pour le pare-feu Windows Defender   <!--  1311949     -->
En tant que préversion publique, vous serez bientôt en mesure d’utiliser Intune pour gérer les règles de pare-feu personnalisées sur les clients pour Windows Defender.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Nouveau concepteur de configuration lors de la création d’un profil OEMConfig pour Android Enterprise <!-- 3712769  -->
Dans Intune, vous pouvez créer un profil de configuration d’appareil qui utilise une application OEMConfig (configuration de l’appareil > Profils > créer un profil > Android Enterprise pour la plateforme > OEMConfig pour le type de profil). Dans ce cas, un éditeur JSON s’ouvre avec un modèle et des valeurs que vous pouvez modifier. Cette mise à jour inclut un concepteur de configuration avec une expérience utilisateur améliorée qui affiche des détails incorporés dans l’application, y compris des titres, des descriptions et bien plus encore. L’éditeur JSON est toujours disponible et affiche toutes les modifications que vous apportez dans le concepteur de configuration.

Pour afficher les paramètres actuels, accédez à [utiliser et gérer des appareils Android Enterprise avec OEMConfig](android-oem-configuration-overview.md).

S’applique à : Android Entreprise


<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des appareils

### <a name="improve-device-location---3855417---"></a>Améliorer l’emplacement de l’appareil<!-- 3855417 -->
Vous pouvez effectuer un zoom avant sur les coordonnées exactes d’un appareil à l’aide de l’action **localiser l’appareil** . Pour plus d’informations sur la localisation des appareils iOS perdus, consultez [Rechercher des appareils iOS perdus](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurer la limite de temps de nettoyage automatique des appareils jusqu’à 30 jours <!--4231059  -->
Vous serez en mesure de définir la limite de temps de nettoyage automatique des appareils sur 30 jours (au lieu de la limite actuelle de 90 jours) après la dernière connexion. Pour ce faire, accédez à la**configuration** > **appareils** >  **Intune** > **configurer les règles de nettoyage des appareils**.


<!-- ***********************************************-->
## <a name="security"></a>Sécurité

### <a name="import-and-export-security-baselines------3408610------------"></a>Importer et exporter des lignes de base de sécurité    <!--3408610          -->  
Nous ajoutons la possibilité d’exporter et d’importer des lignes de base de sécurité afin de pouvoir effectuer vos personnalisations avec vous et les partager entre les environnements Intune.



<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.

