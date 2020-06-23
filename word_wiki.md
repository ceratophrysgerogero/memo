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


<details><summary>スクラム</summary>
アジャエルの派生
スプリントと呼ばれる単位で作業量を決める
チームによってどれくらいのスプリントでできるかを明確にする
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
他のテーブルからデータを参照してカラムにつける制約
もちろん参照先に依存する
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

<details><summary>O/Rマッパー(オブジェクト関係マッピング Object-relational mapping)</summary>
オブジェクトをデータベースに格納可能な単純な値のグループに変換するマッパーの事
オブジェクトをデータベースに格納可能な形式に変換し、後で容易に検索できるようにし
同時にオブジェクト同士の関係の特性を保持することを永続的、永続化という
</details>

<details><summary>リレーショナルモデル(関係モデル)</summary>
要はRDBMSで管理している表のこと
テーブル名カラム名行で管理すること
</details>

<details><summary>PDCA</summary>
企画運営や業務遂行について「計画→実行→評価→改善」のステップを継続的に回すことで、管理体制や運営体制の質を高め続けていくために使われるフレームワークです。PLAN：計画、DO：結果、CHECK：評価、ACTION：改善、それぞれの英単語の頭文字をとって「PDCA（ピーディーシーエー）」と呼ばれる
PDCAチェックシートなどを活用にして社員の評価をすることもある
</details>

<details><summary>エンティティ</summary>
 IDでしか同一性を判断できないものオブジェクト
同姓同名同年齢同性別でも必ずしも本人であるかはデータ上からはわからない
</details>

<details><summary>値オブジェクト</summary>
IDじゃなくても判断できるオブジェクト
同国同市同区であればその属性が一致しているので同一の場所
</details>

<details><summary>永続化</summary>
インスタンスの状態を半永久的に保存し、いつでも復元できるようにすることで基本的にはDBにデータを保存すること。
</details>

<details><summary>PORO, Plain Old Ruby Object</summary>
Active Recordなどを継承していないふつうのオブジェクトのこと
</details>

<details><summary>O2O</summary>
  オンライン・ツー・オフラインとは、インターネットなどのオンラインから店舗などのオフラインへ消費者を呼び込む施策。
</details>

<details><summary>オウンドメディア</summary>
オウンドメディアとは、自社発行の広報誌やパンフレット、インターネットの自社ウェブサイト・ブログなど、企業や組織自らが所有し、消費者に向けて発信する媒体を指す。
</details>

<details><summary>saas</summary>
Software as a Service（サービスとしてのソフトウェア）」の略。
クラウドで提供されるソフトウェアのことを指します
</details>

<details><summary>cvr(コンバージョンレート)</summary>
Conversion Rate の略
Webサイトにアクセスが発生した場合、そのアクセスのうちどのくらいが、登録や購入、申し込みなどのコンバージョンに繋がったかの割合を示します
</details>

<details><summary>カンバン</summary>
チームの状態を見える化しチーム改善を運用するためのツール
参考
https://qiita.com/TAKAKING22/items/0a6412e5c3a95a90da50
</details>

<details><summary>ファン・ダン・ラーン(FDL)</summary>
楽しいこと
遂行できたこと
学習できたこと
に分けて振り返ること
参考
https://qiita.com/yattom/items/90ac533d993d3a2d2d0f
</details>


<details><summary>lint</summary>
ソースコードに対してコンパイラよりも詳細かつ厳密にチェックするプログラム。
</details>

<details><summary>ステージング環境(stg)</summary>
開発環境→検証環境→本番環境と開発を進める中で
検証環境のことをステージング環境と呼ぶ
</details>

<details><summary>Google Analytics(GA)</summary>
Googleが無料で提供するWebページのアクセス解析サービス
</details>

<details><summary>Page Speed Insights </summary>
サイトの重さを測れるツール
</details>

<details><summary>Elasticsearch(エラスティックサーチ)</summary>
全文検索エンジン
</details>

<details><summary>マイクロサービス(アーキテクチャ)</summary>
従来は、ある目的に対して、モノリシック（一枚板）なアーキテクチャでサービスを提供していました。対して、マイクロサービスは、個別に開発された小さなサービスを組み合わせて、一つのサービスを提供するというものです。
参考
https://www.salesforce.com/jp/blog/2016/03/microservices.html
</details>

<details><summary>バインディング</summary>
オブジェクト間の参照の生成。 データバインディング - データベースなどとソフトウェアを結びつける技術
</details>

<details><summary>MVVM</summary>
https://qiita.com/usada-kumi/items/046c9a43b15b9e376198
</details>

<details><summary>Firebase</summary>
モバイルおよびWebアプリケーション開発プラットフォーム
</details>

<details><summary>エアポートテスト</summary>
用基準として『次に乗る飛行機が飛ばなくなり、空港の近くのホテルで泊まらなければならなくなったときに、一緒に泊まって会話ができるか』というテストを、科学的に行っている
</details>

<details><summary>リーディングカンパニー</summary>
一般的に、中核的あるいは模範的立場に立ち、その業界の先駆者として存在する企業を意味する語
</details>

<details><summary>リバースオークション</summary>

</details>


<details><summary>Kubernetes</summary>
クーべネティスやk8sと呼ばれる
簡単に言えばドッカーでできないことをできる様にしたコンテナ管理システム
現在三代クラウドサービスがあるがそのサービスをマネージできるサービスがある
https://www.sbbit.jp/article/cont1/35564
https://qiita.com/MahoTakara/items/85096f8b2632c802ab22
</details>

