Rails Ruby wiki
## 実際に詰まったエラー
`rails aborted! StandardError: An error has occurred, this and all later migrations canceled~~.....`
#### 原因
このエラーは既にテーブルが存在する場合に発生します。
またこのエラーはgitの差分破棄では治りません
#### 解決策
以下のコマンドでmigrateをリセットする
`rake db:migrate:reset`
再度マイグレーションを実行する
`rake db:migrate`


## ファイルやフォルダ解説
`gemspec`
gemの依存関係を記述する

`gemfile`
依存するgemの取得先を記述している

`Gemfile.lock`
開発環境と運用カントで同じgemをインストールする時に使用する  

`_helper.rb`
app/helpers/ビューに対応したコントロラー名.rb
ここで記載したメソッドは対応したビューで使用できる

`app/assets`
imgやjs、css（stylesheets)などはこのファイル以下に存在する
htmlで描画するときはアセットパイプラインを通して行う
アセットパイプラインを通すとassets以下のフォルダはブラウザ場では見えなくなり
全てassets直下に置いてあるかのごとく見える
またimgは適当なランダムな数字のファイル名になる
これはimgを更新したキャッシュしている

`app/views/layouts/_shim.html.erb etc`
先頭にアンダースコアがあるファイルはパーシャルで使う普遍的な命名規約です

`app/assets`
現在のアプリケーション固有のアセット
`lib/assets`
あなたの開発チームによって作成されたライブラリ用のアセット
`vender/assets`
サードパーティのアセット

## コマンド  

`bundle update`
gemfile.lockを更新する

`bundle install`
gemfile.lockを元にインストール


`rails railsのバージョン new アプリ名`
新規プロジェクト作成

`rails server`
railsアプリケーションを起動する

`rails generate scaffold モデル名(単数) カラム名1:データ型1, カラム名2:データ型2`
モデル名は単数形で生成されコントローラーは複数形で生成される
マイグレーション
モデル
コントローラー（index show new edit create update destroy アクションを作成)
ルーティング追加
コントローラーで適宜されたアクションに対応するビュー
が生成される
注意：テーブルの作成はしてないので`rails db:migrate`を忘れないこと

`rails generate controller コントローラー名（キャメル先頭大文字複数） アクション名1 アクション名２`
コントローラー
アクションルート
アクションにそったビュー
テスト
ヘルパー
coffee
css
の生成

`rails destroy  controller コントローラー名 アクション名１ アクション名２`
作成取り消しコマンド

`rails db:rollback`
dbを一つ前に戻す

`rails db:migrate VERSION=0`
dbを初期に戻す

## メソッド

```Ruby
validates :content, length: { maximum: 140 }, presence: true
```
app/models/micropost.rb
contentの長さを140までにする

---
```Ruby
validates :content, presence: true
```

app/models/micropost.rb
content空禁止
他のバリデーションと両立させる場合は,で区切って追加

---
```Ruby
has_many :microposts
```
app/models/user.rb
userモデルは、複数のmicropostsを所持する（関連づける）
`belongs_to :user`
app/models/micropost.rb
micropostモデルは一つのuserをもつ（関連づける）
関連づけが完了すると以下のようにUserクラスからファースト
ユーサーのマイクロポストを取得できるようになる
User.first.microposts.first.user

---
```Ruby
resources :microposts
```

config/routes.rb
以下のルーティングをその一行だけで代用できる

| HTTPリクエスト | URL | アクション | 用途 |
|:-----------|:----------- |:----------- |:-----------
| GET | /microposts | index | 全てのマイクロポストページを表示する |
| GET | /microposts/1  | show | id=1のマイクロポストを表示するページ  |
| GET  | /microposts/new  | new  | マイクロポストを新規作成するページ  |
| POST  | /microposts  | create  | マイクロポストを新規作成するアクション  |
| GET   | /microposts/1/edit  | edit  | マイクロポストを編集するページ  |
| PATCH  | /microposts/1  | update  | id=1のマイクロポストを更新するアクション  |
| DELETE   | /microposts/1  | destroy   |  id1のマイクロポストを削除する  |

複数ではない場合は`resource :micropost`

`root 'コントローラー#アクション'`

---
```Ruby
assert_response :success
```
http 200 OK
リクエストは成功し、レスポンスとともに要求に応じた情報を返せた

---
```Ruby
assert_select "htmlタグ","タグ内に記載されて欲しい記述"
```
指定したタグ内に記載されて欲しい記述があるかどうかチェックする

---
```Ruby
yield
```
処理された内容を埋め込む先を指定する
`provide`で指定された内容や共通なレンタリング（application.html.erbを使用して）を使いそれぞれのビューをレンタリングする際に使用する
application.html.erbで`<%= yield %>`と使用すると各ページの内容がここで挿入される
`provide`で指定された場合は`<%= yield(:タグ名) %> `と記述することで文字通り`provide`提供された物を`yield`産出することができる

