---
title: "証明書マネージャーでテンプレートを使用して証明書を要求する | Microsoft Docs"
description: "証明書マネージャーを使用して、プロファイル テンプレートでソフトウェア証明書を作成および更新する方法について説明します。"
keywords: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/23/2017
ms.topic: article
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: fed5ada9-d80f-4825-aad7-4172ac5d71d3
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 54d03fbd03f6c44298139324ea2dc7d945f008bc
ms.openlocfilehash: 23cfb1134d1cbf2cf838354cb7d915084803cd41
ms.lasthandoff: 01/24/2017


---

# <a name="create-software-certificates-with-certificate-manager"></a>証明書マネージャーを使用してソフトウェア証明書を作成する
ソフトウェア証明書を登録および更新するには、管理者である必要はありません。また、仮想スマート カードも必要ありません。 ある時点で、証明書操作を許可するように求められますが、これは通常の操作です。

## <a name="create-a-software-certificate-profile-template-in-mim-2016-certificate-manager"></a>MIM 2016 証明書マネージャーでソフトウェア証明書プロファイル テンプレートを作成する

1.  仮想スマート カードに必要な証明書のテンプレートを作成します。 MMC を開きます。

2.  **[ファイル]** メニューの **[スナップインの追加と削除]** をクリックします。

3.  [利用できるスナップイン] の一覧で、**[証明書テンプレート]** をクリックして、**[追加]** をクリックします。

4.  **[証明書テンプレート]** が MMC の [コンソール ルート] に表示されます。 ダブルクリックすると、すべての利用可能な証明書テンプレートが表示されます。

5.  **[ユーザー テンプレート]** を右クリックし、**[テンプレートの複製]** をクリックします。

6.  **[互換性]** タブの [証明機関] の [Windows Server 2008] を選択し、[証明書の受信者] の [Windows 8.1 / Windows Server 2012 R2] を選択します。

    1.  **[全般]** タブの表示名フィールドに「 **アーカイブ済み証明書テンプレート**」と入力します。

    2.  b.    **[要求処理]** タブの操作

        1.  **[目的]** を [署名と暗号化] に設定します。

        2.  **[サブジェクトが許可した対称アルゴリズムを含める]**をオンにします。

        3.  キーをアーカイブする場合は、 **[サブジェクトの暗号化プライベート キーをアーカイブする]**をオンにします。

        4.  以下の操作を行います。 **[登録中にユーザーにメッセージを表示する]**を選択します。

    3.  **[暗号化]** タブの操作

        1.  プロバイダーのカテゴリで **[キー記憶域プロバイダー]**を選択します。

        2.  **[サブジェクトのコンピューターで使用できる任意のプロバイダーを要求に使用できる]**をオンにします。

    4.  **[セキュリティ]** タブで、 **[登録]** アクセス権を付与するセキュリティ グループを追加します。 たとえば、すべてのユーザーにアクセス権を付与する場合は、 **[Authenticated users]** グループを選択し、そのグループに **[登録]** アクセス許可を選択します。

    5.  **[サブジェクト名]** タブの操作

        1.  **[サブジェクト名に電子メール名を含める]** をオフにします。

        2.  **[代わりのサブジェクト名に次の情報を含める]**の **[電子メール名]**をオフにします。

    6.  **[OK]** をクリックして変更を完了し、新しいテンプレートを作成します。 [証明書テンプレート] の一覧に新しいテンプレートが表示されます。

    7.  **[ファイル]** を選択し、**[スナップインの追加と削除]** をクリックして、証明機関スナップインを MMC コンソールに追加します。 管理するコンピューターを尋ねられたら、 **[ローカル コンピューター]**を選択します。

    8.  MMC の左側のウィンドウで **[証明機関 (ローカル)]**を展開し、証明機関の一覧内に自身の CA を展開します。

    9. **[証明書テンプレート]** を右クリックし、**[新規作成]** をクリックして、**[発行する証明書テンプレート]** をクリックします。

    10. 一覧から作成した新しいテンプレート (**アーカイブ済み証明書テンプレート**) を選択し、 **[OK]**をクリックします。

## <a name="create-the-profile-template"></a>プロファイル テンプレートを作成する

1.  管理者特権を持つユーザーとして CM ポータルにログインします。

2.  **[管理] &gt; [プロファイル テンプレートの管理]** を選択し、**MIM CM サンプル スマート カードのログオン プロファイル テンプレート**の横にあるチェック ボックスをオンにして、**[選択したプロファイル テンプレートのコピー]** をクリックします。

3.  プロファイル テンプレートの名前を入力し、 **[OK]**をクリックします。

4.  次の画面で、 **[新しい証明書テンプレートを追加]** をクリックして、CA 名の横にあるチェック ボックスがオンになっていることを確認します。

5.  アーカイブ済みソフトウェア証明書名の横にあるチェック ボックスをオンにして、 **[追加]**をクリックします。

6.  ユーザー テンプレートを削除するには、テンプレートの横にあるチェック ボックスをオンにしてから、 **[選択した証明書テンプレートの削除]** 、 **[OK]**の順にクリックします。

7.  **[全般設定の変更]**をクリックします。

8.  **[サーバーに暗号化キーを生成]** の左にあるチェック ボックスをオンにして、 **[OK]**をクリックします。 左側のウィンドウの **[回復ポリシー]**をクリックします。

9. **[全般設定の変更]**をクリックします。

10. アーカイブされた証明書を再発行する場合は、 **[アーカイブされた証明書の再発行]** の左にあるチェック ボックスをオンにして、 **[OK]**をクリックします。

11. 仮想スマート カード CM を使用している場合、データ収集を使用しないので、データ収集項目を無効にする必要があります。 個々のすべてのポリシーについてデータ収集項目を無効にします。無効にするには、左側のウィンドウでポリシーをクリックしてから、 **[サンプル データ項目]** の横のチェック ボックスをオフにして、 **[データ収集項目の削除]**をクリックします。 **[OK]**をクリックします。
