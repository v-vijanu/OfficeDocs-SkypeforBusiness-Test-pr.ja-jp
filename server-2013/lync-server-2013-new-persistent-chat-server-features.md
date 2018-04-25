﻿---
title: 'Lync Server 2013: 常設チャット サーバーの新機能'
TOCTitle: 常設チャット サーバーの新機能
ms:assetid: c3ec6f33-6261-4bf5-aa31-baa8ab2a87d8
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg412965(v=OCS.15)
ms:contentKeyID: 48273517
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の常設チャット サーバーの新機能

 

_**トピックの最終更新日:** 2016-12-08_

Lync Server 2013、 常設チャット サーバーでは、永続的な、マルチパーティのトピックベースの会話に参加できます。 常設チャット サーバーは、組織で次のことを行う場合に役立ちます。

  - 地理的に分散されたチームや職能上の枠を越えたチーム間でのコミュニケーションを深めます。

  - 情報を広めて参加の輪を広げます。

  - 組織外の人間とのコミュニケーションを深めます。

  - 情報過多を緩和します。

  - 情報の認知を高めます。

  - 重要な知識と情報の分散を促進します。

Lync Server 2013、 常設チャット サーバーは Microsoft Office 365 ではご利用いただけません。現時点では、設置型 Lync 2013 を使用されているお客様のみがご利用いただけます。

Lync 2013、常設チャット機能は Lync 2013 クライアントに統合されています。この結果、ユーザーは、インスタント メッセージング/プレゼンス、音声/ビデオ、常設チャットをすべて Lync 2013 クライアントから利用できます。Lync 2013 クライアントの詳細については、<http://go.microsoft.com/fwlink/p/?linkid=270877> を参照してください。

ここでは、 Lync Server 2013、 常設チャット サーバーの新しいバージョンと以前のバージョン ( Microsoft Lync Server 2010、グループ チャット) の間での機能の変更点について説明します。次のような変更があります。

  - Lync Server コントロール パネルで管理機能が提供され、 グループ チャット管理ツールは使われなくなりました

  - グループ チャット構成ツールは使われなくなり、 常設チャット サーバーの構成設定は トポロジ ビルダーに統合されています

  - 以前のバージョンの 常設チャット サーバーから移行およびアップグレードが容易になっています

  - 高可用性および障害復旧ソリューションが提供されます