---
```Ruby
provide(:タグ名, "yieldに入れたい内容")
```
個別レイアウトから共通レイアウトに画面を表示する際に使う
`content_for`と同じ挙動だが`content_for`ではアセットパイプラインがうまく動作しなかったりrailsのストリーミングの挙動が違ったりする
参照 [content_forとprovideの違い](https://qiita.com/pochi355/items/02dd10e32bf5034b383b)
基本は`provide`を使用して問題ない


---
```RuBy
empty?
```
文字列が空
文字列ならtrue
空でなければfalse


---
```RuBy
nil?
```
オブジェクトがnilならtrue
違うならfalse

---
```RuBy
to_s
```
オブジェクトを文字列に変換

---
```RuBy
配列.puts
```
文字列を表示
自動で改行される(\n)
```RuBy
"foo bar   baz".split
=>["foo","bar","baz"]

"fooxbarxbaz".split('x')
=> ["foo", "bar", "baz"]
```
文字列を配列に分割する

---
```RuBy
配列.puhs(プッシュしたい値)
```
配列に追加する

---
```RuBy
配列.join
```
連結する
```RuBy
a
[42, 8, 17, 6, 7, "foo", "bar"]
a.join                       # 単純に連結する
=>"4281767foobar"
a.join(', ')                 # カンマ+スペースを使って連結する
=> "42, 8, 17, 6, 7, foo, bar"
```

---
```RuBy
配列.map { |m| 処理}
```
要素数だけブロックを実行し、ブロックの戻り値で返す。
ブロックの戻り値がないときはnilを渡す
例
```RuBy
[1,1,1,2,3,4].map { |n| n*3 if n==1  }
=> [3,3,3,nil,nil,nil]
```
---
```RuBy
配列.each{ |n| 処理}
```
配列の要素だけブロックを実行する。繰り返しごとにブロックの引数に各要素の順が入る
戻り値はレシーバー
例
```RuBy
[1,2,3].each { |n| n*2}
=> [1,2,3]
```

---
```RuBy
puts "aaa".inspect
=>"aaa"
```
文字列を返す

---
```RuBy
p :name # 'puts :name.inspect'と同じ
=> :name
```
オブジェクトを表示することはよくあるのでショートカットPメソッドがある



---
```RuBy
attr_accessor :name, :email
```
nameとemailのアクセッサー（ゲッターとセッター）を作成する
早い話インスタンス 変数`@name`や`@email`にアクセスできるようになる

---
```RuBy
def initialize(attributes = {})
  @name  = attributes[:name]
  @email = attributes[:email]
end
```
クラスをnewした時に実行されるメソッド

---
```RuBy
link_to("文字", 'パス',class: "")
```
リンクを貼る

```RuBy
link_to image_tag("ファイル名",alt: "")
```
画像を貼る

---
```RuBy
require 'カレントディレクトリからの相対パス'
```
ライブラリやファイル読み込みに使う
ファイルの拡張子は必要ない

---
```RuBy

```

---
```RuBy

```

## gemfile(パッケージ)
デフォ

---
デフォ以外
`gem 'minitest-reporters'`
test/test_helper.rb
require "minitest/reporters"
Minitest::Reporters.use!
testが見やすくなる




## その他ジャンル別にまとめられなかったもの
`rake`
rails4まではrailsとrakeコマンドは別れていたがrails5になってからrailsでもrakeを実行できるようになった

---
`spring`
rails4.1から標準で付属したアプリケーションプリローダー

---
`テンプレート`
railsでのテンプレートはビューをさす

---
`デフォルト式あり引数`
```Ruby
def f2(a, b = "", c = [])
  p [a, b, c]
end
```
結果
```Ruby
f2(42, "answer", [4, 8, 10]) # => [42, "answer", [4, 8, 10]]
```

---
`#{}`
式展開

---
`ダブルクォートとシングルクォートの違い`
""と''は基本は同じだがシングルクォートでは式展開ができない
特殊な#などの文字を使用したい場合\を使用する必要がある
＊明確な理由もなく両者を混用して者も多いい


---
`シングルクォートの使い方`
特殊文字をシングルクォートで囲むと文字列として使用できる形に容易に変換できる
```RuBy
'\n'=>"\\n"
```

---
`unless`
ifの逆バーション
もし評価がfalseであれば実行する

---
`?`
期待値がboolena型であるメソッドは文末に疑問符を示す習慣がある
例 〇〇.empty?

---
`!!`
オブジェクトの評価を二回否定する
使用例 オブジェクトを論理値に変換できる
```RuBy
nil => nil
!nil => ture
!!nil => false
```

---
`暗黙の戻り値`
rubyでは最後の式の評価が返り値になる
```RuBy
def string_message(str = '')
   return "It's an empty string!" if str.empty?
   return "The string is nonempty."
 end
```
この二行目の`return`は無くても動作する（わかりにくいので`return`を使用した方が望ましい)