<details><summary>デーモン</summary>
Unix系のマルチタスクOSに置いて動作するプロセス
〜デーモンと言えば常駐しているシステムだと思って良い
</details>

<details><summary>Saas</summary>
Software as a Service
これまでパッケージ製品として提供されていたソフトウェアを、インターネット経由でサービスとして提供・利用する形態

アプリケーション
ミドルウェア
OS
ハード
ネットワーク
まで提供
</details>

<details><summary>PaaS</summary>
Platform as a Service
アプリケーションソフトが稼動するためのハードウェアやOSなどのプラットフォーム一式を、インターネット上のサービスとして提供する形態

ミドルウェア
OS
ハード
ネットワーク
まで提供
</details>

<details><summary>IaaS</summary>
Infrastructure as a Service
情報システムの稼動に必要な仮想サーバをはじめとした機材やネットワークなどのインフラを、インターネット上のサービスとして提供する形態

OS
ハード
ネットワーク
まで提供
</details>

<details><summary>オンプレミス</summary>
自社内でインフラ周りを整える事
</details>

<details><summary>CAP定理</summary>
Cクラウドサービスを始めとする情報システム（ネットワークでつながった、共通のデータを持つ、一連のノード群）において、「以下の3要素を同時に満たすことができない」というもの

CAP定理の3要素	説明
Consistency：一貫性	誰かがデータを更新したら、その後は必ず更新後のデータが参照できること
Availability：可用性	クライアントは必ずデータにアクセス可能であること（データが壊れたり、ロック待ちにならないこと）
Partition Tolerance：ネットワーク分断耐性　データを複数サーバに分散して保管できること（データが複数のサーバに分散されており、1つサーバに障害が発生し、データが破損した場合でも、別サーバによりデータが参照可能であること）

</details>

<details><summary>VPC</summary>
Virtual Private Cloud
共有型のクラウド、すなわちパブリッククラウド内に作られたプライベートクラウドのこと
Amazon VPCでは仮想ネットワーク環境を制御して、既存のデータセンターと自分のVPC間にハードウェア仮想プライベートネットワーク（VPN）接続

</details>

<details><summary>SMTP</summary>
Simple Mail Transfer Protocol
簡易メール転送プロトコル
</details>

<details><summary>リージョン</summary>
データセンターを設置している独立したエリア
</details>

<details><summary>ゾーン</summary>
各リージョン内には独立したインフラの運用区画
</details>

<details><summary>BCP対策</summary>
Business Continuity Plan
地震、津波、大雨、大雪などの自然災害や事故、停電など、予測不可能な緊急事態に見舞われた際に取るための施策で、重要業務の被害を最小限に抑え、企業運営を滞らせないための行動指針
</details>

<details><summary>TCP</summary>
Transmission Control Protocol
IPと同様にインターネットにおいて標準的に利用されている プロトコル
3way　ハンドシェイクによる通信前の打診
ackによる相手の受信確認や再送処理などを提供している
UDPと比べて負担が大きい
</details>

<details><summary>UDP</summary>
User Datagram Protocol
TCPと同様にIPの上位プロトコルトランスポート層
TCPに比べるとコネクションレス型プロトコルなので信頼性はないものの高速に転送できるまたはUDPヘッダサイズは8byte少ないことからその分アプリケーションデータを多く送受信することができる
パケット到達保証はないのでパットロスを考えてアプリを制作する必要がある
</details>

<details><summary>Heartbleed問題</summary>
OpenSSLへの「heartbeat拡張機能」の実装に大きな問題があった
「heartbeat拡張機能」とは、サーバーとクライアントの接続状態を維持するために用意された機能
外部からの要求に対して必要以上にデータを送信してしまい、メモリ上にあるデータが漏洩してしまう問題で、あたかも「心臓の鼓動＝heartbeat拡張機能」によって「血液が漏れ出る様子」に重ね合わせて「Heartbleed」と表現された
</details>

<details><summary>FISC(フィスク)</summary>
The Center for Financial Industry Information Systems
金融情報システムに関連する様々な問題についての調査研究を行う公益財団法人
</details>

<details><summary>ブルーグリーンデプロイメント</summary>
現状の本番環境（ブルー）とは別に新しい本番環境（グリーン）を構築した上で、ロードバランサーの接続先を切り替えるなどして新しい本番環境をリリースする運用方法
</details>

<details><summary>カナリアリリース</summary>
プロダクトやサービスの新機能を一部ユーザーのみが利用できるようにリリースし、新機能に問題がないことを確認しながら段階的に全体に向けて展開していくデプロイ手法
新バージョンにアクセスするユーザーを炭鉱で毒ガスを検知する「カナリア」に見立てて、この名称が付けられた。
</details>

<details><summary>A/Bテスト</summary>
元のページに対して変更を加えたテストパターンを用意し、ユーザーをそれぞれのページに振り分けどちらがより高いCVRを得られるのかを統計学で検証するWEB改善（CRO）の手法
</details>

<details><summary>cro</summary>
Conversion rate optimization
来訪した訪問者のコンバージョン(サイトの目的達成のこと)に至る率を高めるための施策
</details>

<details><summary>Unicode照合アルゴリズム</summary>
2つのUnicode文字列を比較するアルゴリズムを定義したものである。これによって言語的に正しい大文字小文字変換、ソートが行える
</details>

