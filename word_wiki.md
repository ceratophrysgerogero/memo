 用語wiki


<details><summary>ruby</summary>
オブジェクト思考スクリプト言語
Rubyの処理系は、主にインタプリタとして実装される
可読性を重視した構文となっている。
Ruby においては整数や文字列なども含めデータ型はすべてがオブジェクトであり、純粋なオブジェクト指向言語
設計思想はプログラミングを楽しむこと</details>

<details><summary>オブジェクト思考</summary>
計算機器学者アラン・ケイが言語を説明する中で生み出されたものであるのでそれ単体は漠然とした設計思想
なので言語や人によって認識同じとは限らない
一般的に説明されるオブジェクトの認識は以下のようなもの
クラスやインスウタンスはオブジェクト
オブジェクトは、メソッドをもつ
オブジェクトはデータ（記憶領域）をもつ
</details>

<details><summary>スクリプト言語</summary>
簡易的なプログラミング言語
言語によっては様々だが自分でコンパイルする必要がなかったり、変数の型を宣言しなくても良かったりなど作業をできるだけ簡略化していることが特徴的
</details>

<details><summary>インタープリンタ</summary>
大雑把に説明すると高級言語を機械語に翻訳しながらプログラミングができる
</details>

<details><summary>rails</summary>
webアプリケーションフレームワーク
MVCアーキテクチャに基づいている
テンプレートやパーシャル、レイアウトをeRubyを使用することで素早く構築することができる
Active Recordを使用してデータベースの操作ができる
アセットパイプラインを使用してjsとcssを管理できる
</details>

<details><summary>eRuby(ERB)</summary>
ruby周辺技術の一つ hmtlへRubyスクリプトを埋め込むことを可能にする
embedded(埋め込み) Ruby の略
拡張子はerbのことが多いい
HTML以外のプレーンテキスト（ASCll)でも可能
</details>

<details><summary>Active Record</summary>
データベースからデータを読み出すアプローチまたはデザインパターンのこと
データベースをクラスにラッピングし使いやすくする
</details>

<details><summary>アセットパイプライン</summary>
画像、js、css、htmlなどを分割してコーディングすることで作業分担し負担を軽くする。
分割したソースを一つのファイルの統合すること、統合したファイルをできるだけ小さくまとめる機能のことをアセットパイプラインと呼ぶ
</details>


<details><summary>Webpacker</summary>
Rails上でjsを開発するために必要な一連を提供してくれるGEM
</details>

<details><summary>gem</summary>
RubyGemsが公開しているライブラリのこと
このライブラリはパッケージ管理ツールです
</details>

<details><summary>ライブラリ</summary>
汎用性の高い複数のプログラムを人まめにしたもの
それ単体では、実行できない
</details>

<details><summary>パッケージ</summary>
関連する処理やプログラムをまとめたもの
</details>

<details><summary>git</summary>
分散型バージョン管理システム
動作速度に重点を置いている
特徴としては各ユーザーにワーキングディレクトリを作成する（リポジトリの完全複製物）
ネットワークにアクセスできない状態でもこのワーキングディレクトリを操作することでコミットや、マージといった作業をすることができる。これが分散型と呼ばれる理由
</details>

<details><summary>マイクロポスト</summary>
マイクロブログ（twitter等）に投稿される短いメッセージ
</details>

<details><summary>アーキテクチャ</summary>
コンピュータシステムの論理的構造
</details>

<details><summary>REST</summary>
REpresentational State Transfer
アーキテクチャの一つ
REST理論そのものはかなり抽象的
railsではアプリケーションを構築するコンポーネントをリソースとしてモデル化することをさす
リソースはデータベースの作成/取得/更新/削除操作と四つの基本的なHTTPリクエストメソッドに対応している
開発者はRESTfulな開発スタイルを採用することで作成するコントローラーやアクションの決定が容易になる
</details>

