﻿---
title: Lync Server 2013 を使用した大規模会議のサポート
TOCTitle: Lync Server 2013 を使用した大規模会議のサポート
ms:assetid: 509a424f-a33d-4e72-8f87-a3ec7bb1ddeb
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204894(v=OCS.15)
ms:contentKeyID: 48272075
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 を使用した大規模会議のサポート

 

_**トピックの最終更新日:** 2012-10-03_

大規模な会議には次の特性があるため、前のセクションで説明したテスト モデルは採用されません。

  - 会議の形式が一対多のプレゼンテーションである。

  - 1 人または少数のユーザーが発表者であり、他のユーザーは出席者として参加するだけである。

  - PowerPoint プレゼンテーションの共有が主なデータ グループ作業になる。

  - 音声が必要であり、ビデオも使用する場合がある。

  - 専任担当者 (通常は会議の開催者または開催者の補佐役) がかなり前から会議を設定する。

  - (発表者ではなく) 専任スタッフがオンライン会議への接続、音声、ビデオ、およびスライドの共有作業の確認、ロビーとユーザー ロールの管理、参加者のミュートおよびミュート解除、質問の受付、レコーディングの管理などを必要に応じて行い、会議を運営する。

最大 1,000 ユーザーの大規模な会議をサポートするには、共有ハードウェア モデルと予約なしモデルの両方に関する問題に対処する必要があります。

最大 1,000 ユーザーの会議に対応できる十分な CPU リソースとメモリ リソースを確保するには、ホスト側のフロント エンド サーバーで、他のインスタント メッセージング (IM) とプレゼンスやエンタープライズ VoIP のワークロードを一切ホストしないようにする必要があります。また、会議の規模に関係なく、他の会議をホストしないようにすることも必要です。つまり、最大 1,000 ユーザーの会議をホストするには、最大 1,000 ユーザーの大規模な会議をホストすることだけを目的とした別の Lync Server プールを設定する必要があります。

大規模な会議をホストする専用の Lync Server プールでは、ホストする最大 1,000 ユーザーの会議を一度に 1 つに限定する必要があるので、アウト オブ バンド スケジューリング プロセスによって会議時間をあらかじめ予約し、フロント エンド サーバーの専用サポートを確保する必要があります。一度に複数の大規模な会議をサポートする場合は、専用の大規模会議プールを複数設定することをお勧めします。

大規模な会議のオンライン部分は専任担当者が実行し、監視することをお勧めします。この担当者は、組織の設定に応じて、開催者、開催者または発表者の代理人、大規模な会議の専任サポート チームのメンバーのいずれでもかまいません。

以下のセクションでは、Lync Server 2013 を使用して大規模な会議のシナリオをサポートする際のベスト プラクティスを含め、大規模な会議の専用プールを実装する方法について説明します。

## このセクション中

  - [大規模会議のサポートの設定](lync-server-2013-setting-up-support-for-large-meetings.md)

  - [大規模会議の管理](lync-server-2013-managing-large-meetings.md)

