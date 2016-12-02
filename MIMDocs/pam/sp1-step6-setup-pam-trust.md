---
title: "手順 6. PAM 信頼のセットアップ"
description: "スクリプトによって、Privileged Identity Manager で管理する既存の ID または新規の ID を使用して CORP ドメインを準備する"
keywords: 
author: barclayn
ms.author: barclayn
manager: MBaldwin
ms.date: 10/25/2016
ms.topic: article
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 365989693f844f117f76ee2b69db85df82f06f35
ms.openlocfilehash: 5bcf4f4ef201236746ec1bf75c1c8900841a6c79


---

# <a name="step-6-set-up-the-pam-trust"></a>手順 6. PAM 信頼のセットアップ

>[!div class="step-by-step"]
[« 手順 5](sp1-step5-configuring-pam.md)
[手順 7 »](sp1-step7-setup-sidhistory-sidfiltering.md)

**PRIV のみの環境に必須ではありません。** MIMAdmin アカウントを使用して PAMServer にログインします。

1. MIMAdmin アカウントを使用して PAMServer にログイン
2. 管理者として PowerShell を実行
3. cd $env:path: SYSTEMDRIVE\PAM
4. .\PAMDeployment.ps1
5. メニュー オプション 6 (PAM の信頼のセットアップ) を選択

  要求された場合は、CORP 管理者アカウントの資格情報を入力します。 資格情報を入力した後、信頼関係が確立され、構成が完了します。

>[!div class="step-by-step"]
[« 手順 5](sp1-step5-configuring-pam.md)
[手順 7 »](sp1-step7-setup-sidhistory-sidfiltering.md)



<!--HONumber=Nov16_HO2-->