<details><summary>コンポーネント</summary>
何かの部品として認識してれば現状問題なさそう
深く調べてもこれだという定義がいまいちわからなかった

</details>

<details><summary>セマンティックweb</summary>
semantic 意味、意味論などを示す語
情報リソースに意味を付与することで人を介さ図に、コンピュータが自律的に処理できるようにするための技術
近年ではセマンティックとしてメタデータを付与したりオントロジーを使用することで実現しているß
</details>

<details><summary>メタデータ</summary>
情報に関する情報
例
田中 170 70 19660101 という情報リソースに対して
名前、身長、体重、生年月日というメタデータを付与することで
情報リソースを見ても人間ではわかるがPCではわからない部分がPCでもわかるようになり
自律的に処理しやすくなる（平均体重を割り出す、平均身長を割り出すなど）
メタデータの限界としてあげられるのはメタデータAように作ったプログラムAはメタデータBでは使用できないなどの点があげられる
参考資料
https://thinkit.co.jp/cert/article/0607/12/1/2.htm
</details>

<details><summary>オントロジー</summary>
Ontology 本体論 生存論 ある特定分野の概念や知識をさす
「語彙の定義」や「語彙と語彙の関係」を記述したもの
例
オントロジーがない場合では「東京周辺の歯医者」を検索にかけた時
<病院名＞山口歯医者<病院名＞
<住所＞東京都中央区<住所>
といった住所というメタタグにしか検索できなかったが
オントロジーを加えることで
<病院名＞中川歯医者<病院名＞
<所有地＞東京都大田区<所有地>
も検索することができる

情報科学では「共有されている概念化の形式的・明示的仕様」として用いられる
参考資料
[セマンティックWebとは](https://thinkit.co.jp/cert/article/0607/12/1/2.htm])
</details>

<details><summary>アプリケーションプリローダー</summary>
コマンドを実行する際に事前にバックグランドでライブラリをロードしておくことでその待ち時間を短縮すること
</details>

<details><summary>リファクタリング</summary>
プログラムの動作を変えず内部の構造を整理すること
</details>

<details><summary>SEO</summary>
Search Engine Optimization
検索エンジンのオーガニックな検索結果に置いて特定のウェブサイトが上位に表示されるような構成のこと
</details>



<details><summary>オーガニック</summary>
検索結果ページに表示されるリストのうち広告以外の物からアクセスした数のこと
オーガニック検索
自然検索
ナチュラル検索
などどもいう

</details>


<details><summary>トラフィック</summary>
通信回戦場で一定時間内に転送されたデータ量のこと
アクセス数の代わりに使われることがある
</details>

<details><summary>DRY</summary>
Don't Repeat Youreself
繰り返すべからず
</details>

<details><summary>IRB</summary>
Interactive RuBy
ターミナルからrubyを操作できる
</details>

<details><summary>コンストラクタ</summary>
クラスインスタンスが生成される時に呼び出されるメソッド
</details>

<details><summary>リテラル</summary>
数値や文字列を直接記述した定数のこと
変数の定義語
変更されないことを前提とした値
</details>

<details><summary>Bootstrap</summary>
webアプリケーションを作成するフロントエンドwebアプリケーションフレームワーク
タイポグラフィ、フォーム、ボタン、ナビケーションなどのjs拡張やCSSベースのデザインテンプレートが用意されている
githubで人気があり有名どこではアメリカ航空宇宙局はMSNBCなどに再興されている
</details>

<details><summary>モックアップ</summary>
　　設計やデザイン段階で施策される外見を事物そっくりに似せて作ること
</details>

<details><summary>レスポンシブデザイン</summary>
観覧者の画面サイズまたはウェブブラウザに応じてディスクトップページが観覧できることを目指したウェブデザイン　　
</details>

<details><summary>メタ言語</summary>
言語についてなんらかの記述をする言語
</details>

<details><summary>Sass(scss)</summary>
インデント構文はメタ言語
sassと行ったらインデント構文のことをさすこともある
css3にはないものをcssで拡張できる
sassscriptでcssに変換する
scssはsass記法のものをsass3.0からcssぽく記述できるようにscss記法というので記述できるようになった。どちらも結果的にcssになる
</details>

<details><summary>Less</summary>
The dynamic stylesheet language（ダイナミックなスタイルシート言語）の略
</details>


<details><summary>less</summary>
動的スタイルシート言語
オープンソフトウェア
インデント構文はメタ言語
単純なcssに変換できる
</details>

<details><summary>タイポグラフィー</summary>
文字を効果的にデザインすること　意味は広く字の間やサイズなどを調整して可読性をあげること
</details>

<details><summary>CoffeeScript</summary>
CoffeeScript はプログラミング言語のひとつである。コードはJavaScript のコードに変換される
シンタックスシュガーの導入により、JavaScript に比べ簡潔さと可読性を向上させたほか、配列内包 (Array comprehensions) やパターンマッチングといった機能を追加している。
CoffeeScript により、パフォーマンスを下げることなく、より短いコードでプログラムを記述することができる (JavaScript に比べ 1/3 程度の行数が削減できる)[2]。 2011年3月16日から一時、CoffeeScript は GitHub でもっともウォッチされているプロジェクトであった
JavaScriptにコンパイルしてくれるJavaScriptの拡張言語
</details>

<details><summary>シンタックスシューガー</summary>
またの名を糖衣構文という
プログラミング言語に置いて読み書きのしやすさのために導入される書き方
取り扱いやすい（sweet)から第一義が甘いであることから

