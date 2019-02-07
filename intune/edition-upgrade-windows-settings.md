---
title: Paramètres de mise à niveau de Windows 10 et paramètres mode S dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez la liste de tous les paramètres, et ce qu’ils font lors de la mise à niveau d’une édition de Windows 10 sur un appareil, ou de l’activation du mode S sur un appareil à l’aide d’un profil de configuration d’appareil dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a2a7d7ab1603300119f28596e81ae49cbbcbf550
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54832306"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Paramètres d’appareil Windows 10 (et versions ultérieures) pour mettre à niveau les éditions ou activer le mode S dans Intune

Microsoft Intune comprend de nombreux paramètres permettant de gérer et protéger vos appareils. Cet article répertorie et décrit les paramètres pour mettre à niveau les éditions ou activer le mode S sur les appareils Windows 10. Ces paramètres sont créés dans un profil de configuration de mise à niveau dans Intune et envoyés (push) ou déployés sur les appareils.

Dans le cadre de votre solution MDM (gestion des appareils mobiles), utilisez ces paramètres pour contrôler les options de l’édition et du mode S pour vos appareils Windows 10.

Pour plus d’informations sur cette fonctionnalité, consultez [Mettre à niveau les éditions Windows 10 ou activer le mode S](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez le profil](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Mise à niveau d’édition

- **Édition vers laquelle mettre à niveau** : Sélectionnez l’édition de Windows 10 vers laquelle vous effectuez la mise à niveau. Les appareils ciblés par cette stratégie sont mis à niveau vers l’édition de votre choix.
- **Clé de produit** : Entrez la clé de produit fournie par Microsoft. Une fois que vous avez créé la stratégie basée sur la clé de produit, la clé ne peut plus être mise à jour et est masquée pour des raisons de sécurité. Pour changer la clé de produit, retapez-la en entier.
- **Fichier de licence** : Pour **Windows 10 Holographic for Business** ou **Windows 10 Mobile**, choisissez **Parcourir** afin de sélectionner le fichier de licence fourni par Microsoft. Ce fichier de licence contient des informations de licence pour les éditions vers lesquelles vous mettez à niveau les appareils.

## <a name="mode-switch"></a>Commutateur de mode

- **Aucune configuration** : Un appareil en mode S reste en mode S. Un utilisateur final peut sortir l’appareil du mode S.
- **Rester en mode S** : Empêche l’utilisateur final de sortir l’appareil du mode S.
- **Changer** : Permet de sortir l’appareil du mode S.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il peut ne rien faire pour le moment. Veillez à [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Vous pouvez également créer des profils de mise à niveau d’édition pour les appareils [Windows Holographic for Business](holographic-upgrade.md).