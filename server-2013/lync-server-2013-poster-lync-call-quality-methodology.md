﻿---
title: Lync Call Quality Methodology (通話の品質保証の方法論)
TOCTitle: 'ポスター: Lync Call Quality Methodology (通話の品質保証の方法論)'
ms:assetid: a069f4e5-4f80-4f0f-8657-2e07276b6b41
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn593600(v=OCS.15)
ms:contentKeyID: 61084847
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Call Quality Methodology (通話の品質保証の方法論)

 

_**トピックの最終更新日:** 2016-12-08_

この記事は、ダウンロード センターから提供されている「[Lync Call Quality Methodology](http://go.microsoft.com/fwlink/?linkid=391841)」のポスターと併せてご覧ください。

![CQM プロセスの説明ポスター](images/Dn594589.d239e04a-1c3b-4f0e-93af-88b85198615a(OCS.15).jpg "CQM プロセスの説明ポスター")

このポスターは、Lync 2013 および 2010 の CQM (Call Quality Methodology) について説明しています。これは、エンタープライズ VoIP 機能を含む Lync 実装の通話品質とユーザー エクスペリエンスに影響する問題を見つけて解消するために役立ちます。Call Quality Methodology (通話の品質保証の方法論) は、新しいトラブルシューティングとサービス管理のフレームワークで、Lync のエンタープライズ VoIP サービスの改善に集中したものです。この記事では、CQM、監視対象になるサーバーとソリューションの種類、および収集されたテレメトリ データの処理方法について詳しく説明します。

CQM の使用方法について疑問がある場合は、cqmfeedback@microsoft.com までご連絡ください。

このポスターは、次の領域について説明しています。

  - Lync CQM とは

  - 優先度設定: 傾向把握クエリの実行

  - PCD

  - 管理対象/非管理対象

  - Server Plant Road

  - Last Mile Road

  - End Points Road

  - サービス管理

  - ボード ゲームの規則

## Lync CQM とは

Call Quality Methodology (通話の品質保証の方法論) は、新しいトラブルシューティングとサービス管理のフレームワークで、Lync のエンタープライズ VoIP サービスの改善に集中したものです。CQM を使用すると、少ない労力で通話の品質が保証され、エンタープライズ VoIP に対するユーザーの満足が得られます。CQM について詳しくは、「[Lync Server Networking Guide](http://go.microsoft.com/fwlink/p/?linkid=390677)」をご覧ください。その内容を要約したものが、この記事とポスターです。

CQM は、システムのトラブルシューティングを 3 つの道筋 (Road) に分解します。それらは、Server Plant Road (サーバーとサーバー間のリンクに注目します)、End Points Road (通話に使用されるユーザー デバイスとメディアに注目します)、Last Mile Road (従来の交換電話網による通話との統合に対応します) です。

それぞれの道筋は、特定の領域やトピックに関連するいくつかのセグメントに分割されます。各セグメントでは、受け入れ可能な品質レベルについて定義され、その品質レベルを達成するためのアクションが実行され、その品質レベルを保持するためにサービス管理プランが設定されてから、次のトピックに移行します。

ポスターは、Lync CQM を 3 人のプレーヤーがそれぞれ別の道筋 (Road) を進むボード ゲームとして表しています。ダウンロードに含まれているカードは、通話の品質を確保するために対処する必要がある障害を模しています。目標に関するヒントと提案、およびそれを達成する方法は、3 つの道筋の横に示され、実際に適用するときに最初にどの道筋を追及するかの優先度設定のガイドラインもあります (ゲームでは、3 つの道筋すべてを並行して進めます)。

以前のバージョンの Lync では、CQM はどのように動作していたのでしょうか。CQM は Lync 2013 の新機能ですが、その大部分は Lync 2010 でも使用できるようになっています。CQM はある程度までは Microsoft Office Communicator でも動作しますが、これはテストもサポートもされていません。

CQM の使用方法について疑問がある場合は、cqmfeedback@microsoft.com までご連絡ください。

## 優先度設定: 傾向把握クエリの実行

CQM の最初の手順は、2 週間にわたって傾向を把握するための各クエリを実行して、その結果を分析することです。最大のストリーム投稿者、最大の不良ストリーム率、およびマネージ領域 (制御可能な領域) の順に、対策アクションの優先度を設定します。音声ビデオ Multipoint Control Unit (AV MCU) または仲介クエリの結果が基準以下の場合は、赤 (Server Plant Road) の道筋を開始します。有線またはワイヤレスのクエリの結果が基準以下の場合は、青 (Last Mile Road) の道筋を開始します。VPN または外部クエリの結果が基準以下の場合は、緑 (End Points Road) の道筋を開始します。

開始する道筋を選んだら、それぞれの領域の目標を定義し (Assert)、その目標を達成するために作業し (Achieve)、目標を維持し続ける手順を実装します (Maintain)。また、このポスターをゲームとして使用すると、CQM の背後にある原理を理解できるようになります。

## PCD

PreCall Diagnostics ツール (PCD) を使用すると、境界ネットワークの問題を特定して診断し (QoE データベースはエッジまたは境界ネットワークの情報を収集しません)、Last Mile の接続をトラブルシューティングできます。このツールは、Windows 8 Modern アプリまたは Windows デスクトップ アプリとして、http://apps.microsoft.com/windows/en-us/app/lync-2013-precall-diagnostics/9607fe33-2b51-403d-9615-c23f248e7c88 で提供されています。

## 管理対象/非管理対象

Lync Server 展開とネットワーク インフラストラクチャは、通常は管理対象空間と非管理対象空間に分けられます。管理対象空間には、内部の有線ネットワークおよびサーバー インフラストラクチャの全体が含まれます。非管理対象空間は、ワイヤレス インフラストラクチャおよび外部ネットワーク インフラストラクチャです。

この区別によって、データがいっそう明確になり、ユーザーの音声とビデオの品質に影響するような測定可能な負荷に対して組織が集中できるようになります。所有するインフラストラクチャ (管理対象) で通話が発生した場合と他者の管理下にあるインフラストラクチャ (非管理対象) で発生した場合に、品質に対するユーザーの期待は異なります。言うまでもなく、ワイヤレス ユーザーの手元には、優れた Lync Server エクスペリエンスがインストールされた自分のデバイスが残ります。

非管理対象空間で音声品質を改善するには、管理対象空間で高い品質を保つ必要があります。ワイヤレス (Wi-Fi) は、組織によって管理対象と非管理対象のどちらかにみなされます。正常な環境を達成する技術とソリューションは、2 つの空間で異なります。

## Server Plant Road

Server Plant Road のセグメント 1 は、Lync 実装の実サーバーに対応します。サーバー自体とそのサーバーの実装内のロールに関連する KHI データを収集し、その結果を分析します。アクションが保障されている場合は、見つかった問題をすべて訂正します。このトピックに関して詳しくは、KHI ポスターに伴う「[主要状態インジケーター](lync-server-2013-poster-key-health-indicators.md)」の記事をご覧ください。

2 つ目のセグメントは、AV MCU サーバーと仲介サーバーの間のメディア ストリームに対応します。最初に、不良ストリームしきい値の目標を確認します。不良ストリームとは、通常は PacketLossRate \> .01 または PacketLossRateMax \> .05 です。別の必要な目標は、PoorStreamsRatio \< 2% です。次に、詳細なクエリを使用して、ストリーム不良の AVMCU と仲介サーバーのペアを見つけて、ストリーム不良の原因を調査し、不良ストリーム パスのネットワーク装置を確認し、不良ストリームを修復し、ネットワーク装置に対して最適の (「金の」) 構成を定義します。その結果を保持するために、構成の誤差を管理して新しい問題の領域を報告するプロセスとツールを実装します。

次に、仲介サーバーと公衆交換電話網 (PSTN) ゲートウェイの間のメディア ストリームを確認します。最初に、不良ストリームしきい値の目標を確認します。不良ストリームとは、通常は PacketLossRate \> .01 または PacketLossRateMax \> .05 です。次に、詳細なクエリを使用して、ストリーム不良の仲介サーバーとゲートウェイのペアを見つけて、ストリーム不良の原因を調査し、不良ストリーム パスのネットワーク装置を確認し、不良ストリームを修復し、ネットワーク装置に対して最適の (「金の」) 構成を定義します。次に、詳細なクエリを使用して、ストリーム不良の AVMCU と仲介サーバーのペアを見つけて、ストリーム不良の原因を調査し、不良ストリーム パスのネットワーク装置を確認し、不良ストリームを修復し、ネットワーク装置に対して最適の (「金の」) 構成を定義します。

最後に、PSTN ゲートウェイの正常性指標を確認します。正常性を示す統計を識別し、それに対する目標を定義します。多くの種類のゲートウェイが使用されるため、ここでは特にその方法については示しません。目標を確立したら、その目標を達成するために、必要に応じて修復します。そのプロセスで、ゲートウェイに最適の (「金の」) 構成を定義します。その結果を保持するために、構成の誤差を管理して新しい問題の領域を報告するプロセスとツールを実装します。ファームウェアとソフトウェアのアップデートによって、構成が変更されたり、「金の」構成の定義を変更することになることがあります。これらのアクティビティは慎重に実行してください。

## Last Mile Road

クライアントがネットワークに接続する方法は 2 つありますが、有線のほうが高い品質を期待されているため、Last Mile の問題ではこちらにまず焦点が当てられます。CQM の有線クエリ (LastMile\_0\_Wired) とそれによる不良ストリーム率のデータを使用します (ストリーム数 \> 300 のサイトでは PoorStreamsRatio \< 5% を目標として定義することをお勧めします)。この目標を達成するために、最低ランクのサブネットから最高ランクまで順に修復し、QoS を実装します。

有線接続の品質を最適化した後は、ワイヤレスの品質を向上させることが容易になります。ワイヤレス インフラストラクチャは、それぞれの場所で有線接続の上部構造になっているからです。有線の品質に問題がないサイトでワイヤレス ストリームが不良の場合は、特定のワイヤレス コンポーネントに問題があります。ある日付範囲で CQM のワイヤレス クエリ (LastMile\_1\_Wireless) を操作すると、その環境のすべての内部ワイヤレス ストリーム (Lync クライアントと会議サーバーまたは仲介サーバーの間でやり取りされた) が返されます (ストリーム数 \> 300 のサイトでは PoorStreamsRatio \< 5% を目標として定義することをお勧めします)。 この目標を達成するために、最低ランクのサブネットから最高ランクまで順に修復し、QoS を実装します。

## End Points Road

最初に、Lync で使用するときに許容される品質が提供されることがわかっているデバイス (ヘッドセットなど) について、End Points Road の検査をします (ストリーム数が 100 を超える実装では AvgSendListen MOS \> 3.6 を目標とすることをお勧めします。) この目標を達成するために、問題があるデバイスを特定して、それを修復または交換します。

次に、エンド ユーザーの通話で音声を処理するデバイスまたは PC を検査します。お勧めする目標品質の指標は、 AudioMic GlitchRate \> 1 です。ユーザーのシステムに対する最適のシステム構成を特定して、ドライバーのバージョンも含めた「金の」 PC 構成を定義します。

音声ストリームが Lync エンドポイント システムから通過するネットワーク パスが音声品質不良の原因になることがあるため、これを検査します。音声が VPN 接続を経由する場合は、遅延の問題が見つかることがあります。内部 Lync クライアントが他の内部 Lync クライアントとの間の 2 者間通話またはピアツーピア通話で直接メディア ストリームを確立できない場合は、Lync エッジ サーバーをリレーするパスにフォール バックされるため、再び、遅延の問題が起きたり、損失やジッターの可能性が高まります。品質指標の Media over VPN は 0% に定義することをお勧めします。設定した目標を達成するために修復したら、問題があるサブネットを特定してファイアウォール規則、パケット シェイパー、その他の関連するネットワーク装置の構成を検証してください。

IP パケットは、伝送制御プロトコル (TCP) またはユーザー データグラム プロトコル (UDP) のどちらかを使えます。TCP はデータ ストリームに最適です。UDP は接続がなく、メディアにとって効率的です (TCP の復旧メカニズムはリアルタイム メディアの損失には対応しないため)。Lync は常に UDP を選びますが、UDP セッションを確立できない場合は TCP を使います。TCP 経由のメディア セッションは UDP 経由の場合より品質が劣ります。品質の定義では TCP 経由接続を 0% にすることをお勧めします。設定した目標を達成するために修復したら、問題があるサブネットを特定してファイアウォール規則、パケット シェイパー、その他の関連するネットワーク装置の構成を検証してください。

## サービス管理

サービス管理は CQM の最終的な状態で、3 つの道筋すべての目的地です。通話の品質を高いレベルで保持するには、次の領域を監視します。

1.  **ユーザー** - 修復アクティビティによって、ユーザーの満足度がはっきりと上がります。このことは、問題チケットや他のフィードバック方法によって計測されます。品質指標を公開することもできます。

2.  **手順** - CQM を運用するための日次、週次、および月次の手順を定義します。監視のサイクルは最初は高頻度 (毎日) で修復と並行しますが、次第に頻度が下がって (毎月) 修復作業も落ち着いていきます。

3.  **ツール** - 測定と修復のツールを特定します。CQM クエリを自動的に実行して手順をサポートするツールが使いやすいでしょう。修復には、他のツール (たとえばネットワーク要素で構成を標準化したり不良ストリームの損失をトラブルシューティングする) が必要になることもあります。

## ボード ゲームの規則

このポスターは、CQM 実装のリファレンスとして、またはゲームを通して概念を身に付けるために使えます。ゲームとして使うには、6 面のさいころが 1 個と提供されるカード (ダウンロードした場合は Avery 5871 名刺作成用シートに印刷できます) が必要になります。

ゲームは 3 人でプレイします。プレーヤーは 3 つの道筋 (Server Plant、End Point、Last Mile) を使って必要な品質を達成し、中央の "サービス管理" 状態に到達します。それぞれの道に沿っていくつか停止位置があり、そこで品質目標の定義 (Assert)、目標の達成 (Achieve)、システムの状態の維持 (Maintain) の操作をします。すべてのカードを上の指定された場所に置き、5 枚のカードを引きます。引いたカードを確認してそれらをボードの関連するセグメントに置きます。各プレーヤーが、毎回それぞれの道筋を通してカードを移動しながら、品質目標を定義し、目標を達成し、サービス レベルを維持します。すべてのプレーヤーが中央の "サービス管理" 状態に到達すると、ゲームが終了します。詳しい規則は、ダウンロードされたゲーム カードとともに提供されます。

品質目標を定義 **Assert** するには、その目標に適用されるパラメーターを確認し、それを受け入れるかどうかを皆に聞こえるように宣言します。既にお勧めした開始ポイントがありますが、最終的には自分で宣言する必要があります。例外は KHI データで、この場合は Microsoft が確立した規格を使用する必要があります。併せて KHI のポスターもご覧ください。

ゲームで目標を達成 **Achieve** するには、提供されたカードを KHI データやシステム クエリの代わりに使います。ゲームの開始時に引いたカードが指定された分野に関係ない場合は、パスを続けます。関連するカードがある場合は、さいころを転がします。カードに示された数字より小さい目が出た場合は成功です。カードの数字と同じかより大きい目が出た場合は、別のカードを引きます。カードによって、2 人以上のプレーヤーがさいころを振る必要があると示された場合は、全員がさいころを振って成功する必要があります。

ゲームでシステムを維持 **Maintain** するには、Lync 環境での担当分野 (ゲームでの) に関するサービス管理プランを皆に聞こえるように宣言します。

## 関連項目

#### その他のリソース

[Lync Server Networking Guide](http://go.microsoft.com/fwlink/p/?linkid=390677)  
[主要状態インジケーター: Lync Server の正常性を維持する基盤 (Key Health Indicators: The Foundation for Maintaining Healthy Lync Servers)](http://go.microsoft.com/fwlink/?linkid=391838)  
[Lync Call Quality Methodology (通話の品質保証の方法論)](http://go.microsoft.com/fwlink/?linkid=391841)
