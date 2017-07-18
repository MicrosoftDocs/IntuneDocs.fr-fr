---
title: "Guide pratique pour configurer des paramètres de messagerie Intune"
titleSuffix: Intune on Azure
description: "Découvrez comment configurer Intune pour créer des connexions à la messagerie d’entreprise sur les appareils que vous gérez."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 484bd9b0-fbf1-4f4f-940c-6b12fa07e228
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2ae3e8ec9f9c791d536fe311bc4d30cae41b9482
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Guide pratique pour configurer des paramètres de messagerie dans Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Des profils de messagerie peuvent être utilisés pour configurer les appareils que vous gérez avec les paramètres requis pour la connexion à la messagerie d’entreprise et sa synchronisation. Cela peut aider à garantir que les paramètres sont standard sur l’ensemble de vos appareils et également à réduire les appels au support technique des utilisateurs finaux qui ne connaissent pas les paramètres de messagerie corrects.

Le client de messagerie intégré est pris en charge par la plupart des plateformes. La plupart des applications de messagerie tierces ne sont pas prises en charge actuellement.

Vous pouvez utiliser des profils de messagerie pour configurer le client de messagerie natif sur les types d’appareils suivants :

- Android Samsung KNOX Standard 4.0 et versions ultérieures
- Android for Work
- iOS 8.0 et versions ultérieures
- Windows Phone 8.1 et versions ultérieures
- Windows 10 Desktop et Windows 10 Mobile

Utilisez les informations de cette rubrique pour apprendre les notions de base sur la configuration d’un profil de messagerie et lisez les autres rubriques pour chaque plateforme pour en savoir plus sur les caractéristiques des appareils.

## <a name="create-a-device-profile-containing-email-settings"></a>Créer un profil d’appareil contenant des paramètres de messagerie

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de Services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Configuration de l’appareil**.
2. Dans le panneau **Configuration de l’appareil**, choisissez **Gérer** > **Profils**.
3. Dans le panneau des profils, sélectionnez **Créer un profil**.
4. Dans le panneau **Créer un profil**, entrez un **Nom** et une **Description** pour le profil de messagerie.
5. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres de messagerie. Actuellement, vous pouvez choisir l’une des plateformes suivantes pour les paramètres de messagerie :
    - **Android** (Samsung Android KNOX Standard uniquement)
    - **Android for Work**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 et versions ultérieures**
6. Dans la liste déroulante **Type de profil**, choisissez **E-mail**.
7. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Accédez à l’une des rubriques suivantes pour obtenir les paramètres détaillés pour chaque plateforme :
    - [Paramètres d’Android for Work et de Samsung KNOX Standard](email-settings-android.md)
    - [Paramètres iOS](email-settings-ios.md)
    - [Paramètres Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Paramètres Windows 10](email-settings-windows-10.md)
8. Lorsque vous avez terminé, revenez au panneau **Créer un profil** et appuyez sur **Créer**.

Le profil est créé et s’affiche dans le panneau de la liste des profils.
Si vous souhaitez continuer et attribuer ce profil à des groupes, consultez [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md).

## <a name="further-information"></a>Informations supplémentaires

### <a name="remove-an-email-profile"></a>Supprimer un profil de messagerie

Si vous souhaitez supprimer un profil de messagerie d’un appareil, modifiez l’attribution et supprimez les groupes dont l’appareil est membre. Notez que vous ne pouvez pas supprimer un profil de messagerie de cette manière s’il est le seul profil de messagerie sur un appareil.

### <a name="securing-email-access"></a>Sécurisation de l’accès à la messagerie

Vous pouvez aider à sécuriser les profils de messagerie à l’aide de l’une des deux méthodes suivantes :

1. **Certificats** : quand vous créez le profil de messagerie, vous choisissez un profil de certificat que vous avez créé précédemment dans Intune. Il s’agit du certificat d’identité, qui est utilisé pour l’authentification par rapport à un profil de certificat approuvé (ou un certificat racine) pour établir le fait que l’utilisateur est autorisé à se connecter. Le certificat approuvé est affecté à l’ordinateur qui authentifie la connexion de messagerie, en général le serveur de messagerie natif.
Pour plus d’informations sur la création et l’utilisation des profils de certificat dans Intune, consultez [Guide pratique pour configurer des certificats avec Intune](certificates-configure.md).
2. **Nom d’utilisateur et mot de passe** : l’utilisateur s’authentifie auprès du serveur de messagerie natif en fournissant son nom d’utilisateur et son mot de passe.
Comme le mot de passe n’est pas contenu dans le profil de messagerie, l’utilisateur doit le fournir quand il se connecte à sa messagerie.


### <a name="how-intune-handles-existing-email-accounts"></a>Comment Intune gère les comptes de messagerie existants

Si l’utilisateur a déjà configuré un compte de messagerie, le résultat de l’attribution de profil de messagerie Intune dépend de la plateforme de l’appareil :

- **iOS** : un profil de messagerie existant en double est détecté en fonction de l’adresse e-mail et du nom d’hôte. Le profil de messagerie en double bloque l’attribution d’un profil Intune. Dans ce cas, le Portail d’entreprise signale à l’utilisateur qu’il n’est pas conforme et l’invite à supprimer le profil configuré manuellement. Pour éviter ce problème, demandez à vos utilisateurs de s’inscrire avant d’installer un profil de messagerie, ce qui permet à Intune de configurer le profil.
- **Windows** : un profil de messagerie existant en double est détecté en fonction de l’adresse e-mail et du nom d’hôte. Intune remplace le profil de messagerie existant créé par l’utilisateur.
- **Android Samsung KNOX Standard** : Un profil de messagerie existant en double est détecté en fonction de l’adresse e-mail, et est remplacé par le profil Intune.
Étant donné qu’Android n’utilise pas le nom d’hôte pour identifier le profil, nous vous recommandons de ne pas créer plusieurs profils de messagerie à utiliser à la même adresse e-mail sur des hôtes différents, car ils se remplaceront l’un l’autre.
- **Android for Work** Intune fournit deux profils de messagerie Android for Work, un pour chacune des applications de messagerie Gmail et Nine Work. Ces applications sont disponibles dans le Google Play Store et sont installées dans le profil de travail de l’appareil. Ainsi, aucun profil en double ne peut être généré. Ces deux applications prennent en charge les connexions à Exchange. Pour activer la connectivité de la messagerie, déployez l’une de ces applications de messagerie sur les appareils de vos utilisateurs, puis créez et déployez le profil approprié. Les applications de messagerie telles que Nine Work peuvent ne pas être gratuites. Vérifiez les détails de licence de l’application ou contactez le fabricant de l’application si vous avez des questions.

### <a name="update-an-email-profile"></a>Mettre à jour un profil de messagerie

Si vous apportez des modifications à un profil de messagerie que vous avez affecté précédemment, les utilisateurs finaux peuvent voir un message leur demandant d’approuver la reconfiguration de leurs paramètres de messagerie.