最新バージョンの 常設チャット サーバーの詳細については、以下を参照してください。

  - 常設チャットのヘルプ (<http://go.microsoft.com/fwlink/p/?linkid=270945>)。常設チャットの機能の一覧とそのしくみ、および 常設チャット サーバーを実行中の使用方法について説明されています。

  - 「計画」のドキュメントの「[Lync Server 2013 での常設チャット サーバーの計画](lync-server-2013-planning-for-persistent-chat-server.md)」、「展開」のドキュメントの「[Lync Server 2013 での常設チャット サーバーの展開](lync-server-2013-deploying-persistent-chat-server.md)」、「移行」のドキュメントの「[Lync Server 2010、グループ チャットまたは Office Communicatins Server 2007 R2 グループ チャットから Lync Server 2013、常設チャット サーバーへの移行](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)」、および「操作」のドキュメントの「[Lync Server 2013、常設チャット サーバーの管理](managing-lync-server-2013-persistent-chat-server.md)」には、 常設チャット サーバーのセットアップ手順が記載されています。

  - 常設チャット サーバーの Documentation.msi ファイル (Windows インストーラー ファイル) を使用すると、ユーザーは、 常設チャット サーバーに関する包括的なオフライン ドキュメントにアクセスできます。

## 常設チャット サーバー のトポロジに関する重要な変更点

常設チャット サーバーに関する変更点の概要は次のとおりです。

常設チャット サーバーはサーバーの役割になっています。 Microsoft Lync Server 2010 では、 グループ チャット サーバー は Microsoft Lync Server 2010 用の信頼されたサードパーティ アプリケーションでした。 トポロジ ビルダーを使用して、 常設チャットを Lync Server 2013 トポロジに追加することができます。 Lync Server 2013 では、 常設チャット サーバーの機能は 3 つの新しいサーバーの役割を使用して実装されています。

  - **PersistentChatService :** これは、 常設チャットのフロントエンドの役割です。 Standard Edition 展開では、 常設チャット サーバー サービスの役割は、 Lync Server の他のあらゆる役割と同様に、Bootstrapper によって展開された Standard Edition サーバーに共存します。 Enterprise Edition 展開では、 常設チャット サービスの役割は、 Lync Server の他のあらゆる役割と同様に、Bootstrapper によってスタンドアロン コンピューターに展開されます。

  - **PersistentChatStore :** すべてのチャット コンテンツが格納される 常設チャット コンテンツ データベースに対応するバックエンド サーバーです。

  - **PersistentChatComplianceStore :** すべてのコンプライアンス イベントが格納される 常設チャット コンプライアンス データベースに対応するバックエンド サーバーです。

これらの 常設チャット サーバーの役割はオプションであり、 常設チャット サーバーの包括的な機能が必要な場合にのみインストールします。 **PersistentChatComplianceStore** の役割は、 常設チャット コンプライアンスを展開する場合にのみ必要です。

**PersistentChatService** の役割は、次の 2 つのサービスを実行します。

  - 常設チャット サービス

  - 常設チャット コンプライアンス サービス

これらのサービスを各 常設チャット サーバー で実行すると、複数サーバーの 常設チャット サーバー プールでのこれらのサービスによって高可用性が提供されます。

さらに、 常設チャット ルームでのファイルのアップロードとダウンロードをサポートするために、 常設チャット サーバーには Web サービスが含まれています。従来、このサービスは 常設チャット サーバーに共存しており、前提条件として フロント エンド サーバーおよび必要な インターネット インフォメーション サービス (IIS) がインストールされていました。 Lync Server 2013常設チャット サーバーでは、ファイル アップロード/ダウンロード Web サービスは Lync Server 2013フロント エンド サーバーと共存します。そのため、 インターネット インフォメーション サービス (IIS) は 常設チャット サーバーの前提条件ではなくなっています。ファイル アップロード/ダウンロード Web サービスは、 インターネット インフォメーション サービス (IIS) Manager では **PersistentChat**として識別されます。


> [!IMPORTANT]
> <STRONG>PersistentChatService</STRONG> の役割は、 フロント エンド サーバーが Standard Editionフロント エンド サーバーである場合に限り、 Lync Server 2013フロント エンド サーバーと同じサーバー上で実行できます。 <STRONG>PersistentChatService</STRONG> の役割は、 Lync Server 2013フロント エンド サーバーから独立して実行することはできません。 Lync Server 2013 展開に関連する形でのみインストールできます。



常設チャット サーバーでは、参照サービスがなくなっています。 Lync Server 2010、グループ チャット では、すべての グループ チャット サーバーフロント エンド サーバーに参照サービスがあり、チャネル サーバーの 1 つへのルーティングを実行していました。 Lync Server 2013 は連絡先オブジェクトを使用するルーティングに依存しています。各 常設チャット サーバー プールを表す連絡先オブジェクトは、適切な 常設チャット サーバー プールおよびプール内で 常設チャット サーバーを実行しているコンピューターの 1 つを識別して要求をルーティングするために、 Lync Serverフロント エンド サーバーで使用されます。

Lync Server 2013 では、コンプライアンス サービスが変更されています。

  - Lync Server 2010 では、コンプライアンス サービスはスタンドアロン (非共存) であり、1 台のサーバーでだけ実行されていました。新しいコンプライアンス サービスは、すべての常設チャット サーバーフロント エンド サーバーで常設チャット サービスと共に実行され、それによって複数サーバーの常設チャット サーバー プールでの高可用性を提供します。常設チャット サーバーには XML アダプターが付属しています。

  - 各 常設チャット サーバーフロント エンド サーバーにおいて 常設チャット サービスとコンプライアンス サービスが共有するメッセージ キュー (MSMQ とも呼ばれます) は、この 2 つのサービスだけが共有するプライベート キューになりました。すべてのコンプライアンス サービスは、同じコンプライアンス バックエンド データベースに書き込みます。また、すべてのコンプライアンス サービスは、このデータベースからデータを読み取ってアダプターのインスタンスに送信します。コンプライアンス バックエンド サーバーは、新しいバックエンド サーバーの役割として表されます。
    

    > [!IMPORTANT]
    > 以前のバージョンと同様に、すべてのコンプライアンス データは 1 回だけ処理されます。さまざまな Lync Server 2013、 常設チャット サーバー コンピューターで実行されるコンプライアンス サービスによって起動されたアダプター インスタンスのどれでも、データを処理できます。 常設チャット サーバーでは、どのアダプター インスタンスでもデータを処理できます。

    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>メッセージ キューのインストールの詳細については、「展開」のドキュメントの「<a href="lync-server-2013-install-operating-systems-and-prerequisite-software-on-servers.md">Lync Server 2013 のオペレーティング システムと必要なソフトウェアのサーバーへのインストール</a>」を参照してください。</td>
    </tr>
    </tbody>
    </table>


Lync Server 2013 では、高可用性と障害復旧の両方が向上しています。

  - 高可用性の向上: SQL Server のミラーリングを使用して、データ センター内 (サイト内) の 常設チャット サーバー コンテンツ データベースおよび 常設チャット コンプライアンス データベースに対する高可用性が提供されます。

  - 障害復旧の向上: 常設チャット サーバー は、1 つの 常設チャット サーバー プールを 2 つのサイトに拡張できる拡張プール アーキテクチャ (つまり、トポロジ内に 1 つの論理プールがあり、プール内のサーバーは物理的に 2 つのサイトにわたって存在する状態) をサポートします。クロスサイトの障害復旧には SQL Server のログ配布が使用されます。

高可用性および障害復旧の詳細については、「展開」のドキュメントの「[Lync Server 2013 の高可用性と障害復旧に対応した常設チャット サーバーの構成](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)」を参照してください。

## 常設チャット サーバー での管理に関する重要な変更点

Lync Server 2013 では、次のように 常設チャット サーバーの管理が容易になっています。

  - 統合された管理。 Lync Server 2013 では、Lync 管理者であれば使い慣れているツールを使用して 常設チャット サーバーを簡単に管理できます。 常設チャット サーバーでは、管理ユーザー インターフェイス環境が Lync Server コントロール パネルと統合されており、以前のバージョンの グループ チャット サーバー ユーザー インターフェイスにあったパフォーマンスの問題が対処されています。また、 常設チャット サーバーには、 常設チャット サーバーのカテゴリ、 常設チャット サーバー ルーム (ルームおよび古いコンテンツの削除を含みます)、アドインを管理するための、一連の Windows PowerShell コマンドレットが含まれます。

  - 単純化された管理モデル。 Lync Server 2013 では、次の重要な顧客要件に対応することで 常設チャット サーバー モデルが単純化されています。
    
      - スコープとカテゴリの複雑な入れ子階層の除去。
    
      - 現在 MindAlign を使用しており 常設チャット サーバーへの移行を計画しているお客様に対する、拒否リストおよび許可リスト (スコープ) の定義のサポート。

## 以前のバージョンの グループ チャット サーバーでのユーザーの役割との違い

Lync Server 2010、グループ チャット には、ユーザー管理者の役割、チャット ルーム管理者の役割、およびアドインを管理できる Lync Server 管理者の役割がありました。 常設チャット サーバーでは、 常設チャット管理者の役割 ( Lync Server での役割ベースのアクセス制御 (RBAC) の他の役割と類似しています) だけが提供されています。この RBAC の役割のメンバーであるすべてのユーザーは、チャット ルーム、アドイン、およびカテゴリ (それに伴い、これらのカテゴリに対するユーザー アクセス) と、 常設チャット サーバー プールの構成を管理できます。

## 以前のバージョンの グループ チャット サーバーでのチャット ルーム カテゴリとの違い

チャット ルーム カテゴリは入れ子ではなくなり、ルーム カテゴリの変更はできなくなりました。AllowedMembers/DeniedMembers は、従来のバージョンの グループ チャット サーバーでスコープが果たしていた機能を構成します (拒否リストの指定をサポートしていなかった点を除きます)。入れ子になったカテゴリが存在しないため、スコープの上書きはできなくなりました。 Lync Server 2013 の 常設チャット管理者は、チャット ルームのカテゴリを作成して管理できます。チャット ルームのカテゴリの作成および管理の一部として、 常設チャット管理者は、特定のカテゴリのチャット ルームのメンバー/作成者にアクセスできるプリンシパル (Active Directory グループ/コンテナー/ユーザー) を構成できます。また、 常設チャット管理者は、カテゴリに拒否するメンバーを追加し、許可するリストから明示的に除外することもできます。拒否するメンバーは許可するメンバーより優先されます。

## 以前のバージョンの グループ チャット サーバーでのチャット ルーム プロパティとの違い

Lync Server 2013、 常設チャット サーバーには、開いているチャット ルームの新しい概念が存在します。すべての許可するメンバーは、排他的メンバーシップを使用せずにチャット ルームに参加できます。

以前のバージョンの 常設チャット サーバーにあった以下のチャット ルーム プロパティはなくなっています。

  - トピック: ルームに指定できるのは説明のみになります。

  - 新規メンバー リストの作成: 常設チャット サーバーでは、すべてのチャット ルームは空のメンバーシップで開始します (許可するメンバーと同じメンバーシップまで拡大できます)。

  - ファイル アップロード: ファイル アップロード/ダウンロードを許可するかどうかを制御する、チャット ルームごとの設定でした。現在はカテゴリ レベルでのみ設定され、そのカテゴリに属するすべてのルームに適用されます。

  - チャットの履歴: チャットの履歴を有効にするかどうかを制御する、チャット ルームごとの設定でしたが、現在はカテゴリ レベルでのみ設定され、そのカテゴリに属するすべてのルームに適用されます。

  - 招待: ルームは常に、カテゴリに対する設定を継承します。ルームで招待をオフにすることはできます。カテゴリで既に招待がオフに設定されている場合は、ルームで招待をオンにすることはできません。

## 以前のバージョンの グループ チャット サーバーでのポリシーとの違い

常設チャット サーバー では、 常設チャットで有効になった新しい Lync ポリシーがあり、ユーザー/プール/サイト/グローバル設定に従います。 Lync 2013 クライアントでは、 常設チャットのポリシーによって (直接またはプール/サイト/グローバル設定によって) 有効になっているユーザーだけが 常設チャット環境を使用できます。

以前のバージョンの グループ チャット サーバーには、 Lync Server ポリシーに統合されたポリシーはありませんでした。ユーザー単位およびカテゴリ/ルーム単位に、\[**ファイルのアップロードが可能**\] ユーザー単位機能を使用して、ユーザーをユーザー管理者やチャット ルーム管理者にしたり、ユーザーのファイル アップロード機能を構成したりできました。 常設チャット サーバーの \[**ファイルのアップロード**\] 機能は、カテゴリ単位だけです。

## ログ記録

常設チャット サーバーおよび System Center Operations Manager に対するログ記録は、 Lync Server 2013 のトレース ログに統合されています。

## 関連項目

#### その他のリソース

[Lync Server 2013 での常設チャット サーバーの計画](lync-server-2013-planning-for-persistent-chat-server.md)
