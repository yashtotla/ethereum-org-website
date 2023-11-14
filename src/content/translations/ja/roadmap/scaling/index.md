---
title: Scaling Ethereum
description: ロールアップでは、トランザクションをオフチェーンでまとめて処理することで、ユーザーのコスト削減を実現しています。 しかし、現在のロールアップでは、データを使用するコストが高く、トランザクションを安価にすることが難しいという課題があります。 これについては、プロトダンクシャーディングによって解決できます。
lang: ja
image: ../../../../../assets/roadmap/roadmap-transactions.png
alt: "イーサリアムロードマップ"
template: roadmap
---

イーサリアムは、[レイヤー 2](/layer-2/#rollups)(ロールアップとも呼ばれます)と呼ばれるスケーリング技術で、トランザクションをまとめて処理し、出力をイーサリアムに送信します。 ロールアップでは、イーサリアムメインネットよりも最大 8 倍安価に取引を行うことができますが、ロールアップのさらなる最適化によって、さらにコストを削減できる可能性があります。 ただし、ロールアップには一部の集中化されたコンポーネントも含まれており、これはロールアップが成熟するにつれてデベロッパーによって取り除かれる予定です。

<InfoBanner mb={8} title="トランザクションコスト">
  <ul style="margin-bottom: 0">
    <li>現在のロールアップはイーサリアムのレイヤー1よりも<strong>約3～8倍</strong>安い</li>
    <li>ゼロ知識ロールアップはまもなく、<strong>約40～100倍</strong>安くなる予定</li>
    <li>イーサリアムの今後の仕様変更により、さらに<strong>約100～1000倍</strong>のスケーリングが実現</li>
    <li style="margin-bottom: 0">ユーザーは、トランザクションのコストが<strong>0.001ドル未満</strong>というメリットを享受</li>
  </ul>
</InfoBanner>

## データ費用の削減 {#making-data-cheaper}

ロールアップでは、大量のトランザクションをまとめて、その結果をイーサリアムに送信します。 これにより、大量のデータが生成されます。このデータは、誰でもアクセスできるように公開する必要があります。公開されているので、誰でも自分でトランザクションを実行し、ロールアップオペレーターが正直かどうかを確認することができます。 不一致を発見した場合、異議を申し立てることができます。

### プロトダンクシャーディング {#proto-danksharding}

ロールアップのデータは、イーサリアム上に永続的に保存されるため、コストがかかります。 ユーザーは、ロールアップで支払うトランザクションコストの 90%以上を、データストレージに費やしています。 トランザクションコストを削減するため、新たに「ブロブ」と呼ばれる一時ストレージ領域にデータを移動できるようになりました。 ブロブは、永続的でないため、比較的コストが安くなっており、不要になるとイーサリアムから削除されます。 ロールアップデータの長期保存は、ロールアップオペレータ、取引所、インデックスサービスなど、それを必要とする人々の役割となります。 イーサリアムへのブロブトランザクションの追加は、「プロトダンクシャーディング」と呼ばれるアップグレードの一部であり、 2023 年後半の比較的早い時期にリリースされる予定です。

プロトダンクシャーディングによって、イーサリアムプロトコルにブロブトランザクションが組み込まれると、イーサリアムのブロックにたくさんのブロブを追加できるようになります。 これにより、イーサリアムのスループットが大幅に向上し(100 倍以上)、トランザクションのコストも下げることができます。

### ダークシャーディング {#danksharding}

ブロブデータ拡張の第 2 段階は、大変複雑です。理由は、ロールアップデータがネットワーク上で利用可能であることを確認する新しい方法が必要だからです。また、バリデータの役割を分離して、ブロック構築とブロック提案に分けることも必要です。 さらに、バリデータがブロブデータの小さなサブセットを検証したことを暗号的に証明する方法も必要になります。

この 2 番目のステップは、[「ダンクシャーディング」](/roadmap/danksharding/)と呼ばれます。 完全に実装されるまでには、数年かかると予想されています。 ダンクシャーディングは、[ブロック構築とブロック提案を分離する](/roadmap/pbs)などの他の開発に依存しています。また、データが利用可能であることを効率的に確認するために、[データ可用性サンプリング(DAS)](/developers/docs/data-availability)と呼ばれる、数キロバイトのデータをランダムにサンプリングする新しいネットワーク設計も採用しています。

<ButtonLink variant="outline-color" to="/roadmap/danksharding/">ダンクシャーディングの詳細</ButtonLink>

## 分散型ロールアップ {#decentralizing-rollups}

[ロールアップ](/layer-2)は、イーサリアムのスケーラビリティ問題を解決する技術として、すでに実用化されています。 [ロールアッププロジェクトの豊富なエコシステム](https://l2beat.com/scaling/tvl)は、さまざまなセキュリティ保証を備えており、ユーザーは迅速かつ安価にトランザクションを実行できます。 しかし、ロールアップは、集中型のシーケンサー(トランザクションをイーサリアムに送信する前にすべてのトランザクション処理と集約を行うコンピューター)に依存しています。 シーケンサーは、オペレーターが制裁を受けたり、賄賂を受け取ったり、その他の方法で妨害される可能性があるため、検閲に対して脆弱です。 同時に、[ロールアップでは受信データを検証する方法が異なります](https://l2beat.com)。 最善の方法としては、「証明者」が不正証明または有効性証明を提出することですが、すべてのロールアップに備わっているわけではありません。 さらに、有効性証明および不正証明を使用するロールアップであっても、既知の証明者の小さなプールを使用するものがあります。 そのため、イーサリアムをスケーリングするための次の重要なステップは、シーケンサーと証明者を実行する責任をより多くの人々に分散することです。

<ButtonLink variant="outline-color" to="/developers/docs/scaling/">ロールアップの詳細</ButtonLink>

## 現在の進行状況 {#current-progress}

プロトダンクシャーディングは、ロードマップの初期段階で実装される予定です。 セットアップに必要な分散型の計算ステップはすでに開発済みです。また、いくつかのクライアントがブロブデータを処理できるプロトタイプも実装済みです。 完全なダンクシャーディングは、他のロードマップアイテムの完了を待つ必要があるため、おそらく数年先になるでしょう。 分散型ロールアップのインフラストラクチャは、段階的なプロセスを踏みます。たくさんの異なるロールアップが存在し、各システムで小さな違いがあります。そのため、それぞれ違った速度で完全に分散化されることになるでしょう。