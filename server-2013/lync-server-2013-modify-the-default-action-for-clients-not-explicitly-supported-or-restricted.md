﻿---
title: サポートまたは制限が明示的に設定されていないクライアントの既定のアクションの変更
TOCTitle: サポートまたは制限が明示的に設定されていないクライアントの既定のアクションの変更
ms:assetid: 548dd0f5-62fe-4c3f-8952-2b9fd4c5fff3
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg520994(v=OCS.15)
ms:contentKeyID: 48272118
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# サポートまたは制限が明示的に設定されていないクライアントの既定のアクションの変更

 

_**トピックの最終更新日:** 2013-02-23_

Lync Server 2013 環境でサポートするクライアントのバージョンのほか、バージョン ポリシーが定義されていないクライアントに対する既定のアクションも指定できます。これにより、Lync Server 環境で使用するクライアント バージョンを制限できるため、複数のクライアント バージョンをサポートすることで発生するコストを抑えることができます。

## 明示的にサポートまたは制限されていないクライアントの既定のアクションを変更するには

1.  CsUserAdministrator または CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**クライアント**\] をクリックし、\[**クライアント バージョン構成**\] をクリックします。

4.  \[**クライアント バージョン構成**\] ページで、リスト内の \[**グローバル**\] 構成をダブルクリックします。

5.  \[**クライアント バージョン構成の編集**\] ダイアログ ボックスで \[**バージョン管理を有効にする**\] チェック ボックスがオンになっていることを確認し、\[**既定のアクション**\] で次のいずれかを選択します。
    
      - \[**許可**\]   クライアント バージョンが \[**クライアント バージョン ポリシー**\] リスト内のフィルターと一致しない場合に、クライアントのログオンを許可します。
    
      - \[**禁止**\]   クライアント バージョンが \[**クライアント バージョン ポリシー**\] リスト内のフィルターと一致しない場合に、クライアントのログオンを禁止します。
    
      - \[**禁止して URL を表示**\]   クライアント バージョンが \[**クライアント バージョン ポリシー**\] リスト内のフィルターと一致しない場合にクライアントのログオンを禁止し、新しいクライアントをダウンロードできる URL を含むエラー メッセージを表示します。
    
      - \[**許可して URL を表示**\]   クライアント バージョンが \[**クライアント バージョン ポリシー**\] リスト内のフィルターと一致しない場合にクライアントのログオンを許可し、新しいクライアントをダウンロードできる URL を含むエラー メッセージを表示します。

6.  \[**禁止して URL を表示**\] を選択した場合は、エラー メッセージに含めるクライアントのダウンロード用 URL を \[**URL**\] ボックスに入力します。

7.  \[**確定**\] をクリックします。

## クライアント バージョン管理を無効にするには

  - バージョン管理を無効にしてすべてのクライアントがクライアント バージョンに関係なくログオンできるようにするには、\[**バージョン管理を有効にする**\] をオフにして \[**確定**\] をクリックします。

## Lync Server PowerShell コマンドレットを使用した既定のアクションの変更

クライアント バージョン ポリシーによって明示的にサポートまたは制限されていないクライアントを使用してユーザーがサインオンしようとしたときに実行される既定のアクションは、Windows PowerShell コマンドライン インターフェイスと **Set-CsClientVersionPolicy** コマンドレットを使用して管理することもできます。このコマンドレットは、Lync Server 2013 管理シェルから実行することも、Windows PowerShell のリモート セッションから実行することもできます。リモートの Windows PowerShell を使用して Lync Server に接続する方法の詳細については、Lync Server Windows PowerShell のブログ記事「Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell」 ([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876)) を参照してください。

## アクセスを禁止するように既定のアクションを構成する

  - 次のコマンドでは、Redmond サイトの既定のアクションを "Block" に設定します。これにより、クライアント バージョン構成ルールが存在しないクライアントの登録が禁止されます。
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Block

## アクセスを許可するように既定のアクションを構成する

  - この例では、Redmond サイトの既定のアクションが "Allow" に設定されています。これにより、クライアント バージョン構成ルールが存在しないクライアントの登録が許可されます。
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Allow

詳細については、[Set-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientVersionPolicy) コマンドレットに関するヘルプ トピックを参照してください。

## 関連項目

#### その他のリソース

[Lync Server 2013 でのデバイス、電話、クライアント アプリケーションの管理](lync-server-2013-managing-devices-phones-and-client-applications.md)