java
String[] strs = new String[3];
strs[0] = "a";
strs[1] = "b";
strs[2] = "c";　は
String[] strs = { "a", "b", "c" };
とかける
</details>

<details><summary>インスタンス変数</summary>
オブジェクトの中で値を保存することができる変数
railsでは@変数名で宣言できる
</details>

<details><summary>ローカル変数</summary>
主にメソッド内でしか使わない変数のこと
メソッドが処理している間はメソッド内で使用できる
</details>

<details><summary>SQLインゼクション</summary>
データベースと連動したWebサイトで、データベースへの問い合わせや操作を行うプログラムにパラメータとしてSQL文の断片を与えることにより、データベースを改ざんしたり不正に情報を入手する攻撃。また、そのような攻撃を許してしまうプログラムの脆弱性のこと。
</details>
<details><summary>RSpec</summary>
RSpec とは Ruby プログラマー向けの BDD(Behaviour-Driven Development) ツールです。
ここでの BDD はテスト駆動開発(Test-Driven Development), ドメイン駆動型設計(Domain Driven Design), 受け入れテスト型設計へのアプローチのことです。

RSpec は Gem パッケージとして提供されています。

</details>
<details><summary>BDD</summary>
ビヘイビア駆動開発という
TDDと何が違うかと言われるとそこまで違いがないのでほぼ同じようなものだと思っていいかもしれない
</details>


<details><summary>シンボリックリンク</summary>
OSファイルシステムの一つ、特定のファイルやフォルダディレクトリを示す別のファイルを作成し、参照させる
馴染み深く言えばショートカットのようなもの
</details>
<details><summary>Active Record Pattern</summary>
データベーステーブルまたは、ビューをラッピングし、データベースアクセスをカプセル化することでデータにドメインロジックを追加するオブジェクトを作成する
rubyで再現すると
・クラスは１つのテーブルを表す
・インスタンス はテーブルの一行を表す
・クラス、インスタンス メソッドで関連するデータ処理を行う

</details>

<details><summary>リレーショナルデータベース</summary>
RDBと略して言ったりする
一件のデータを複数の属性の値の組として表現し、組を列挙することでデータを格納していく方式。属性を列、組を行とする表（テーブル）の形で示されることが多い。最も普及している方式で、単にデータベースといった場合はリレーショナルデータベースであることが多い。
RDMSとはリレーショナルデータベース管理システム
RDMSでDBを操作する場合はSQLを使用する
</details>