<details><summary>ベッターロックイン</summary>
特定ベンダー（メーカー）の独自技術に大きく依存した製品、サービス、システム等を採用した際に、他ベンダーの提供する同種の製品、サービス、システム等への乗り換えが困難になる現象のこと
</details>

<details><summary>フォールト　トレランス</summary>
その構成部品の一部が故障しても正常に処理を続行するシステム
</details>

<details><summary>SLA</summary>
Service Level Agreement(契約)
サービスを提供する事業者が契約者に対し、どの程度の品質を保証するかを明示したもの
</details>

<details><summary>DHCP</summary>
Dynamic Host Configuration Protocol
IPv4ネットワークにおいて通信用の基本的な設定を自動的に行うためのプロトコル
一般にIPv4での通信を行う際には、個々のホストに最低でも自身のIPv4アドレス、 サブネットマスク、デフォルトゲートウェイ、DNSサーバのアドレスを設定する必要があります。 ただ、このような設定をすべて手動で行おうとすると、 ホストの台数が増えるに従って手間が増えますし、間違いも起こりやすくなります。 これに対し、DHCPを利用すると、個々のホストはDHCPサーバに問い合わせをすることで、 各種設定に必要な情報を入手して、自動的に設定を行えるようになります。
</details>

<details><summary>ipアドレス 8.8.8.8</summary>
Googleが運営するGoogle Public DNS
</details>

<details><summary>cURL(カール)</summary>
さまざまなプロトコルを用いてデータを転送するライブラリとコマンドラインツールを提供するプロジェクト
基本的にはコンソール上でwebページを読み込みたい時に使う
</details>

<details><summary>フィンガープリント</summary>
元のデータをハッシュ関数に通した値のことを示す
またフィンガーの意味は指紋
改竄されているかどうかわかる仕組み
あるオブジェクトをハッシュ化する
オブジェクトとハッシュ化したものを送信する
送信先では送られてきたオブジェクトをハッシュ化して送られてきたハッシュ化された値を比較して
改竄されていないかを見分ける
</details>

<details><summary>スキーマー</summary>
型というみ
DBではrdmsなどで使われる用語
DBによって概念や定義が違うので汎用的にこれだと言えるスキーマーは存在しない
基本的にスキーマーがあるので処理が速くなったり遅くなったりする
</details>

<details><summary>レイテンシー</summary>
データ転送における代表的な指標
転送要求を出してから実際にデータが送られてくるまでに生じる、通信の遅延時間のことを指します
</details>

<details><summary>ランタイム</summary>
開発・実行の両方の機能を備えたソフトウェアから、開発の機能を省き、実効の機能のみを取り出したプログラムのこと
</details>

<details><summary>ワークロード</summary>
仕事量、作業負荷などの意味を持つ英単語。 ITの分野ではコンピュータやシステムにかかる処理の負荷の大きさを指すことが多い
</details>

<details><summary>モノリシック</summary>
一枚板全体が１つのモジュールで分解できないことをさす
</details>

<details><summary>ロギング</summary>
logを残すこと
</details>

<details><summary>イベントドリブン</summary>
利用者や外部の別のプログラムなどが引き起こす出来事に対応する処理を記述あるいは実行する方式のこと
</details>

<details><summary>シームレス</summary>
つなぎ目がないこと
wifiがあったら自動的に使用するなどはシームレスという
</details>

<details><summary>プロビジョニング</summary>
準備　提供　設備
顧客に対する技術やサービスの提供
</details>

<details><summary>オーケストレーション</summary>
コンピュータやアプリのサービスにおける設定や管理　調整の自動化
</details>

<details><summary>パーソナライズ</summary>
顧客全員に同じサービスやコンテンツを提供するのではなく個別に属性や履歴から
最適な情報を提供すること
</details>

<details><summary>データウェハウス</summary>
企業などの業務上発生した取引記録などのデータを
時系列に保管したデータベース
</details>

<details><summary>POP</summary>
Post Office Protocol
メール受診に使われるプロトコル
GCPの説明の二アンスはプロトコルではなくpopサーバーやPCからPOPで送信している場所ってことだと思う？
</details>

<details><summary>IP Anycast（エニーキャスト)</summary>
一意に割当てられる　IPアドレスを特定のサービスに対して共通に割当可能にするという技術
簡単にいうとサーバーが二つあってIPアドレスが同じでアクセスを分散できる

</details>

<details><summary>ネットワークトポロジ</summary>
通信ネットワーク上にコンピュータや制御器きがどのような携帯で接続されているかを示す。
</details>

<details><summary>インテグレーション</summary>
統合

</details>

<details><summary>jenkins</summary>
フリーでオープンソースの自動化サーバー
開発のビルドやテスト、デプロイをサポートする
</details>

<details><summary>RFC 1918</summary>
プライベートIPアドレスの範囲を定義しているもの
</details>

<details><summary>CI/CD</summary>
アプリの開発からテスト、提供、デプロイに至るまでのプロセス全体を継続的に統合、自動化、監視する手法
</details>

<details><summary>Bastion host　Jumpサーバー　踏み台インスタンス</summary>
インフラストラクチャの一つ
インスタンスやサーバーをメンテナンスしたい時に一度踏み台となるインスタンスやサーバーを経由する
事でセキュリティ面を向上させる。踏み台となるものはメンテナンスする以外はアクセスできず。また
メンテナンス先は踏み台からでしかアクセスできない。これによりアクセスする時間帯を減少させ
セキュリティの向上を図る
</details>

