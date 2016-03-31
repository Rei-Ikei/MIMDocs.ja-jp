---
title: MIM 2016 & #58; をインストールします。MIM サービスおよびポータル |Microsoft Identity Manager
ms.custom:
  - Identity Management
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology:
  - security
ms.tgt_pltfrm: na
ms.topic: get-started-article
author: kgremban
---
# インストールを実行する MIM 2016: MIM サービスおよびポータル

>[! div クラスを「ステップバイ ステップ」=]
[前へ](https://docsmsftstage.azurewebsites.net/MIM/DeployUse/install-mim-sync.html)
**MIM 同期サービスのインストールを実行する MIM 2016:**

> [!NOTE]
> 次に、すべての例で **mimservername** 、ドメイン コント ローラーの名前を表す **contoso** ドメイン名を表すと **Pass@word1** 例パスワードを表します。

最後の手順で、MIM インストール パッケージをセットアップしていない場合は、Microsoft Identity Manager 2016 コンポーネントをインストールする手順に従います。

1. としてサインイン *contoso \administrator* id 管理を使用している CORPIDM サーバーにします。

2. MIM インストール パッケージを展開するか、MIM イメージ DVD をマウントします。

## インストールの MIM サービスおよびポータルを構成します。

1.  実行、 **MIM サービスおよびポータルのインストーラー** から、展開された **サービスおよびポータル** サブフォルダーです。

2.  ウェルカム画面で、 **[次へ]**をクリックします。

3.  使用許諾契約書を読み、ライセンス条項に同意する場合のクリックして **次**します。

4.   **MIM カスタマー エクスペリエンス向上プログラム** 画面で、[ **次**します。

5.  この展開のコンポーネントの機能を選択すると、MIM サービス (MIM Reporting) を除くと MIM ポータル機能が含まれることを確認してください。 MIM パスワード リセット ポータルと MIM パスワード変更通知サービスを選択することもできます。

6.   **MIM データベース接続の構成** ] ページで、指定 **新しいデータベースを作成**します。

    ![MIM データベース接続のイメージを構成します。](media/MIM-Install10.png)

7.   **メール サーバーの接続を構成する**, 、として、Exchange サーバーの名前を入力 **メール サーバー**します。 メール サーバーが構成されていない場合は、メール サーバー名として localhost を指定し、上部の 2 つのチェック ボックスをオフにします。  **[次へ]**をクリックします。

    ![メール サーバーの接続のイメージを構成します。](media/MIM-Install11.png)

8.  新しい自己署名証明書を生成するか、適切な証明書を選択することを指定します。

9. を使用するサービス アカウント名を指定して *MIMService*, 、および例については、サービス アカウントのパスワード *Pass@word1*, 、例については、サービス アカウント ドメイン *contoso* と例については、サービスの電子メール アカウント *contoso*します。

    ![MIM サービス アカウントの画像を構成します。](media/MIM-Install12.png)

10. 現在の構成ではサービス アカウントがセキュリティ保護されていないことを警告するメッセージが表示されます。

11. 同期サーバーの場所の既定値を受け入れ、として MIM 管理エージェント アカウントを指定して *contoso \mimsync*します。

    ![MIM サービスおよびポータルのイメージを構成します。](media/MIM-Install13.png)

12. 指定 *CORPIDM* (このコンピューターの名前)、MIM ポータルの MIM サービス サーバー アドレスとして。

13. 指定 *http://CorpIDM.contoso.local:82* として、SharePoint サイト コレクション URL。

14. 指定 *http://CorpIDM.contoso.local:8080* パスワード登録 URL として。

15. 指定 *http://CorpIDM.contoso.local:8088* パスワードとして URL をリセットします。

16. ファイアウォールのポート 5725 および 5726 を開くためのチェック ボックスをオンにし、さらに、すべての認証されたユーザーに MIM ポータルへのアクセス権を付与するためのチェック ボックスを選択します。

## MIM パスワード登録ポータルの構成] 画面

1.  SSPR 登録のサービス アカウント名を設定 *contoso \mimsspr* とそのパスワードを *Pass@word1*します。

2.  指定  *CORPIDM* MIM パスワード登録のホスト名とポートを設定および **8080**します。 有効にする、 **ファイアウォールでポートを開く** オプション。

    ![IIS のイメージで使用される構成情報を入力してください。](media/MIM-Install14.png)

3.  警告が表示されます。確認して **[次へ]**をクリックします。

4. 次の MIM パスワード登録ポータルの構成画面で指定  *http://CorpIDM.contoso.local* パスワード登録ポータルの MIM サービス サーバーのアドレスにします。

## MIM パスワード リセット ポータルの構成] 画面

1.  SSPR 登録のサービス アカウント名を設定 *Contoso\MIMSSPRService* とそのパスワードを *Pass@word1*します。

2.  指定  *CORPIDM* MIM パスワード登録のホスト名とポートを設定および **8080**します。 有効にする、 **ファイアウォールでポートを開く** オプション。

    ![IIS のイメージで使用される構成情報を入力してください。](media/MIM-Install15.png)

3.  警告が表示されます。確認して **[次へ]**をクリックします。

4. 次の MIM パスワード登録ポータルの構成画面で指定 *CorpIDname http://CorpIDname.domain.local* パスワード リセット ポータルの MIM サービス サーバーのアドレスにします。

## MIM サービスおよびポータルのインストール

すべてのインストール前の定義は、クリックして **インストール** 、選択したインストールを開始する **サービスおよびポータル** コンポーネントです。

![MIM サービスおよびポータルのイメージをインストールします。](media/MIM-Install16.png)

インストールが完了したら、MIM ポータルがアクティブであることを確認します。

1. Internet Explorer を起動し、上の MIM ポータルに接続  *http://corpidm.contoso.local:82 します。*します。 このページに初めてアクセスする場合、少し時間がかかることがあります。

    - 必要に応じて、ユーザーとして認証 *contoso \administrator* Internet Explorer にします。

2. Internet Explorer で、 **[インターネット オプション]**を開き、 **[セキュリティ]** タブに切り替えます。 **[ローカル イントラネット]** ゾーンに該当するサイトがまだ存在しない場合は、そのサイトを追加します。   **[インターネット オプション]** ダイアログを閉じます。

3. MIM でユーザーが独自のエントリを表示できるようにします。

    1.  Internet Explorer を使用し、 **MIM ポータル**で、 **[管理ポリシー規則]**をクリックします。

    2.  管理ポリシー規則の検索 **ユーザーの管理: ユーザーが独自の属性を読み取ることができます**します。

    3.  この管理ポリシー規則を選択して、オフにして **ポリシーが無効になっている**します。

    4.   **[OK]** をクリックし、 **[送信]**をクリックします。

4.  ファイアウォールが TCP ポート 5725 と 5726 との受信接続を許可していることを確認します。

    1.  起動 **管理ツール» Windows ファイアウォール** と **上級セキュリティ**します。

    2.   **[受信の規則]**をクリックします。

    3.  次の 2 つの規則が表示されていることを確認します。

        -   Forefront Identity Manager サービス (STS)。

        -   Forefront Identity Manager サービス (Webservice)。

    4.  ウィザードを完了し、 **Windows ファイアウォール** アプリケーションを閉じます。

    5.  起動 **コントロール パネル-[ネットワークとインターネット» ネットワークの状態とタスクを表示**します。

    6.  ドメイン ネットワークとして contoso.local と表示されたアクティブなネットワークがあることを確認します。

    7.   **[コントロール パネル]**を閉じます。

> [!NOTE]
> 省略可能: この時点でインストールできます MIM アドインおよび拡張機能。

>[! div クラスを「ステップバイ ステップ」=]  
[次へ](https://docsmsftstage.azurewebsites.net/MIM/DeployUse/mim-install-sync-ad-service.html)
**Active Directory と MIM サービスに同期 MIM 2016 をインストールするには。**


<!--HONumber=Mar16_HO3-->