<details><summary>NoSQL</summary>
RDBでデータの問い合わせや操作を用いる言語であるSQLを使用しない
基本的にRDBの苦手なことができるようになったと考えて問題ない
</details>

<details><summary>インクリメンタルサーチ</summary>
アプリケーションに置ける検索方法の一つ
検索したい単語を全て入力した上で検索するのではなく入力のたびごと即座に候補を表示させる
逐語（ちくご）検索ともいう
</details>

<details><summary>コンフリクト</summary>
衝突、矛盾
デジタル業界ではソフトウェア同士がお互いのメモリー領域を犯すなどのような障害やエラーに対して対してコンフリクトという言葉を使う
</details>

<details><summary>SQLite</summary>
パブリックドメインの軽量なRDBMS（関係データベース管理システム)
サーバーとしてではなくアプリケーションに組み込んで利用されるDB
一般なRDBMSち番うAPIは単純にライブラリを呼び出すだけ
データの保存には単一のファイルを使用することが特徴

</details>

<details><summary>オブジェクトリレーショナルマッピング</summary>
直接SQL文を書く代わりに非常に短いコードでデータベースの読み書きを行える機能のこと
</details>

<details><summary>ORM　O/R マッピング　オブジェクトマッピング</summary>
データベースとオブジェクト指向プログラミング言語の間の非互換データを変換するプログラミング技法
</details>

<details><summary>エイリアス</summary>
alias
偽名、別名、通称などの意味をもつ英語
例
rails
update_attributesとupdateは同じメソッド
</details>

<details><summary>isp(インターネットサービスプロバイダ)</summary>
回線業者が提供するインターネット回線を使用するためのインターネット接続事業者のことをさす
主にメールアドレスやセキュリティ対策、独自ドメイン取得サービスなど様々な提供を行なっている
</details>
<details><summary>index(インデックス)</summary>
素因、検索エンジンの記録されてるホームページ情報、DBの検索を早くする仕組み、配列の添字など様々な分野で色々な意味合いで使用される
データベースにインデックスを付けるという意味あいでは列検索することや列を何かの基準に並べて検索をかけるといったことをすることで単純で検索量が少なければ検索スピードが早くなると思っていいss
</details>
<details><summary>ハッシュ化</summary>
元のデータから一定の計算手順にしたがってハッシュと呼ばれる規則性のない固定長の値を決めること
よくパスワードの保管で使われる
パスワードの認証も入力したハッシュ値と保存したハッシュ値を比較して認証する
同じ入力に対しては同じ値が帰ってくる
ハッシュ値から元のデータを特定するのはほとんどできない（計算量的に復元が困難　不可逆ともいう）
ものデータが少しでも変わるとハッシュ値はガラリと変わる
</details>

<details><summary>暗号化</summary>
設計上元に戻すことができる規則性のない値にすること
</details>

<details><summary>BCrypt</summary>
Blowfish(対照ブロック暗号化)の暗号式をプログラムで利用できるように実装したもの。特許されていないライセンスフリーであることや他の暗号化より比較的に高速であることから認証システムでよく使われる
ハッシュはソルト化している
レインボーテーブルにに対して強特徴をもつ
railsでしようしたい場合はgemfileで追加する
</details>

<details><summary>ソルト化</summary>
パスワードやパスレーズなどのデータをハッシュ化する際に、一方向性関数の入力に加えるランダムなデータのこと
ソルト（塩）という短いランダムな文字列をパスワードの末尾に加えた上で暗号化する。ソルトは認証のさいに利用できるように暗号化したパスワードと共に保管される。通常のソルトはユーザごとに異なるので各パスワードの候補のハッシュ値を一個しか計算していない事前計算リストは役に立たない。bcryptは126ビットのソルトを使用している
</details>

