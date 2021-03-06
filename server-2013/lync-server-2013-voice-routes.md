﻿---
title: 'Lync Server 2013: 音声ルート'
TOCTitle: 音声ルート
ms:assetid: a2ddf327-2ec4-407b-af0f-276f2b13eefd
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg412757(v=OCS.15)
ms:contentKeyID: 48273147
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の音声ルート

 

_**トピックの最終更新日:** 2012-10-22_

通話ルートは、 エンタープライズ VoIP ユーザーが発信する通話を、 Lync Server がどのように処理するかを指定します。ユーザーが電話をかけると、 フロント エンド サーバーは必要に応じて、ダイヤル文字列を E.164 形式に正規化し、一致する SIP URI があるかどうかを調べます。一致する SIP URI が見つからない場合は、番号に基づいて発信通話ルーティング ロジックが適用されます。発信通話ルーティング ロジックを定義する最後のステップでは、ダイヤル プランごとの各相手電話番号に対して、個別の名前が付けられた通話ルートが作成されます。

発信通話ルートを定義する前に、次のステップを実行しておく必要があります。

  - 1 つ以上のトランクの展開

  - 必要に応じた、場所、個々のユーザー、および連絡先オブジェクトに対するダイヤル プランの作成

  - 公衆交換電話網 (PSTN) の使用法レコードの作成

さらに、発信通話ルーティングを有効にするには、1 つ以上の音声ポリシーを作成して割り当てる必要があります。このステップは、発信通話ルートを定義する前および定義した後のどちらでも実行できます。

各ルートごとに、次の項目を指定する必要があります。

  - 簡単に識別できる名前

  - オプションの説明 (名前だけではルートの内容を十分に説明できない場合に使用)

  - ルートを適用する対象となる、相手電話番号を識別する正規表現による一致パターンと、一致パターンを適用させない例外

  - ルートに割り当てる 1 つ以上のトランク

  - 相手電話番号の正規表現に一致する電話番号を発信するために、ユーザーに必要な PSTN 使用法レコード

通話ルートは、 Lync Server コントロール パネルで指定することができます。これらの通話ルートはサーバーのルーティング テーブルに設定され、 Lync Server はそれを使用して PSTN 宛ての通話をルーティングします。

## M:N トランクのサポート

Lync Server では、通話を PSTN にルーティングする方法を柔軟に制御できます。ボイス ルートは、特定の音声通話に対して使用できる PSTN へのトランクのセットを指定します。トランクは、 仲介サーバーとポート番号を PSTN ゲートウェイとリッスン ポート番号に関連付けます。この論理的な関連付けにより、 仲介サーバーに複数のゲートウェイを関連付けたり、同じゲートウェイへの複数の接続を割り当てたりすることができます。通話ルートを定義するときには、そのルートに関連するトランクを指定しますが、どの 仲介サーバーがそのルートと関連するかについては指定しません。 仲介サーバーと PSTN ゲートウェイ、IP-PBX、およびセッション ボーダー コントローラー (SBC) との関係を定義してトランクを作成するには、 トポロジ ビルダーを使用します。

## 最小コスト ルーティング

さまざまな番号のルーティング先であるトランクを指定する機能を使用すると、コストが最も低くなるルートを判断し、それに従ってルーティングできます。この機能は、長距離通話料金を最も少なくするために、宛先の番号の場所に最も近いゲートウェイを含むトランク選択して指定します。たとえば、ニューヨークからローマの番号に発信する場合に、ローマの事務所のゲートウェイを含むトランクまで IP ネットワークを介して通話を中継すると、支払いが必要になるのは市内通話料金だけになります。

最小コスト ルーティングの使用例としては、次のような状況を想定してください。Fabrikam は、ドイツのユーザーが米国のトランクを使用して米国の番号をダイヤルできるようにすることを決定しました。また、Fabrikam は、米国の Lync Server ユーザーからドイツおよび隣接する国/地域へのすべての通話がドイツのゲートウェイを含むトランクで終了するように、システムを構成しようとしています。このルーティングを使用すると、たとえば、ドイツからオーストリアへの通話は米国からオーストリアへの通話より安価なので、費用を節約できます。

## 発信ダイヤル文字列の変換

Lync Server 2013 では、直前モデルと同様に、逆引き番号検索 (RNL) を実行するためにすべてのダイヤル文字列を正規化して E.164 形式にする必要があります。 Lync Server 2013 では、地域のダイヤル形式に変換された番号を必要とするゲートウェイまたは構内交換機 (PBX) を含むトランクのために、着信電話番号 (要求 URI) をトランクにルーティングする前に操作するのに役立つ複数のルールを作成できます。たとえば、+44 をダイヤル文字列の先頭から削除し、0144 に置き換えるルールを作成できます。

Lync Server 2013 では、発信電話番号をトランクにルーティングする前に操作するのに役立つ複数のルールを作成できます。

ゲートウェイとポートのペアを 仲介サーバーとポートのペアに関連付けるトランクについて計画する際に、必要な変換ルールの数を減らして変換ルールの書き込みにかかる時間を短縮するように、類似した地域のダイヤル要件を持つトランクをグループ化すると役立つ場合があります。

## 発信者番号の構成

Lync Server を使用して、発信通話の発信者番号を操作することができます。たとえば、組織が従業員の直通内線番号を隠し、会社や部門の一般的な電話番号に置き換える場合、管理者は Lync Server コントロール パネルを使用して、実際の発信者番号ではなく、指定した別の発信者番号が表示されるようにすることができます。ルーティング ロジックを計画する際は、このオプションが特定の個人、グループ、場所、またはすべての従業員に必要かどうかを検討します。

> [!NOTE]
> PSTN を介して再ルーティングされる通話の場合、元の発信者番号ではなく、一般的な発信者番号が表示されます。これにより、通話の呼び出し先が構成した応答不可設定またはプライバシー設定がバイパスされる場合があります。


## その他のルーティング ロジック

発信通話ルートを作成する際には、以下の要因がルーティング ロジックに作用することを認識しておく必要があります。

  - フェデレーションの境界を越えて通話が確立される場合、URI のドメイン部分を使用して、発信ルーティング ロジックの適用を行うエンタープライズに通話をルーティングします。

  - 要求 URI のドメイン部分にエンタープライズでサポートされているドメインが含まれていない場合、サーバーの発信ルーティング コンポーネントは通話の処理を行いません。

  - エンタープライズ VoIP に対してユーザーが有効化されていない場合、サーバーは、状況に応じて他のルーティング ロジックを適用します。

  - 空き回線のないゲートウェイ (すべてのトランク回線が使用中) に通話がルーティングされると、ゲートウェイによって通話が拒否されるため、発信ルーティング コンポーネントは次にコストの低いルートに通話をリダイレクトします。海外の小規模な支店 (たとえば、チューリヒ) に合わせて構成された小規模なゲートウェイが、実際にはスイス宛ての大量の国際通話を処理するような場合があるため、ルーティングには詳細な配慮が必要です。このような追加トラフィックに対応できるようにゲートウェイのサイズを適正に構成していない場合は、スイス宛ての通話がドイツにあるゲートウェイを経由してルーティングされ、多額の通話料金が発生する可能性があります。

