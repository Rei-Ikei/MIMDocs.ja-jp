---
title: "手順 7. セットアップ SID 履歴/SID フィルター"
description: "これは、スクリプトを使用した Privileged Identity Manager 構成の 7 番目の手順です。 この手順では、SID 履歴/SID のフィルターのセットアップを行います。"
keywords: 
author: barclayn
ms.author: barclayn
manager: MBaldwin
ms.date: 08/18/2017
ms.topic: article
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
ms.openlocfilehash: e3d8578e9d58ccc2f3dc3bb4ff437d124bf15291
ms.sourcegitcommit: 8edd380f54c3e9e83cfabe8adfa31587612e5773
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2017
---
# <a name="step-7-set-up-sid-historysid-filtering"></a>手順 7. SID 履歴/SID フィルターのセットアップ

>[!div class="step-by-step"]
[« 手順 6](sp1-step6-setup-pam-trust.md)
[手順 8 »](sp1-step8-pam-deployment-verification.md)

**PRIV のみの環境に必須ではありません。** MIMAdmin アカウントを使用して PAMServer にログインします。

1. 管理者として CORP DC にログイン
2. 管理者として PowerShell を実行
3. cd $env:path: SYSTEMDRIVE\PAM
4. .\PAMDeployment.ps1
5. メニュー オプション 8 を選択 (セットアップ SID 履歴/SID フィルター)

正常に実行されると、次のメッセージが表示されます。<br/></br>
SID フィルターの場合: <br/></br>
"信頼で SID をフィルターしないよう設定しています。" または "SID フィルターはこの信頼に対して有効になっていません。" </br></br>
SID 履歴の場合: </br></br>
"この信頼に対して SID 履歴を有効にしています。" または "SID 履歴はこの信頼に対して既に有効になっています。"

>[!div class="step-by-step"]
[« 手順 6](sp1-step6-setup-pam-trust.md)
[手順 8 »](sp1-step8-pam-deployment-verification.md)