<details><summary>辞書攻撃(dictionary attack)</summary>
クラッカーが特定のコンピュータに施されたパスワードを調べたりスパム送信者が送信先のメールアドレスを決める際に用いられる
ブルートフォースアタックや、よく使われる単語からメールアドレスを推測し宛先を調べたりする
</details>

<details><summary>ブルートフォースアタック</summary>
総当たりでパスワードを打ち込んでパスワードを知る方法
</details>

<details><summary>レインボーテーブルアタック</summary>
簡単な考え方としては、このハッシュ値だったら平文はこれだというものを事前に用意しておくこと
例えばmd5 ハッシュ値が
5f4dcc3b5aa765d61d8327deb882cf99 ならば 平文はpasswordとなる

これを様々な文字列を総当たりでやって事前にデータ化することが発端
</details>

<details><summary>YAML</summary>
ヤムルと読む
yaml ain't markup language（マークアップ言語ではない）
構造化データやオブジェクトを文字列にシリアライズするためのデータ形式
主に設定ファイルやデータの保存ログファイルなどで使用する
特徴として読みやすい、書きやすい、わかりやすいなどやインデントを使ってデータ構造を
表せたり終了タグが存在しない、データ構造をハッシュ、配列、スカラーであわらせる
</details>

<details><summary>シリアライズ</summary>
メモリ上に存在する情報をファイルとして保存したり、ネットワークで送受信したりできるように変換すること
javaではインスタンス をファイルに保存して復元したりできることをさす
</details>

<details><summary>Gravatar</summary>
無料サービスでプロフィール写真をアップロードして指定したメールアドレスと関連づけることができる
その結果プロフィール写真をアップロードするときに面倒な作業やトラブルがなくなりやすくなると同時に
画像の置き場所の悩みも解決してくれます
というのも、ユーザーのメールアドレスを組み込んだGravatar専用の画像パスを構成するだけで、
対応するGravatarの画像が自動的に表示されるからです
</details>

<details><summary>スクリーンリーダー</summary>
画面読み上げソフトウェア
</details>

<details><summary>マスアサインメント</summary>
DB登録・更新で複数のカラムを一括で指定して登録すること
</details>

<details><summary>SSL(TLS)</summary>
インターネットなどのTCP/IPネットワークでデータを暗号送受信するプロトコルの一つ
Secure Sockets Layer からTransport Layer Securityと変わったがいまだにSSLと呼ぶことが多い
</details>

<details><summary>WEBrick</summary>
単純なhttp webサーバの機能を提供するRubyのライブラリ
</details>

<details><summary>webサーバー</summary>
ユーザーから送られてきたリクエストを何らかの処理を加えるプログラム
場合によってはアプリケーションにリクエストを投げる
有名どころではNginxとapache　IIS
cssやJS、画像など頻繁に変化しないファイルのリクエストではRailsアプリケーションはそのリクエスト
を処理する必要する必要がないかもしれない。
webサーバーはSSLリクエストや静的なファイルやアセット、圧縮されたリクエスト等を処理したり、その他大半のwebサイトが必要としそうな数多くの処理をこなしたりすることができます
</details>

<details><summary>アプリケーションサーバー</summary>
アプリケーションを動かしいていいるもの(rubyやjavaを動かしていると思っていい)
Unicorn、Thin、Rainbows、Puma、Tomcat、GlassFish
</details>

<details><summary>ステートレスポトコル</summary>
通信が独立した要求と対応の組みからなるようにそれぞれの要求を
それ以前の要求とは無関係に独立したトランザクションとして扱う通信プロトコル
例としてInternet Protocol、World Wide Web、Hypertext Transfer Protocol(HTTP)などがある
</details>

<details><summary>セッションハイジャック</summary>
セッションを乗っ取りなりすましてログインしたりすること
HTTPによるハイジャックを示すことが多いいが必ずしもこの用語が示す範囲とは限らない
</details>

