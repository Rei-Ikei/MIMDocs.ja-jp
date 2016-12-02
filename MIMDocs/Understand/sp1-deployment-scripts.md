---
title: "MIM2016 SP1 PAM 展開スクリプト"
description: "スクリプトによって、Privileged Identity Manager で管理する既存の ID または新規の ID を使用して CORP ドメインを準備する"
keywords: 
author: barclayn
ms.author: barclayn
manager: MBaldwin
ms.date: 09/26/2016
ms.topic: article
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 99b1ff9f622ddd357866b2a3f9f4cc8e0fc88005
ms.openlocfilehash: 82500ff42e24f5b155bfdd336566a2cd3d87fe7e


---

# <a name="mim2016-sp1-pam-deployment-scripts"></a>MIM2016 SP1 PAM 展開スクリプト

この Service Pack には、PAM の展開を容易にする一連の展開スクリプトが導入されています。 これらのスクリプトは、ダウンロード センターで入手できます。 スクリプトを使用する前に、次の前提条件が使用中の環境に当てはまることを確認してください。

重要な前提条件:
1. すべてのコンピューターのオペレーティング システムが、Windows Server 2012 R2 以上です。 Windows Server 2016 Technical Preview 5 を試す場合は、TP5 ビルドを使用して PRIV ドメイン コント ローラーをインストールする必要があります。
2. DNS は、ドメイン コントローラーとコンポーネントのサーバー間での名前解決が自動となるように構成する必要があります。
3. インストール バイナリは、SQL、SharePoint、および MIM のインストールで指定したサーバーのローカルで使用可能にする必要があります。
4. この環境には、次の 3 つ専用 (物理または仮想) コンピューターがあり、別々に CORPDC、PRIVDC、PAMSERVER を実行しています。
5. 検証オプション用に、この手順を実行する専用のクライアント コンピューターが存在するものとします。

>[!NOTE]
>スクリプトの実行に関する問題が発生した場合は、ログの確認が必要になる場合があります。 すべてのスクリプト ログは、%AppData%\MIMPAMInstall に保存されます。 フォルダーを Zip ファイルに圧縮して、操作およびエラーの詳細と共に電子メールで mim2016@microsoft.com に送信してください。

PAM 展開スクリプトを使用する準備ができたら、 「[スクリプトを使用した PAM の構成](/microsoft-identity-manager/pam/sp1-pam-configure-using-scripts)」に進んでください。



<!--HONumber=Oct16_HO1-->