`早期return`
```RuBy
def isXXX?(arg)
  return false if arg.nil?
  return false if arg == 'hoge'
  return true;
end
```

---
`モジュールヘルパーについて`
```RuBy
modlue ApplicationHelper`
```

rubyではモジュールを使用するために`include`メソッドを使用してモジュールを組み込まなくてはならないがrailsでは自動的にヘルパーモジュールを読み込んでくれるのでincludeする必要はない
＊コントローラーは全部のヘルパーをインクルードするがビューはコントローラ名と
同名のヘルパーしか読み込まない
参考：[viewから使えるhelperはデフォルトでController名と同じやつ](https://qiita.com/ppworks/items/b6bb04e9235fd75ec341)

---
`レシーバーに処理した内容を代入する場合`
メソッドの後に!を入れることでレシーバーに代入できる
```RuBy
a = [42,8,17]
a.sort => [8,17,42]
a => [42,8,17]
a.sort! => [8,17,42]
a => [8,17,42]
```

---
`ブロック`
```RuBy
(1..5).each { |i| puts 2 * i }
```
または
```RuBy
(1..5).each do |i|
  puts 2 * i
end
```
の記述でもできる前者は処理内容が短い時、後者は、長い時に使うといいだろう

---

`ハッシュとシンボル`
ハッシュはキーと値のペアを波括弧うで囲んで表記する
決してブロックの波括弧ではない
ハッシュは並び順が保証されない
順序が必要なら配列を使用する

```RuBy
user = {} #{}は空のハッシュ
user["aaa"] = "bbb" #キーが"aaa"で値が"bbb"
user["ccc"] = "ddd"
user
=> {"aaa"=>"bbb", "ccc"=>"ddd"}
userid = { "eee"=>"fff", "ggg"=>"hhh" } #複数の宣言 最初と最後に空白を入れる習慣がある
```
ハッシュのキーは通常文字列では無くシンボルを使うのが普通
シンボルは特定の文字(barなど)を使用することができない
```RuBy
user1 = { :name => "Michael", :email => "mishael@exaple.com"}
user1[:name]
=> "Michael"
user1[:pass]
=>nil
#シンボルとハッシュロケットの組み合わせ表現
user2 = { name: "Michael", email: "mishael@exaple.com"}
user1 == user2
=> true
＊ :name => と　name:　は同じ意味
```
ハッシュの中にハッシュを入れることもできる
```RuBy
params = {}
params[:user] = { name: "Michael", email: "mishael@exaple.com"}
params
=> {:user=>{:name=>"Michael",:email=>"mishael@exaple.com"}}
params[:user][:name]
=>"Michael"
```
eachメソッドも使用できる
```RuBy
flash = { success: "It worked!", danger: "It failed." }
flash.each do |key, value|　#キーと値の両方を変数に入れる必要がある
   puts "Key #{key.inspect} has value #{value.inspect}"
end
Key :success has value "It worked!"
Key :danger has value "It failed."
```

---

`メソッドに()は省略可能`
```RuBy
stylesheet_link_tag('application', media: 'all',
                                   'data-turbolinks-track': 'reload')
stylesheet_link_tag 'application', media: 'all',
　　　　　　　　　　　　　　　　　　　　　'data-turbolinks-track': 'reload'

```
`ハッシュがメソッドの呼び出しの最後の引数である場合波括弧を省略できる`
```RuBy
stylesheet_link_tag 'application', { media: 'all',
                                     'data-turbolinks-track': 'reload' }
stylesheet_link_tag 'application', media: 'all',
                                   'data-turbolinks-track': 'reload'
```

---
`コンストラクタ`
クラスインスタンス 生成時に実行されるメソッド
暗黙のリテラルコンストラクタ
```RuBy
s = "foobar"       # ダブルクォートは実は文字列のコンストラクタ
s.class
=> String
```
明示的に名前つきコンストラクタの使用
```RuBy
s = String.new("foobar")   # 文字列の名前付きコンストラクタ
s.class
=> String
s == "foobar"
=> true
```
ハッシュの場合は違う
```RuBy
h = Hash.new
=>{}
h[:hoo] #存在しないキー
=>nil
h= Hash.new(0)　#存在しないキーのデフォルト値を0にする
=>{}
h[:foo]
=> 0

```

---
`埋め込みルビーコメントアウト`
```RuBy
<%#= image_tag("kitten.jpg", alt: "Kitten") %>
```
`#`を入れる

---
`パーシャル`
```RuBy
<%= render 'layouts/shim' %>
```
この行ではapp/views/layouts/_shim.html.erbというファイルを探し、結果をビューに挿入する
パーシャル用ディレクトりはsharedディレクトリがよく使用される
```RuBy

```
```RuBy

```
```RuBy

```
```RuBy

```
```RuBy

```
```RuBy

```
```RuBy

```
```RuBy

```