<details><summary>イディオム</summary>
二、三の語が結びついて、原義とは幾分違った特殊な意味を持つ、習慣的な言いまわし。慣用語。成句。
</details>

<details><summary>ディレクティブ</summary>
プログラミングのコマンドのような意味合いで使われる。コンパイラやアセンブラに処理方法を
指示するようなことをさす。
</details>

<details><summary>jQuery</summary>
ウェブブラウザ用のjsコードをより簡易に記述できるように設計荒れたjsライブラリs
</details>

<details><summary>クロスサイトリクエストフォージュリー(CSRF)</summary>
サイトに攻撃用のコード（js）を埋め込むことでアクセスしてきたユーザーに対して
意図しない操作を行わせる攻撃（連続投稿とか色々）
</details>

<details><summary>クロスサイトスクリプティング（XSS）</summary>
スクリプトをxssの貧弱性のあるサイトに埋め込む（スクリプトが埋め込まれたリンクのURLを掲示板へ投稿等）
ユーザーが敷かれたサイトに訪問
スクリプトリンクをクリック（実行）
ユーザーのパソコンにスクリプトの情報が保存された状態で仕掛けられたリンクから他のサイトへ移動する（クロスサイト）
スクリプトによって偽サイトへ移動する
偽サイトで個人情報を入力
個人情報漏洩やマルウェア感染
</details>

<details><summary>トークン</summary>
コンピュータが生成管理する秘密情報
パスワードとの違いはパスワードはユーザーが作成して管理するもの
</details>

<details><summary>cookie(クッキー)</summary>
HTTP cookies
HTTPに置けるwebサーバとウェブブラウザ間で状態の管理をする通信プロトコル、またはそこで用いられるWebブラウザに保存されている情報をさす
ユーザーの識別やセッション管理を実現することに使われる
クッキーは様々な利点があるが他者に盗まれてしまうと悪用され被害が出ることがあるので十分とりあつかいには注意したい
クッキーを取得する方法で有名な方法は4つある
1.管理の甘いネットワークを通過するネットワークぱkっとからパケットスニッファという特殊なソフトで取り出す
2.データベースから記憶トークンを取り出す
3.クロスサイトスクリプティングを使う
4.ユーザーがログインしているパソコンやスマホを直接操作してアクセスする

</details>

<details><summary>スニッファ</summary>
パケットとを登頂するとき使うソフトのこと
</details>

<details><summary>クエリ</summary>
検索条件のことs
</details>

<details><summary>パケット</summary>
情報転送の単位
ネットワークを流れるひとかたまりのデータ
</details>

<details><summary>三項演算子</summary>
if 条件
　式１
else
　式２
end
を
条件 ? 式１ : 式２
に置き換えれる
これはrubyの例である
他の言語では仕様が違うことがあるので他の言語でも同じ書き方だと思うと痛い目にあう
また複雑な式に関しては可読性がなくなってしまうことが多いいので
シンプルなif文になる式に使用した方が懸命だろう      
またrailsで使用する場合ハッシュ記号:と三項演算子の:に区別つきにくいのであまり使いたくはない
</details>

<details><summary>URLクエリーパラメーター</summary>
urlにパラメーターをつけること
例
http://gaforum.jp/?s=gaiq
　　　　　　　　?s　=　gaiqがクエリパラメーターで
パラメーター（変数）＝ 値
となる
パラメーターを複数使いう場合は&でつなげる
</details>


<details><summary>メタプログラミング</summary>
プログラムでプログラミを生成すること
プログラムでメソッド名を作る等
</details>

<details><summary>純粋関数</summary>
なにかが必ず値が帰ってくる
void型は値がないので違う
副作用がない（他のクラスの値が変わらない等)
</details>

