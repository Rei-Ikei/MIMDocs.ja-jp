---
title: "CM REST API サービスの詳細 | Microsoft Docs"
description: 
keywords: 
author: msmbaldwin
ms.author: mbaldwin
manager: mbaldwin
ms.date: 10/17/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 530047f1-e43b-4a69-9542-75bc1da57bf7
audience: developer
ms.reviewer: mwahl
ms.suite: ems
ms.openlocfilehash: 3d724dea8b1536f0155f9fc287d0cd74f5f16b3c
ms.sourcegitcommit: 02fb1274ae0dc11288f8bd9cd4799af144b8feae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2017
---
# <a name="cm-rest-api-service-details"></a>CM REST API サービスの詳細
次のセクションでは、Microsoft Identity Manager (MIM) Certificate Management (CM) REST API の詳細について説明します。

## <a name="architecture"></a>アーキテクチャ 
MIM CM REST API の呼び出しは、コントローラーによって処理されます。 次の表に、コンテキストで使用可能なコントローラーとサンプルのすべての一覧を示します。

コントローラー| サンプル ルート
----------|-------------
CertificateDataController| /api/v1.0/requests/{requestid}/certificatedata /
CertificateRequestGenerationOptionsController| /api/v1.0/requests/{requestid}/certificaterequestgenerationoptions
CertificatesController| /api/v1.0/smartcards/{smartcardid}/certificates <br/> /api/v1.0/profiles/{profileid}/certificates
OperationsController| /api/v1.0/smartcards/{smartcardid}/operations <br/> /api/v1.0/profiles/{profileid}/operations
PoliciesController| /api/v1.0/profiletemplates/{profiletemplateid}/policies/{id}
ProfilesController| /api/v1.0/profiles/{id} <br/> /api/v1.0/Profiles <br/> /api/v1.0/requests/{requestid}/profiles/{id}
ProfileTemplatesController| /api/v1.0/profiletemplates/{id} <br/> /api/v1.0/profiletemplates <br/> /api/v1.0/profiletemplates/{profiletemplateid}/policies/{id}
RequestsController| /api/v1.0/requests/{id} <br/> /api/v1.0/requests
SmartcardsController| /api/v1.0/requests/{requestid}/smartcards/{id}/diversifiedkey <br/> /api/v1.0/requests/{requestid}/smartcards/{id}/serverproposedpin <br/> /api/v1.0/requests/{requestid}/smartcards/{id}/authenticationresponse <br/> /api/v1.0/requests/{requestid}/smartcards/{id} <br/> /api/v1.0/smartcards/{id} <br/> /api/v1.0/smartcards
SmartcardsConfigurationController| /api/v1.0/profiletemplates/{profiletemplateid}/configuration/smartcards
<br/>

## <a name="http-request-and-response-headers"></a>HTTP 要求および応答ヘッダー

API に送信された HTTP 要求には、次のヘッダーを含める必要があります (このリストは完全ではありません)。

ヘッダー | 説明
-------|------------
承認 | 必須。 コンテンツは認証方法に依存します。認証方法は構成可能で、WIA (Windows 統合認証) または ADFS に基づくことができます。
Content-Type | 要求本文が含まれる場合は必須。 "application/json" である必要があります。
Content-Length | 要求本文が含まれる場合は必須。 
Cookie | セッションの Cookie。 認証方法によって必要な場合があります。
<br/>
HTTP 応答には、次のヘッダーが含まれます (このリストは完全ではありません)。

Header | 説明
-------|------------
Content-Type | この API は、常に "application/json" を返します。
Content-Length | 要求本文がある場合は、その長さ (バイト)。


## <a name="api-versioning"></a>API のバージョン管理 
CM REST API の現在のバージョンは 1.0 です。 バージョンは、URI: `/api/v1.0` の `/api` セグメントのすぐ後ろのセグメントで指定されています。 将来、API インターフェイスに大きな変更があった場合には、バージョン番号が変更になります。


## <a name="enabling-the-api"></a>API の有効化 
Web.config ファイルの `<ClmConfiguration>` セクションは、次の新しいキーで拡張されています。

```
<add key="Clm.WebApi.Enabled" value="false" />
```
<br/>

このキーは、CM REST API がクライアントに公開されているかどうかを判断します。 キーが "false" に設定されていると、アプリケーションの起動時に、API のルート マッピングが実行されません。 これは、API エンドポイントへの後続の要求で HTTP 404 エラー コードが返されることを意味します。 既定ではキーは「無効」に設定されています。
この値を "true" に変更した後に、忘れずにサーバーで **iisreset** を実行します。

## <a name="enabling-tracing-and-logging"></a>トレースとログ記録の有効化 
MIM CM REST API では、受信した各 HTTP 要求のトレース データを出力します。 次の構成値を設定することで、出力されるトレース情報の詳細レベルを設定することができます。

```
<add name="Microsoft.Clm.Web.API" value="0" />
```
<br/>

## <a name="error-handling-and-troubleshooting"></a>エラー処理とトラブルシューティング 
要求の処理中に例外が発生すると、MIM CM REST API は、HTTP 状態コードを Web クライアントに返します。 一般的なエラーの場合、API は該当する HTTP 状態コードとエラー コードを返します。 

未処理の例外は、HTTP 状態コード 500 (「内部エラー」) の `HttpResponseException` に変換され、イベント ログと MIM CM のトレース ファイルの両方にトレースされます。 未処理の例外はそれぞれ、対応する関連付け ID を持つイベント ログに書き込まれます。 関連付け ID は、エラー メッセージで API のコンシューマーにも送信されます。 エラーのトラブルシューティングを行うため、管理者は対応する関連付け ID でイベント ログを検索して、エラーの詳細を確認できます。

セキュリティ上の問題により、MIM CM REST API を使用した結果として生成されたエラーに対応するスタック トレースは、クライアントに送信されません。
