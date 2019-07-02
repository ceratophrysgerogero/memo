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

<details><summary>sass(scss)</summary>
インデント構文はメタ言語
sassと行ったらインデント構文のことをさすこともある
css3にはないものをcssで拡張できる
sassscriptでcssに変換する
scssはsass記法のものをsass3.0からcssぽく記述できるようにscss記法というので記述できるようになった。どちらも結果的にcssになる
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

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>
