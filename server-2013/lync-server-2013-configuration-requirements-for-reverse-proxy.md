﻿---
title: Lync Server 2013 でのリバース プロキシの構成要件
TOCTitle: Lync Server 2013 でのリバース プロキシの構成要件
ms:assetid: c37d688a-28e4-4822-80cc-6add59c71052
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ945651(v=OCS.15)
ms:contentKeyID: 52056700
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 でのリバース プロキシの構成要件

 

_**トピックの最終更新日:** 2013-03-05_

Lync Server 2013 には、外部クライアントからディレクター、ディレクター プール、フロント エンド サーバー、または フロント エンド プールでホストされている外部 Web サービスに渡される通信に関して、いくつかの要件があります。ユーザーに会議機能を提供する場合は、リバース プロキシが Office Web Apps サーバー の公開も担当します。

> [!NOTE]
> Lync Server 2013 では、使用する必要のある特定のリバース プロキシは指定しません。Lync Server 2013 では、リバース プロキシで実行できなければならない操作要件のみを定義します。通常、インフラストラクチャに展開済みのリバース プロキシは、要件を満たしている可能性があります。


## リバース プロキシの要件

Lync Server 2013 がリバース プロキシに期待する機能操作は、次のとおりです。

  - 公的証明機関から取得した証明書を使用して実装された Secure Socket Layer (SSL) およびトランスポート層セキュリティ (TLS) を使用して、ディレクター、ディレクター プール、フロント エンド サーバー、またはフロント エンド プールの公開された外部 Web サービスに接続します。ディレクターおよびフロント エンド サーバーは、ロード バランサー機器を使用して負荷分散されたプールに配置することができます。

  - 内部 Web サイトは、必要に応じて、暗号化用の証明書を使用して公開するか、暗号化されない方法で公開することができます。

  - 完全修飾ドメイン名 (FQDN) を使用して、内部的にホストされている Web サイトを外部に公開することができます。

  - ホストされている Web サイトのすべてのコンテンツを公開することができます。既定では、大部分の Web サーバーに認識される **/\*** ディレクティブを使用することができます。これは "Web サーバーですべてのコンテンツを公開" することを意味します。また、ディレクティブを **/Uwca/\*** のように変更することができます。これは "仮想ディレクトリ Ucwa 下にすべてのコンテンツを公開" することを意味します。

  - 公開された Web サイトのコンテンツを要求するクライアントで Secure Sockets Layer (SSL) 接続またはトランスポート層セキュリティ (TLS) 接続を使用するように構成できる必要があります。

  - サブジェクトの別名 (SAN) エントリを持つ証明書を受け入れる必要があります。

  - 外部 Web サービスの FQDN が解決されるリスナーまたはインターフェイスに対して証明書をバインドできる必要があります。インターフェイスの構成よりリスナーの構成をお勧めします。多くのリスナーは、単一のインターフェイスで構成できます。

  - ホスト ヘッダー処理の構成を許可する必要があります。多くの場合、要求元のクライアントによって送信される元のホスト ヘッダーは、リバース プロキシにより変更されるのではなく、透過的に渡される必要があります。

  - 外部で定義された 1 つのポート (例: TCP 443) から別の定義されたポート (例: TCP 4443) への SSL および TLS トラフィックのブリッジ。リバース プロキシは、受信時にパケットの暗号化を解除し、送信時に再度パケットを暗号化できます。

  - 1 つのポート (例: TCP 80) から別のポート (例: TCP 8080) への暗号化されていない TCP トラフィックのブリッジ。

  - NTLM 認証、認証なし、およびパススルー認証の構成を許可または受け入れます。