<details><summary>http(Hypertext Transfer Protocol)</summary>
HTMLなどのコンテンツ送受信の通信プロトコルのこと
通常時トランスポートプロトコルとしてTCPを使う
</details>

<details><summary>https</summary>
TLSで暗号化セキュリティを確保された場合はhttpsと呼ばれる
</details>

<details><summary>3ハンドシェイク</summary>

</details>


<details><summary>アジャエル</summary>

</details>

<details><summary>スクラム</summary>
アジャエルの派生
スプリントと呼ばれる単位で作業量を決める
チームによってどれくらいのスプリントでできるかを明確にする
</details>

<details><summary><details><summary></summary>

</details><details><summary></summary>

</details>VBA</summary>

</details>

<details><summary>セッション</summary>

</details>

<details><summary>TCP</summary>

</details>

<details><summary>UDP</summary>

</details>

<details><summary>sier</summary>

</details>

<details><summary>ses</summary>

</details>

<details><summary>URIスキーム</summary>

</details>

<details><summary>ファシリティ</summary>
総務部の仕事に含まれオフィス移転やレイアウト変更、設備備品管理、内戦管理などをする業務
</details>

<details><summary>IOT(Internet of Things)</summary>
物インターネット
様々な物がインターネットに接続され情報公かすることにより相互制御をする仕組み
</details>

<details><summary>外部キー</summary>
FOREIGN KEYと呼ばれ関連したテーブル感を結ぶために設定される列のこと
参考　https://wa3.i-3-i.info/word1992.html
</details>

<details><summary>ER図</summary>

</details>

<details><summary>フィード</summary>
　ウェブサイト、特にブログやニュースサイトなどのコンテンツの概要もしくはコンテンツ全体を配信用に加工した文章のこと
</details>

<details><summary>モックアップ</summary>
設計や、デザイン段階でしい作される外見を事物そっくりににさせて作られた実物大の模型
webサイトやソフトウェアなどは試作品として言われることもある
</details>

<details><summary>フィード</summary>
新規記事を一覧やサイトないのページの一覧公開のまとめた物を示す
</details>

<details><summary>Ajax</summary>
Asynchronous JavaScript + XML の略
簡単に説明するとjsとXMLを使って非同期サーバー通信を行うことができる
画面遷移せずにHTMLを更新することができるのでサーバーの負荷軽減に繋がる
例えばrailsチュートリアルではfollowボタンを押したとき必ずリダイレクトで元のプロフィール画面に戻ってしまうが
Ajaxを利用することで非同期でページを移動することなく送信する(14章)
</details>


<details><summary>XMLHttpRequest</summary>
クライアントとサーバーの間でデータを伝送するための機能をクライアント側で提供するapii
ページ全体を再読み込みする必要なくURLからデータの一位部を更新することができる
</details>

<details><summary>DOM(Document Object Model)</summary>
HTMLおよびXMLドキュメントのためのAPI
ドキュメントの構造的な表現を提供し、内容と表現形態を変化させることを機能とする
webページとスクリプトやプログラミング言語と繋ぐような機構
</details>

<details><summary>json(JavaScript Object Notation)</summary>
軽量のデータ交換フォーマットで、人間にとって読み書きが用意なもの
{ "name"   : "John Smith",
  "sku"    : "20223",
  "price"  : 23.95,
  "shipTo" : { "name" : "Jane Smith",
               "address" : "123 Maple Street",
               "city" : "Pretendville",
               "state" : "NY",
               "zip"   : "12345" },
  "billTo" : { "name" : "John Smith",
               "address" : "123 Maple Street",
               "city" : "Pretendville",
               "state" : "NY",
               "zip"   : "12345" }
}

</details>

<details><summary>ALGOL</summary>
アルゴル
アルゴリズムの記述に向いた手続き型プログラミング言語の一つ
1958年に発表　この頃には珍しく抽象的、汎用的な言語として規定された
のちのC言語には大きな影響を与えた
</details>