<details><summary>プリエンプティブ</summary>
マルチタスクOS上で実行されているプログラムを切り替えるときの方式
</details>

<details><summary>iops</summary>
秒当たりにディスクが処理できるI/Oアクセスの数のことです。
1回のI/O処理にかかる時間は、データ転送時間と平均アクセス時間とを足した数値となります。
このI/O処理が1秒当たり何回実行できるかの数値
</details>

<details><summary>スナップショット</summary>
全体をコピーしたもの
よくデータベースの複製などで使われる
</details>

<details><summary>LDAP</summary>
Lightweight Directory Access Protocol
ユーザーやコンピュータの情報を集中管理する「ディレクトリサービス」へのアクセス時に用いられるプロトコルの一つ
ディレクトリサービス（DB)の特徴
・読み取りが高速
・分散型の情報格納モデル
・高度な検索機能を持つ
例
DNSサーバー
</details>

<details><summary>プロキシ</summary>
代理という意味
イメージとしてはwebページを受け取る時に仲介役になってくれる
支払いサービスのpaypalみたいなもの
プロキシサーバーというサーバーを使ってサイトにアクセスすることで以下のようなメリットがある

・ログが取れる（誰がログインして何をしたかがわかる)
・ウィルスチェックができる
・匿名性の確保
・負荷分散

デメリットとして大きいのは
パスワードまでプロキシで確認できてしまうので情報が抜き取られ内容な対策が必要
</details>

<details><summary>redis</summary>
ネットワーク接続された永続化可能なインメモリデータベース。連想配列、リスト、セットなどのデータ構造を扱える。いわゆるNoSQLデータベースの一つ
</details>

<details><summary>クロスコミュニケーション</summary>
ユーザーに何をどう伝えるのかを視点に、そのために最適なメディアを選び、表現方法を設計するという発想。
</details>

<details><summary>フェイルオーバー</summary>
現用系コンピュータサーバ/システム/ネットワークで異常事態が発生したとき、
自動的に冗長な待機系コンピュータサーバ/システム/ネットワークに切り換える機能を意味する。
 これに対して、何らかの異常を察知して、人間が手動で切り替えを行うことをスイッチオーバー
</details>

<details><summary>IRC</summary>
Internet Relay Chat
インターネットを通じて複数の利用者がリアルタイムに文字メッセージを交換することができるチャットシステ
</details>

<details><summary>ダークリリース（ダークロンチ)</summary>
リリースと同時に機能を開放せずに別の方法で新機能を開放する手段を提供する
特定の条件下や特定の割合で新機能を試し、検証を行う
</details>

<details><summary>カスケード障害</summary>
一箇所の電力網が停電すると、接続している近隣の電力網の負荷も増え連動して停電してしまい、次から次へと停電地域が広がってしまう障害
</details>

<details><summary>オンデマンド</summary>
需要に応じて、または必要になった時だけ、行うこと。
</details>

<details><summary>フォールトトレラント</summary>
システムの一部に問題が生じても全体が機能停止するということなく（たとえ機能を縮小しても）動作し続けるようなシステムを設計するものである。
</details>

<details><summary>CDN(コンテンツデリバリネットワーク)</summary>
ウェブコンテンツをインターネット経由で配信するために最適化されたネットワークのことである
</details>

<details><summary>データストア</summary>
データベースのようなリポジトリだけでなく、単純なファイルや電子メールなどの単純なストアタイプも含む
データのコレクションを永続的に保存および管理するためのリポジトリ
</details>

<details><summary>BGP</summary>
Border Gateway Protocol
複数の独立したネットワークを接続したTCP/IPネットワークにおいて、ネットワーク間の経路情報を通信機器間で交換する手順を定めたプロトコル
</details>

<details><summary>インプレース</summary>
コンピューターシステムをアップグレードする際、既存の環境やデータを維持したまま、ソフトウエアを新規のものに入れ替えること。
</details>

<details><summary>ラックマウント</summary>
薄型のコンピュータを専用の棚(ラック)に積み上げるように設置すること。また、そのような形態のコンピュータ製品
</details>

<details><summary><レプリケート/summary>
ハードウェアを含め同じシステム環境が2セット（稼働系と待機系）用意され、
データ同期も図られているため、万が一、稼働系に障害が発生した時にも、待機系に切り替えるだけで業務を継続することができます
</details>

<details><summary>シャーディング</summary>
データを複数のサーバに分散させる機能です
</details>

<details><summary>スケーラビリティ</summary>
電気通信やソフトウェア工学において、システムまたはネットワークまたはアルゴリズムの
持つべき望ましい特性の1つで、一種の拡張性である。より具体的には、小規模なシステムを大規模にする場合に、
システム全体を交換する方法（建物で例えると大きな物件に引っ越すこと）では無く、
リソース（特にハードウェア）の追加によって大規模なものへと透過的に規模拡張できる能力
（建物で例えると、増築や別棟を建てること）はスケーラビリティの一種だといえる。

スケーラビリティの高さは様々な尺度で評価される。例として

規模透過性
負荷の高低に合わせてリソース・プールを拡大・縮小できること
位置透過性
ユーザーやリソースがどれだけ離れているか意識せずに、変わらない使い勝手でシステムが利用できること
異種透過性
システムを構成する機器やソフトウェアが異なっていることを意識せずに管理・利用できること
ケーラビリティについて議論する際には規模透過性のみを問題にすることも多い。
</details>

