﻿---
title: 'Lync Server 2013: パブリック インスタント メッセージング接続の設定'
TOCTitle: パブリック インスタント メッセージング接続の設定
ms:assetid: 816dea2a-96fa-4a36-b6c2-a9402675868b
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ205041(v=OCS.15)
ms:contentKeyID: 48272685
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 でのパブリック インスタント メッセージング接続の設定

 

_**トピックの最終更新日:** 2012-09-08_

組織で AOL とのパブリック インスタント メッセージング (IM) 接続をサポートする必要がある場合は、Lync Server 展開ウィザードを使用して証明書を要求することはできません。代わりに、以下の手順を実行します。

## パブリック インスタント メッセージング接続の設定

1.  フロントエンド サーバーでトポロジ ビルダーを開きます。エッジ プールを展開し、エッジ サーバーまたはエッジ サーバー プールを右クリックします。\[プロパティの編集\] をクリックします。

2.  \[全般\] の下の \[プロパティの編集\] で、\[このエッジ プールのフェデレーションの有効化 (ポート 5061)\] を選択します。\[OK\] をクリックします。

3.  \[アクション\] をクリックし、\[トポロジ\]、\[公開\] の順にクリックします。トポロジの公開を確認するプロンプトが表示されたら、\[次へ\] をクリックします。公開が完了したら、\[完了\] をクリックします。

4.  エッジ サーバーで、Lync Server 展開ウィザードを開きます。\[Lync Server システムのインストールまたは更新\] をクリックして、\[Lync Server コンポーネントのセットアップまたは削除\] をクリックします。\[再実行\] をクリックします。

5.  \[Lync Server コンポーネントのセットアップ\] で、\[次へ\] をクリックします。概要画面に、実行された処理が表示されます。展開が完了したら、\[ログの表示\] をクリックして、利用可能なログ ファイルを表示します。\[完了\] をクリックして、展開を完了します。

## AOL とのパブリック IM 接続をサポートするために、エッジ サーバーの外部インターフェイス用に証明書要求を作成するには

1.  必要なテンプレートが CA で利用できる場合、エッジ サーバーで次の Windows PowerShell コマンドレットを使用して証明書を要求します。
    
        Request-CsCertificate -New -Type AccessEdgeExternal  -Output C:\ <certfilename.txt or certfilename.csr>  -ClientEku $true -Template <template name>
    
    Lync Server 用に使用されるテンプレートの既定の証明書名は、Web サーバーです。既定のテンプレートとは異なるテンプレートを使用する必要がある場合は、\<テンプレート名\> のみ指定します。
    

    > [!IMPORTANT]
    > 組織で AOL とのパブリック インスタント メッセージング (IM) 接続をサポートする必要がある場合、証明書ウィザードの代わりに Windows PowerShell を使用して、アクセス エッジ サービスの外部エッジに割り当てる証明書を要求します。これは、証明書を要求するために証明書ウィザードが使用する証明機関 (CA) Web サーバー テンプレートが、クライアント EKU 構成をサポートしていないためです。Windows PowerShell を使用して証明書を作成する前に、CA 管理者はクライアント EKU をサポートする新しいテンプレートを作成して展開する必要があります。


