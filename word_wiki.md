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
https://thinkit.co.jp/cert/article/0607/12/1/2.htm
</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>

<details><summary></summary>

</details>