<details><summary>リードレプリカ</summary>
「リードレプリカ」は、アプライアンス「データベース」をマスターとする読み込み専用のデータベースサーバを作成する機能です。
SQLクライアント側では読み込みに特化し高速で参照可能なリードレプリカを接続先とすることで、
データ解析や分析など大量のデータを複雑なクエリで扱う処理においても
マスター側のデータベースに負荷をかけることなく実行することが可能となります。
</details>

<details><summary>垂直スケーリング</summary>
アプリを実行するハードウェアの能力を高めます。
これは、コードのリファクタリングを必要とせず、複雑な構成やものを作成する必要がないため
スケーリングする最も簡単な方法です。
ただし、垂直にスケーリングする場合にできることは限られています。 1台のサーバーで拡張できる容量には制限があります。
分かりやすい例えでいうと、高層ビルです。明らかに、建物を月まで垂直に拡大することはできません。
</details>

<details><summary>水平スケーリング</summary>
水平スケーリングは建物を高くしていくのではなく、複数の建物を建てるように、ハードウェアの数を増やしていきます。
トラフィックが多すぎて単一のハードウェアで処理できない場合、より多くのサーバーを取り込んで連携します。

これにより、システム全体の計算能力が向上します。増加したトラフィックは、増加した計算能力に簡単に対処できます。
また、無限のリソースがあると仮定した場合、水平方向に拡張できる量に文字通り制限はありません。

水平スケーリングは、事前計画と規定の時間を必要とする垂直スケーリングとは対照的に、ウェブサイトの
トラフィックが一定期間にわたって増減するときにリアルタイムで動的にスケーリングする機能を提供します。

クラウドコンピューティングが業界で非常に人気を博した最大の理由は、動的に拡大縮小できることです。
ウェブサイトが必要とするリソースに対してのみ支払うので、コスパも高いです。
</details>

<details><summary>オーケストレーション</summary>
コンピュータシステム、アプリケーション、およびサービスにおける、設定、管理、調整の自動化111
</details>

<details><summary>サンドボックス</summary>
砂場、砂箱という意味の英単語で、コンピュータの分野では、ソフトウェアの特殊な実行環境として用意された、
外部へのアクセスが厳しく制限された領域のことを指すことが多い
</details>

<details><summary>ドリブン</summary>
driveの過去分詞。 「～に突き動かされた」「～に駆り立てられる」
</details>

<details><summary>イベントドリブン</summary>
コンピュータプログラムの開発および実行方式の一つで、
利用者や外部の別のプログラムなどが引き起こす出来事に対応する形で処理を記述あるいは実行する方式
</details>

<details><summary>パッチ</summary>
pache
プログラムの一部分を更新してバグ修正や機能変更を行うもの
ゲームで改造するパッチはmodと呼ばれる
</details>

<details><summary>ホットキー</summary>
特定の機能を直接実行できるキー
もしくはキーの組み合わせ
</details>

<details><summary>etl</summary>
Extract/Transform/Load（略称：ETL）とは、データウェアハウスにおける以下のような工程を指す。

Extract - 外部の情報源からデータを抽出
Transform - 抽出したデータをビジネスでの必要に応じて変換・加工
Load - 最終的ターゲット（すなわちデータウェアハウス）に変換・加工済みのデータをロード
ETLは、データウェアハウスにデータを実際にロードする方法として重要である。ETLという用語はデータウェアハウスでのデータのロードだけでなく、任意のデータベースでのロード工程を指すこともある。ETLはレガシーシステムとの統合にも使われる。通常のETL実装は、処理についての監査証跡を記録する。ほとんど全ての設計において、この監査証跡は、元のデータが利用不可能な場合にETLの結果を再現できるほどの細粒度のレベルにはなっていない。
</details>

<details><summary>Pub/Sub</summary>
Publish/subscribe
パニッシャー　サブスクレイパー
</details>

<details><summary>acl</summary>
Access Control List
アクセス権限リストのこと
</details>

<details><summary>OpEx/CapEx</summary>
Operating expense　業務費や運営費のこと
CAPEX　expense　　　不動産や設備の価値を、維持する時にかかる費用のこと

</details>

<details><summary>tco</summary>
Total Cost of Ownership
コンピューターシステム構築の際にかかるハード・ソフトの導入費用から
運用後の維持費・管理費・人件費など全てを含む、システムの総所有コストを意味する
</details>

<details><summary>ファイアウォール インバウンド アウトバウンド</summary>
インバウンドファイアウォールの役割は
インターネットなどのネットワークセグメントから流入するトラフィックに対してネットワークを保護することだ。
具体的には、許可されていない接続、マルウェア、DoS攻撃などから保護する。

アウトバウンドファイアウォールの役割は、企業ネットワーク内部から流出するトラフィックを保護することだ。
</details>

<details><summary>レプリカサーバ スレーブ</summary>
レプリカ　＝　複製
スレーブ　＝　マスターの制御下

</details>

<details><summary>フェイルオーバー</summary>
現用系コンピュータサーバ/システム/ネットワークで異常事態が発生したとき、
自動的に冗長な待機系コンピュータサーバ/システム/ネットワークに切り換える機能を意味する
</details>

<details><summary>フリーミアム</summary>
フリーとプレミアムを合わせた造語
基本料金無料
</details>

<details><summary>ファラデーケージ</summary>
導体に囲まれた空間、またはそのような空間を作り出すために用いられる導体製の籠や器そのものを指す
</details>

