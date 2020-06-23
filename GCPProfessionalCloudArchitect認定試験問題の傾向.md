

# 概要
GCP Professional Cloud Architect認定試験受講経験からよく出てきた問題を例題を踏まえてまとめる
[Professional Cloud Architect 公式サイト](https://cloud.google.com/certification/cloud-architect?hl=ja)


# 目次
[ケーススタディ](#ケーススタディ)
[障害特定](#障害特定)
[似通うプロダクトの選択](#似通うプロダクトの選択)
[ネットワーク](#ネットワーク)
[情報収集](#情報収集)
[実行パス保存先](#実行パス保存先)
[オンプレミスとgcpの接続](#オンプレミスとgcpの接続)
[k8sクラスタ生成と展開](#k8sクラスタ生成と展開)
[アラートと仮想機器の増量](#アラートと仮想機器の増量)
[ストレージ内のデータ自動削除](#ストレージ内のデータ自動削除)
[耐障害性テスト](#耐障害性テスト)
[スナップショットとイメージ](#スナップショットとイメージ)

### ケーススタディ
[Dress4Win](https://cloud.google.com/certification/guides/cloud-architect/casestudy-dress4win-rev2)
[TerramEarth](https://cloud.google.com/certification/guides/cloud-architect/casestudy-terramearth-rev2?hl=ja)
[Mountkirk Games](https://cloud.google.com/certification/guides/cloud-architect/casestudy-mountkirkgames-rev2?hl=ja)

ケーススタディの問題は簡単な問題から複雑な問題まで出題される
出題数は10問くらい
一つの回答と複数の回答を求められる問題が出題される
複数の回答の方が難しい傾向にある

例題
この質問については、JencoMart のケーススタディを参照してください。
JencoMart のセキュリティチームは、すべてのGoogle Cloud Platform インフラストラクチャが運用リソースと開発リソースの分離した最小限の権限モデルを使ってデプロイされていることを望んでいます。
どのGoogle ドメインとプロジェクト構造をするべきでしょうか？

A. ユーザーを管理するために開発/テスト/ステージング用と本番用の2つのG Suiteアカウントを作成します。各アカウントにはアプリケーションごとに1つのプロジェクトを含める必要があります。
B. ユーザーを管理するために2つのG Suiteアカウントを作成します。1つはすべての開発アプリケーション用の単一プロジェクト、もう1つはすべての本番アプリケーション用の単一プロジェクトです。
C. 1つのG Suiteアカウントを作成して、独自のプロジェクトの各アプリケーションの各段階でユーザーを管理します。
D. 単一のG Suiteアカウントを作成して、開発/テスト/ステージング環境用の1つのプロジェクトと本番環境用の1つのプロジェクトでユーザーを管理します。
Correct Answer: D

複雑な問題の特徴は複数の選択を問われる
例題
この質問については、JencoMart のケーススタディを参照してください。
JencoMart がユーザ認証情報データベースをGoogle Cloud Platform に移行して古いサーバをシャットダウンした数日後、新しいデータベースサーバはSSH 接続に応答しなくなりました。アプリケーション サーバーへのデータベース要求は正しく処理しています。
問題を診断するには、次のどの手順を実行する必要がありますか？（回答は3つ）

A. 仮想マシン（VM）とディスクを削除して、新しいVMを作成します。
B. インスタンスを削除し、ディスクを新しいVMに接続して調査します。
C. ディスクのスナップショットを取得し、新しいマシンに接続して調査します。
D. マシンが接続されているネットワークの受信ファイア ウォールルールを確認します。
E. 非常に単純なファイアウォールルールを使用してVMを別のネットワークに接続し、調査します。
F. トラブルシューティング用にインスタンスのシリアルコンソール出力を印刷し、インタラクティブコンソールをアクティブにして調査します。
Correct Answer: C, D, F

### 障害特定
障害を特定する問題
[Stackdriver](https://cloud.google.com/products/operations?hl=ja)を使用して特定する事が多かった

例題
顧客は、最近更新したGoogle App Engine アプリケーションが一部のユーザーでの読み込みに約30秒かかっているという報告を受けています。
この動作は、更新前には報告されていませんでした。
どうすればいいでしょうか？

A. ISPと協力して問題を診断します。
B. 問題を診断するためにネットワークキャプチャとフローデータを要求するサポートチケットを開き、アプリケーションをロールバックします。
C. 最初に以前の既知の正常なリリースにロールバックし、次にStackdriver Trace とStackdriver Logging を使用して、開発/テスト/ステージング環境で問題を診断します。
D. 既知の正常なリリースにロールバックし、アクセスが少ない時間にリリースを再度プッシュして調査し、Stackdriver Trace とStackdriver Logging を使用して問題を診断します。
Correct Answer: C

### 似通うプロダクトの選択
ストレージプロダクトやデータ解析プロダクトなどといった似通ったプロダクトの中からシュチュエーションにあったプロダクトを選択する問題
概要がわかりづらい[Dataflow](https://cloud.google.com/dataflow?hl=ja)や[pub/sub](https://cloud.google.com/pubsub/docs/overview?hl=ja)、内容と名前を混合させてしまう可能性がある[BigQuery](https://cloud.google.com/bigquery/?hl=ja&utm_source=google&utm_medium=cpc&utm_campaign=japac-JP-all-ja-dr-bkws-all-super-trial-e-dr-1008074&utm_content=text-ad-none-none-DEV_c-CRE_314712312207-ADGP_Hybrid+%7C+AW+SEM+%7C+BKWS+~+T1+%7C+EXA+%7C+Big+Data+%7C+1:1+%7C+JP+%7C+ja+%7C+big+query+%7C+bigquery+%7C+en-KWID_43700030995747722-kwd-47616965283&userloc_1009309&utm_term=KW_bigquery&gclid=CjwKCAjwrcH3BRApEiwAxjdPTYwFKn5FBeOSRvEE1Wwn-ej3JjoPN6PkZ1MZTwwxDWmmu8wuejcTfRoCSXUQAvD_BwE)と[Bigtable](https://cloud.google.com/bigtable/docs/overview?hl=ja)と言ったを区別しづらいプトダクトを確認しておくと良い

例題
会社では、ローカルデータセンターで実行されるApache Spark およびHadoop ジョブの数とサイズが急激に増加すると予測しています。
パブリック クラウドを利用して、最小限の運用作業とコード変更でこの今後の需要を拡大できるようにします。
どのGoogle Cloud Platafromプロダクトを使用するべきでしょうか？

正確なリアルタイムの天気図作成アプリケーションのパフォーマンスを最適化する必要があります。
データは5万個のセンサーから発信され、タイムスタンプとセンサーの読み取り値の形式で毎秒10回の読み取り値が送信されます。
どのGoogle Cloud Platform プロダクトにデータを保存するべきでしょうか？

A. Google BigQuery
B. Google Cloud SQL
C. Google Cloud Bigtable
D. Google Cloud Storage

Correct Answer: C

### ネットワーク
[ファイアウォール](https://cloud.google.com/vpc/docs/firewalls?hl=ja)やルート設定、タグ機能などを利用したネットワーク構築についての問題
[ネットワークタグ](https://cloud.google.com/vpc/docs/add-remove-network-tags?hl=ja)は便利だと思うので試験に出るでないにかかわらず学んでおく方がいいだろう

例題
組織には、Google Cloud Platform（GCP） の同じネットワークに展開された3層のWebアプリケーションがあります。
各層（Web、API、データベース）は、他の層とは独立してスケーリングします。ネットワーク トラフィックは、Webを介してAPI 層に流れ、次にデータベース層に流れます。Webとデータベース層の間をトラフィックが流れてはなりません。
どのようなネットワーク構成にする必要がありますか？

A. 各層を異なるサブネットワークに追加します。
B. 個々のVMにソフトウェアベースのファイアウォールをセットアップします。
C. タグを各層に追加し、ルートを設定して、目的のトラフィック フローを許可します。
D. 各層にタグを追加し、ファイアウォール ルールを設定して、目的のトラフィックフローを許可します。
Correct Answer: D


### 情報収集
他チームに提供するべき情報を選択する問題
基本的には[Stackdriver](https://cloud.google.com/products/operations?hl=ja)が活躍するだろう

例題
開発チームは、Google Compute Engine（GCE）仮想マシン（VM）のバッチサーバーに新しいLinux カーネルモジュールをインストールして、夜間のバッチプロセスを高速化しました。
インストールの2日後、バッチサーバーの50％が夜間のバッチ実行に失敗しました。
開発チームに渡すための失敗に関する詳細を収集する必要があります。
どのアクションを実行するべきでしょうか？（回答は3つ）

A. Stackdriver Logging を使用して、モジュールログエントリを検索します。
B. API またはGoogle Cloud Platform（GCP）Console を使用して、GCE のデバッグ アクティビティログを読み取ります。
C. gcloud またはGCP Console を使用してシリアルコンソールに接続し、ログを確認します。
D. アクティビティログで、障害が発生したサーバのライブ マイグレーション イベントが発生したかどうかを特定します。
E. Google Stackdriver のタイムラインを障害時間に合わせて調整し、バッチサーバ メトリックを観察します。
F. デバッグ VMをイメージにエクスポートし、カーネルログ メッセージがネイティブ画面に表示されるローカルサーバでイメージを実行します。
Correct Answer: A、C、E

### 実行パス保存先
試験で丸々同じ問題が出たので紹介

例題
Google Cloud Shell を使用しており、数週間で使用するカスタムユーティリティをインストールする必要があります。
ファイルをデフォルトの実行パスに保存し、セッション間で保持するには、どこに保存しますか？

A. ~/bin
B. Google Cloud Storage
C. /google/scripts
D. /usr/local/bin
Correct Answer: A

### オンプレミスとgcpの接続
オンプレミスとgcpプロダクトの接続方法
オンプレミスとの業務パターンは様々な物が存在する。パターンを知りたければ様々なプロダクトのユースケースをみると良いだろう。オンプレミスと関係しているユースケースは少なくないはず。

例題
Google Compute Engine インスタンスとオンプレミスのデータセンターの間にプライベート接続を作成します。
少なくとも20 Gbpsの接続が必要です。Google のベストプラクティスに従いまし
接続をどのように設定するべきでしょうか？？

A. VPCを作成し、Dedicated Interconnect を使用してオンプレミスのデータセンターに接続します。
B. VPCを作成し、単一のGoogle Cloud VPN を使ってオンプレミスのデータセンターに接続します。
C. Google Cloud Content Delivery Network（Google Cloud CDN）を作り、Dedicated Interconnect を使ってオンプレミスのデータセンターに接続します。
D. Google Cloud CDN を作り、単一のGoogle Cloud VPN でオンプレミスのデータセンターに接続します。
Correct Answer: A

### k8sクラスタ生成と展開
[Kubernetes(k8s)](https://kubernetes.io/ja/docs/concepts/overview/what-is-kubernetes/)をしようしたアプリ起動や配備の仕方
Kubernetesの詳しい内容は問われなっかったがクラスタやノードの意味などといった基本的な概念を理解すると良い。

例題
開発チームからKubernetes Deployment ファイルが提供されています。
インフラストラクチャはまだなく、アプリケーションを配備する必要があります。
どうすれば良いでしょうか？

A. gcloud を使用してKubernetes クラスタを作成し、Google Cloud Deployment Manager を使用して、デプロイメントを作成します。
B. gcloud を使用してKubernetes クラスタを作成し、kubectl を使用して展開を作成します。
C. kubectl を使用してKubernetes クラスタを作成し、Google Cloud Deployment Managerを使用して、デプロイメントを作成します。
D. kubectl を使用してKubernetes クラスタを作成し、 kubectlを使用して展開を作成します。
Correct Answer: B


### アラートと機器の増量
ある一定量を超えるような負荷がかかるシュチュエーションのアラートと処理速度&ストレージ調整を問う問題
アラートは基本的に[Stackdriver](https://cloud.google.com/products/operations?hl=ja)。
CPU1 40%
CPU2 40%
みたいなユースケースは見当たらず
CPU1 70%
CPU2 30%
のように片方が溢れる量を肩代わりする内容が多かった。このことからcpuを極端に下げて負荷を分散させる問題は気をつけた方が良いと感じた。　

例題
大規模なCRM 展開のデータベース バックエンドとしてGoogle Cloud SQL を使用しています。
使用量の増加に合わせて拡張し、ストレージが不足しないように、CPU 使用率コアを75 %に維持し、レプリケーションのラグを60 秒未満に抑える必要があります。
要件を満たすための正しい手順は何でしょうか？

A.
インスタンスの自動ストレージ増加を有効にします。
CPU 使用率が75 ％を超えた場合にStackdriver アラートを作成し、インスタンスタイプを変更してCPU 使用率を削減します。
レプリケーション ラグのStackdriver アラートを作成し、データベースを分割してレプリケーション時間を短縮します。
B.
インスタンスの自動ストレージ増加を有効にします。
インスタンスタイプを32コア マシンタイプに変更して、CPU 使用率を75 ％未満に保ちます。
レプリケーション ラグのStackdriver アラートを作成し、memcache を展開して、マスターの負荷を軽減します。
C.
ストレージが75 ％を超えたときにStackdriver アラートを作成し、インスタンスで使用可能なストレージを増やして、より多くのスペースを作成します。
memcached をデプロイして、CPU 負荷を減らします。
インスタンスタイプを32コア マシンタイプに変更して、レプリケーション ラグを減らします。
D.
ストレージが75 ％を超えたときにStackdriver アラートを作成し、インスタンスで使用可能なストレージを増やして、より多くのスペースを作成します。
memcached をデプロイして、CPU 負荷を減らします。
レプリケーション ラグのStackdriverアラートを作成し、インスタンスタイプを32コア マシンタイプに変更して、レプリケーション ラグを減らします。
Correct Answer: A

### ストレージ内のデータ自動削除
Cloud Storageの[オブジェクトライフサイクル管理](https://cloud.google.com/storage/docs/lifecycle?hl=ja)やGoogle BigQueryの[タイムパーティション](https://cloud.google.com/bigquery/docs/partitioned-tables?hl=ja)を利用したデータ自動削除機能を問う問題。
nopos化を考えると必ず出てきそうな問題です。私が受けた試験ではどちらも出題されました。

例題
アプリケーションは、分析のためにログをGoogle BigQuery に書き込むことになります。
各アプリケーションには、独自のテーブルが必要で、45日を経過したログはすべて削除する必要があります。
ストレージを最適化し、Google のベストプラクティスに従います。
どうすれば良いでしょうか？

A. テーブルの有効期限を45 日に設定します。
B. テーブルをタイムパーティション化し、パーティションの有効期限を45 日に設定します。
C. Google BigQuery のデフォルトの振る舞いを利用して、45 日以上経過したアプリケーションログを削除する。
D. Google BigQuery コマンドライン ツール（bg）を使用して、45 日より古いレコードを削除するスクリプトを作成する。
Correct Answer: B


### 耐障害性テスト
災害テストの仕方だけではなく、[高可用性構成](https://cloud.google.com/sql/docs/mysql/high-availability?hl=ja)についても理解しておく事が大切です。

例題
顧客は、認証レイヤーの耐障害性テストを希望しています。
Google Cloud SQL インスタンスの読み取りと書き込みを行う公開 REST API を提供するリージョン マネージド インスタンス グループで構成されます。
何をするべきでしょうか？

A. セキュリティ企業と協力して、悪意のあるWebサイトからユーザの認証データを検索します。見つかった場合は通知するWebスクレイパーを実行します。
B. 不正アクセスを検出してログに記録するために、仮想マシンに侵入検知ソフトウェアを導入します。
C. ゾーン内のすべてのVMをシャットダウンしてアプリケーションの動作を確認できる災害シミュレーションの実行をスケジュールします。
D. マスターとは別のゾーンでGoogle Cloud SQL インスタンスの読み取りレプリカを設定し、REST API のKPI を監視しながら手動でフェイルオーバーをトリガーします。
Correct Answer: C

### スナップショットとイメージ
バックアップは複製元としてしようされる[スナップショット](https://cloud.google.com/compute/docs/disks/create-snapshots?hl=ja)や[イメージ](https://cloud.google.com/compute/docs/images?hl=ja)の使用用途を区別できるようにすると良いです。認定試験ではどちらも一つの問題の選択で問われ区別できなければ答えられませんでした。

例題
この質問については、TerramEarth のケーススタディを参照してください。
TerramEarthは、接続されているすべてのトラックにサーバとセンサーを搭載し、遠隔測定データを収集しています。
来年にこのデータを使用して機械学習モデルをトレーニングしたいと考えています。 またコストを削減しながら、このデータをパブリック クラウドに保存したいとも考えています。
何をすれば良いでしょうか？

A. トラックのコンピューターに1時間ごとのスナップショットでデータを圧縮させ、Google Cloud Nearline Storage バケットに保存します。
B. 遠隔測定データを、データを圧縮するストリーミングデータ フロージョブにリアルタイムでプッシュし、Google BigQuery に保存します。
C. データを圧縮するストリーミングデータ フロージョブにリアルタイムで遠隔測定データをプッシュし、Google Cloud Bigtable に保存します。
D. トラックのコンピューターに1時間ごとのスナップショットでデータを圧縮させ、Google Cloud Coldline Storage バケットに保存します。
Correct Answer: D

例題
マネージド インスタンス グループの作成を自動化したいと考えています。
VMには、多くのOS パッケージの依存関係があり、インスタンス グループ内の新しいVMの起動時間を最小限にしたいと望んでいます。
何をするべきでしょうか？

A. Terraform を使用して、マネージド インスタンス グループと起動スクリプトを作成し、OS パッケージの依存関係をインストールします。
B. すべてのOSパッケージの依存関係を持つカスタムVM イメージを作成します。 Google Cloud Deployment Manager を使用して、VM イメージでマネージド インスタンス グループを作成します。
C. Puppet を使用して、マネージドインスタンスグループを作成し、OSパッケージの依存関係をインストールします。
D. Google Cloud Deployment Manager を使用してマネージド インスタンス グループを作成し、Ansible でOS パッケージの依存関係をインストールします。
