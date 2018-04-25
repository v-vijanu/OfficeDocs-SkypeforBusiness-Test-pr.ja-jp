﻿---
title: パイロット プール展開の DNS レコードの構成
TOCTitle: パイロット プール展開の DNS レコードの構成
ms:assetid: 5c7a6e10-e1e9-4479-9bf9-d4a3e2e09ff0
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ688072(v=OCS.15)
ms:contentKeyID: 49886974
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# パイロット プール展開の DNS レコードの構成

 

_**トピックの最終更新日:** 2012-09-24_

Lync Server 2013 パイロット ツールを展開する前に、パイロット プールの DNS ホスト A エントリを更新する必要があります。この手順を適切に完了するには、少なくとも Domain Admins グループのメンバーまたは DnsAdmins グループのメンバーとしてサーバーまたはドメインにログオンする必要があります。

**DNS ホスト A レコードを構成するには**

1.  ドメイン ネーム システム (DNS) サーバーで、\[**スタート**\]、\[**管理ツール**\]、および \[**DNS**\] の順にクリックします。

2.  ドメインのコンソール ツリーで、\[**前方参照ゾーン**\] を展開し、Lync Server 2013 がインストールされるドメインを右クリックします。

3.  \[**新しいホスト (A または AAAA)**\] をクリックします。

4.  \[**名前**\] をクリックして、プールのホスト名を入力します (ドメイン名は、レコードが定義されるゾーンから取られるため、A レコードの一部として入力する必要はありません)。

5.  \[**IP アドレス**\] をクリックし、フロント エンド プール の IP アドレス入力します。

6.  \[**ホストの追加**\] をクリックし、\[**OK**\] をクリックします。

7.  すべて終了したら \[**完了**\] をクリックします。
