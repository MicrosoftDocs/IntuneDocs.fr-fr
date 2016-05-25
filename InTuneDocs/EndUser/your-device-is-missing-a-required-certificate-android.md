---
# required metadata

title: Il manque un certificat obligatoire à votre appareil | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Un certificat obligatoire est manquant sur votre appareil
Si votre appareil Android n’est pas inscrit dans Intune et qu’il manque un certificat qui devrait être installé sur votre téléphone, vous ne pouvez pas vous connecter à l’application Portail d’entreprise Android. Quand vous essayez de vous connecter, le message suivant s’affiche :

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

Pour résoudre ce problème et obtenir le certificat obligatoire :

1.  Dans un navigateur, accédez à cette [page du certificat Digicert](https://www.digicert.com/digicert-root-certificates.htm)..

2.  Recherchez et téléchargez le certificat Baltimore CyberTrust Root (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

3.  Faites glisser à partir du haut pour ouvrir vos notifications, puis appuyez sur **BaltimoreCyberTrustRoot.crt** dans la liste des notifications.

4.  Dans la boîte de dialogue **Name the certificate** (Nommer le certificat), acceptez le nom du certificat par défaut.

5. Vérifiez que **Credential Use** (Utilisation des informations d’identification) a la valeur **Used for VPN and apps** (Utilisé pour le VPN et les applications), puis appuyez sur **OK**..

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. Fermez le navigateur web et l’application Portail d’entreprise.

7. Rouvrez l’application Portail d’entreprise. Vous devriez pouvoir vous connecter à l’application Portail d’entreprise. Si vous avez besoin d’aide, contactez votre administrateur informatique.

<!--HONumber=May16_HO1-->