<details><summary>手続き型言語</summary>
正直よくわからん
そういう言語ってことでいいと思う
</details>


<details><summary>フィンガープリント</summary>
指紋という意味
改竄されているかチェックする仕組み
簡単に例に出して説明すると
1.メールをハッシュ化してフィンガープリントを作成する
2.メールとフィンガープリントを送信する
3.受取手は受け取ったメールをハッシュ化してフィンガープリントを作成する
4.受取手は受け取ったフィンガープリントと作成したフィンガープリントを見比べる
5.同じ内容であれば改ざんされていないことになる
</details>

<details><summary>MD5</summary>
暗号学的ハッシュ関数の一つ
</details>


<details><summary>Unicode</summary>
文字コードの業界規格名称
ツイッターやLINEなどで使える絵文字（顔文字が有名)のコードのこと
</details>


<details><summary>SPA(single page application)</summary>
単一のwebページ

メリットとして動作性の工場
より行動なweb表現
ネイティブアプリの代用
</details>

<details><summary>cms(content management system)</summary>
コンテンツ管理システム
本来であればwebページを作成するためにはhtmlなどを駆使する必要があるが誰でも作成できるようにしたもの
よくあるブログ作成サービスはいい例
</details>

<details><summary>CRUD(クラッド)</summary>
コンピュータソフトウェアがもつ永続的基本機能4つのイニシャル
Create（生成）
Read（読み取り）
Update（更新）
Delete（削除）
</details>

<details><summary>sprign(rails)</summary>
Springとは、Rails4.1から標準で付属するようになったアプリケーションプリローダーです。
Rails内では様々なライブラリのロードなどの前処理が行われるので、コマンドを実行するための待ち時間がかかってしまいます。
事前にバックグラウンドでライブラリをロードしておくことで、その待ち時間を短くするものがアプリケーションプリローダーです。

MiniTestやRSpecをrakeコマンドで実行したり、サーバー起動やconsoleをrailsコマンドで実行すると思いますが、動き出すまで数秒かかると思います。
開発を通すとこういったコマンドは、何十回、何百回も実行することになるので、数秒でも早いにこしたことはありません。

他の有名なアプリケーションプリローダーには、SporkやZeusといったものもあります。

git hubから
Compatibility
Ruby versions: MRI 2.4, MRI 2.5, MRI 2.6
Rails versions: 4.2, 5.0, 5.1, 5.2, 6.0 (Spring is installed by default when you do rails new to generate your application)
</details>


<details><summary>yaru</summary>
js　パッケージマネージャー
npmよりもインストールが早い
npmよりもモジュールバージョンを厳密に管理できる
npmと一緒に使える
</details>

<details><summary>npm</summary>
node.js パッケージ管理ツール
node package managerの略
</details>

<details><summary>node.js</summary>
jsは本来クライアント再度で動く言語でhtmlで書かれたページに動きをつける
node.jsはサーバーサイドで動くjs

メリットとしては様々
主にc10k問題を解決できること大きい
</details>

<details><summary></summary>

</details>

以下メモ
### 先駆者に聞きたいこと、詳しく調べたいこと
* railsはSQLを気にせずにデータベースを操作できるがNoSqlと何が違くて利点はどこなのか？
* DBの歴史について知りたい
* ORMのメリットがいまいち理解できない　同じ学習コストがかさむならSQLでもいいのでは？
* update_attributesよりupdate_attributeを使う利点（使い所さん）
* キーワード引数やオプション引数など引数にハッシュやシンボルの宣言ができるが危なくないのか？
* ヘルパーにすべきメソッドの見分けかた
* railsでコントローラで宣言されているインスタンス変数が使える範囲(1インスタンスはどこからどこまでかわからない)

### やりたいこと
railsチュートリアルではメールアドレスを大文字小文字関係なく同一としていたのでそこを同一ではないように作成したい

### 今後学ぶべき事柄
正規表現
scss
Bootstrap