<details><summary>TPM</summary>
Trusted Platform Module とは、コンピュータにおいて、
セキュリティに関する各種機能を備えたデバイスもしくはチップであり、国際標準規格のに則ったもの
</details>

<details><summary>J2E</summary>
Java 2 Platform, Enterprise Edition
「Java 2」の機能セットの1つ
企業の業務 システムや電子商取引などで使われるサーバに必要な機能をまとめた
エンタープライズシステム向けのJavaプラットフォーム
</details>

<details><summary>フラットファイルデータベース</summary>
「フラットファイル」とはプレーンテキストまたはテキストとバイナリの混合であり、
通常1行が1レコードになっている
レコード内はフィールドを区切り文字（デリミタ）で区切った構造になっており
例えばカンマで区切ったり、固定の文字数で区切ったりする
</details>

<details><summary>resize2fs</summary>
Linuxディストリビューションの標準　ソフトウェア
主にファイルシステムのメンテナンスやディスク容量変更を行える
</details>

<details><summary>PSI　DSS</summary>
payment card industry data security standard
クレジットカードの情報保護の情報セキュリティ基準
</details>

<details><summary>フェールオーバークラスタリング(WSFC)</summary>
Windows Server Failover Clustering
マイクロソフトのサーバ向けOS
複数のWindowsサーバーを束ねるクラスタリングを実現する
</details>

<details><summary>クラスタ</summary>
複数のコンピュータを連携させて一つの統合システムにすること
</details>


<details><summary>クラスタリング(クラスター分析)</summary>
分類対象の集合を内的結合と外的ぶんりが達せいされるような
部分集合に分割すること
</details>

<details><summary>SQL Server AlwaysOn</summary>
SQL Server2012から搭載された冗長化のための機能で
複数のSQL Serverのグループ（可用性グループ）を仮想的に
1台のSQL Serverのに見せ、グループのいずれか1台が正常に機能していれば
接続先からは正常に動いているように見せるという技術
</details>

<details><summary>KPI</summary>
Key Performance Indicator
重要業績評価指標という意味
KPIとは目標を達成する上で
その達成度合いを計測・監視するための定量的な指標
</details>

<details><summary>Rolling Update(ローリングアップデート)</summary>
同じ機能を持った複数のコンピュータで構成している場合のシステムを
アップデートする手法
システムの稼動状態を維持しながら
1台ずつ順番にアップデートを行っていく
</details>

<details><summary>HIPAA(Health Insurance Portability and Accountability Act of)</summary>
医療情報と電子化の促進に関するプライバシー保護やセキュリティ確保を
定めた法律

</details>

<details><summary>モダナイゼーション</summary>
近代化
稼働中の資産を生かしながら最新に
置き換えることを示す
</details>

<details><summary>NoOps</summary>
Mo Operationの略
人間によるシステム運用作業の最小化
</details>

<details><summary>NFS</summary>
ストレージ共有の仕組み
主にLInuxをはじめとするUNIX系が多いい
特徴としてネットワークシステムと呼ばれるようにネットワークを介してサーバー上のストレージ領域をローカルストレージと同様にマウントできる
</details>

<details><summary>レプリケーション</summary>
あるコンピュータやソフトウェアの管理するデータ集合の複製を別のコンピュータ上に作成し、リアルタイムに更新反映させて常に内容を同期する。これにより
耐障害性や可用性を高める
</details>

<details><summary>SCSI</summary>
Small Computer System Interface
スカジーという
主に周辺機器とコンピュータなどのハードウェア間のデータのやりとりを行うインタフェース規格

</details>

<details><summary>NVM Express</summary>
不揮発性ストレージメディアを接続するための論理デバイスインターフェースの規格であり、AHCIに代わる次世代の接続プロトコル規格
SSDなどに使用する
</details>

<details><summary>スループット</summary>
器や通信路などの性能を表す特性の一つで、単位時間あたりに処理できる量のこと
</details>

<details><summary>SSTable</summary>
ディスクに格納されたファイル
データファイルはデーターディレクトリーに格納されるがインストール時に場所が変わる
キースペース事にデータディレクトリないのディレクトリに各テーブルが格納されます
例
/data/ks1/cf1-5be396077b811e3a3ab9dc4b9ac088d/la-1-big-Data.dbはデータ・ファイルを表しています。
ks1は、ストリーミングまたは一括読み込みデータのキースペースを区別するキースペース名を表します。
この例の16進数文字列5be396077b811e3a3ab9dc4b9ac088dは、テーブル名に追加され、一意のテーブルIDを表します。
</details>

<details><summary>アドテック</summary>
AdTech
Advertising Technology（広告技術）を表す略称で、インターネット広告の技術を広く指す場合に使われる
</details>

<details><summary>フィンテック</summary>
金融（Finance）と技術（Technology）を組み合わせた造語で、金融サービスと情報技術を結びつけたさまざまな革新的な動きを示す
</details>

<details><summary>MapReduce(マップリデュース)</summary>
コンピュータ機器のクラスタ上での巨大なデータセットに対する分散コンピュータを支援する目的でGoogleによって2004年に導入されたプログラミングモデル
</details>

<details><summary>トラッキング</summary>
特定のユーザーが、サイト内でどこを閲覧しているのかを追跡、分析することである。 どこから来た人が（インターネット広告や検索エンジン）、どのようなページを見て（製品紹介・事例）、コンバージョン（資料請求・商品購入）に結びつくのかを追跡する
</details>

<details><summary>memcached</summary>
memory cache daemon
メモキャッシュと読む
分散型メモリキャッシュシステム
C言語
RDBMSが負荷を軽減したい時に使う。
データベースへの問合せ結果を一時的にキャッシュすることでデータベースへのアクセス回数を減らしスケーラビリティを向上させる
</details>

<details><summary>Redis</summary>
ネットーワーク接続された永続かなインメモリーデータベース。想配列、リスト、セットなどのデータ構造を扱える。いわゆるNoSQLデータベースの一つ
</details>


<details><summary>DBA</summary>
DataBase Adminstrator
データベース管理者
</details>


<details><summary>イテレーション</summary>
反復繰り返し
主にアジャイル開発で用いられる短期期間で反復しながら効率的に開発を進めるサイクルの一つ。
</details>

<details><summary>宣言型セキュリティ</summary>
Declarative Security
ロール、アクセス制御、認証の要求事項などを含むアプリケーションのセキュリティの構造をフォームとしてそのアプリケーションの外部に表記する手法をいう。ウェブ アプリケーションにおいて、デプロイメント ディスクリプタが宣言型セキュリティの主たる手段となる
</details>

<details><summary>デプロイメントディスクリプタ</summary>
Web アプリケーションの構成情報を記述するファイルであり、配備記述子とも呼ばれ
Web アプリケーション毎に1つ存在していたが近年では必ずしも使う必要がないが代わりにアノテーションを使用したりする。
実態はweb.xml
</details>

<details><summary>セキュリティポリシー</summary>
企業や組織におけるコンピューターのセキュリティに関する方針や行動指針のことである
</details>

<details><summary>QUIC</summary>
Quick UDP Internet Connections
Googleが開発している実験的なトランスポートレイヤーネットワークプロトコルで2013年より実装
</details>

<details><summary>HTTP/2</summary>
HTTP/１.1の問題を解決するために生まれた
Googleによって開発された？
最大の特徴はストーリーム概念を取り入れたこと
１つのコレクションないで同時に並列して複数のリクエストレスポンスを処理できる

</details>

<details><summary>ネットワークエッジ</summary>
通信ネットワークの末端にあたる領域。
外部のネットワークとの境界や、端末などが接続された、それ以上先がない端の部分
</details>

<details><summary>CIDR</summary>
Classless Inter-Domain Routing
クラスを使わないIPアドレスの割り当てと経路情報集成を行う技術。
</details>

<details><summary>クラスアドレス</summary>
IPアドレスをクラスに分けることによって使用したいサブネットマスクの値がわかる。
しかしクラスは一つの位でしか分けれないので
クラスA　0~
クラスB 10~
クラスC 110~
クラスD 1110~
となってしまい平等にクラスを分散することができない
</details>

<details><summary>ペアリング</summary>
一対の通信機器同士やネットワーク同士が互いに相手を認識・承認し、相互に通信を行える状態にすること
</details>

<details><summary>ラストワンマイル</summary>
家庭や企業のユーザーに通信のための接続を提供する最終工程であり、通信事業者の最寄の加入者局からユーザの建物までのネットワーク接続のための手段のこと
</details>

<details><summary>サフィックス</summary>
ファイルの拡張子やドメイン名の末尾に付けられれる識別子
</details>

<details><summary>CNAME</summary>
正規ホスト名に対する別名を定義するレコードです。
特定のホスト名を別のドメイン名に転送する時などに利用します
</details>

<details><summary>DSR</summary>
Dynamic Source Routing
ルーティングプロトコルの1つ
ネットワークインフラそのものや管理が不要で、自律的な無線ネットワークの構築が可能
</details>

<details><summary>NIC</summary>
Network Interface Card
</details>


<details><summary>NAT</summary>
NetWorkTranslation
ネットワークのアドレスを変換す技術
プライベートIPアドレスでは外部インターネットと通信できないので
プライベートIPアドレスをグローバルIPに変換することで外部と通信できる様にする

応用として
宛先を変換するDNATや
送信元を変更するSNATなどがある
</details>

<details><summary>PRT</summary>
Patner Relationship Management
大入店などのパートナー企業を使って使用品を販売するベンダー企業が
パートナー企業に情報を収集し、パフォーマンスをあげる戦略立案や
アクションに役立てるという考え方
</details>

<details><summary>deb</summary>
Debianなどで使われるフォーマット
</details>

<details><summary>Chef</summary>
ファイルに記述した設定内容に応じて自動的にユーザーの作成やパッケージのインストール、設定ファイルの編集などを行うツール
</details>

<details><summary>リモートプロシージャコール</summary>
ネットワークによって接続された他のPC上でプログラムを呼び出し実行させること
</details>

<details><summary>プロシージャ</summary>
プログラミングに置いて複数の処理を１つにまとめたももの
</details>

<details><summary>Webhook</summary>
webアプリケーションでイベントが実行された際に外部サービスにHTTPで通知する仕組み
</details>

<details><summary>パブリッシュ</summary>
情報提供者
送信者
</details>

<details><summary>サブスクレイパー</summary>
情報利用者
受信者
</details>

<details><summary>Apache Parquet</summary>
Apache Hadoopエコシステムの無料でオープンソースの列指向のデータストレージ形式です。これは、Hadoopで使用可能な他の列ストレージファイル形式、つまりRCFileとORCに似ています。これは、Hadoop環境のほとんどのデータ処理フレームワークと互換性があります。
</details>

<details><summary>ODBCドライバー</summary>
Open Database Connectivity (ODBC) は、関係データベース管理システム (RDBMS) にアクセスするための共通インタフェース (API)である。
</details>

<details><summary>JDBC</summary>
Java Database Connectivityの略で、Javaアプリケーションからデータベースを操作するAPIのことです。 JDKのコアAPIとしてjava.sqlパッケージに実装されています。

</details>

<details><summary>SSO</summary>
シングルサイオン
一度のユーザ認証処理によって独立した複数のソフトウェアシステム上のリソースが利用可能になる特性である。この特性によって、ユーザはシステムごとにユーザIDとパスワードの組を入力する必要がなくなる。
</details>

<details><summary>ロードバランサーL4</summary>
・レイヤー4の負荷分散が可能です。（IPアドレスとポート番号による負荷分散が可能）
　・10～2000Mbpsの帯域から選択が可能です。
　・標準で冗長化構成がされています。
　・安価で容易に導入が可能です。
　・サーバー保守、パッチ適用などのメンテナンス作業は不要です。
　・IPv6での通信が可能です。
</details>

<details><summary>ロードバランサーL7</summary>
・レイヤー7で負荷分散が可能です。 （URLやHTTPヘッダーで負荷分散が可能）
　・10Mbps～2Gbpsの帯域から選択可能です。
　・サーバー上に構築いただくソフトウエアロードバランサーとなります。
　・サービス利用時にe-small2以上のサーバー構築が必要で、お客様にてサーバー保守を実施していただく必要がございます。
　　（L7ロードバランサー利用料とは別にサーバー利用料が発生いたします）
</details>

<details><summary>デュアルホームホスト</summary>
ネットワークインターフェイスを2枚(以上)備えたホストコンピューター。また、TCP/IPにおいて、1つのインターフェイスに対して2つ(以上)のIPアドレスが割り当てられているホストのことを指す場合もある
</details>

<details><summary>ゼロデイ</summary>
ゼロデイ攻撃は、脆弱性が発見されて修正プログラムが提供される日より前にその脆弱性を攻略する攻撃のこと。ゼロデイ は脆弱性を解消する手段がない状態で脅威にさらされる状況をいう。
</details>

<details><summary>オプトイン</summary>
ユーザーに宣伝広告を配信する際、事前に許可を求めること。 また、宣伝広告の受け取りを、ユーザーが許可する意思を示すこと。 英語での表記はOpt-Inと表記し、「選択」という意味を持つ。
</details>

<details><summary>Spinnaker</summary>
近年素早いソフトウェアの改善改良の新機能追加が求められている(継続的デリバリ)
主に自動ビルド、テストなど
Spinnakerは、動画配信サービスを手がける米Netflixが2015年に公開したツール
Webブラウザ経由で操作するフロントエンド（Web UI）と、さまざまなクラウドインフラに対応するバックエンドの組み合わせで構築されている。GUIでデプロイを実行できるだけでなく、特定の処理の完了をトリガーに処理を実行するパイプライン機能が提供されているのが特徴
SpinnakerはAmazon Web Services（AWS）やGoogle Cloud Platform（GCP）といったパブリッククラウドで利用できるほか、KubernetesやOpenStackといったプライベートクラウド構築で使われている技術についてもサポートされている
</details>

<details><summary>フェデレーテッド</summary>
連ねた」「繋いだ」という意味。 つまり複数のクラウドサービスを組み合わせたもの、という意味だ。 同サービスでは、顧客の「プライベートクラウド」、日立の「マネージドクラウド」、さらにアマゾンのアマゾンウェブサービス（AWS）など日立の提携相手の「パートナークラウド」、の3つを繋いで使用できる
</details>

<details><summary>WebSocket</summary>
ンピュータネットワーク用の通信規格の1つである。ウェブアプリケーションにおいて、双方向通信を実現するための技術規格である
</details>

<details><summary>OLTP</summary>
オンライントランザクション処理
</details>

<details><summary>パーティショニング</summary>
分割
</details>

<details><summary>ライブマイグレーション</summary>
クライアントまたはアプリケーションを切断せずに実行中の仮想マシンまたはアプリケーションを異なる物理マシン間で移動するプロセス
</details>


<details><summary>カットオーバー</summary>
本番環境導入
</details>

<details><summary>ローンチ</summary>
新商品お披露目
</details>

<details><summary>リリース</summary>
納品
</details>

<details><summary>LVM</summary>
logical volume manager
論理ボリューム管理
論理ボリュームマネージャは、「物理ボリューム」を提供するハードディスクなどのストレージメディア・デバイスに、直接ファイルシステムをマップするのではなく、粗粒度のブロックにより一旦「論理ボリューム」と呼ばれる仮想化されたボリュームに束ねて利用するためのシステムである。
</details>

<details><summary>Blob</summary>
バイナリ・ラージ・オブジェクト
データベース管理システムにおいてバイナリデータを格納する場合のデータ型である。画像や音声、その他のマルチメディアオブジェクトがBLOBとして格納される
</details>

<details><summary>サニタイズ</summary>
例えば<br>の改行コードを無効にして<br>と表示する機能
</details>

<details><summary>PCI DSS</summary>
PCIデータセキュリティスタンダードは、 クレジットカード情報および取り引き情報を保護するために2004年12月、JCB・American Express・Discover・マスターカード・VISAの国際ペイメントブランド5社が共同で策定した、クレジット業界におけるグローバルセキュリティ基準である
</details>

<details><summary>RFC1918</summary>
プライベートIPアドレスによる接続の定義書？
</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>
