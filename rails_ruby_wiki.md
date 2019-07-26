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

`WARN Selenium [DEPRECATION] Selenium::WebDriver::Chrome#driver_path= is deprecated. Use ...`
#### 原因
基本的にタイポだと思っていい
たとえば`test`に`do`を入れわせれたりすると起きる


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

`db/development.sqlite3`
SQLiteのデータベースの実体
`db/schema.rb`
データベースの構造を追跡するファイル（スキーマ）

`db/migrate/.rb`
データベースを生成する際に必要となる設計図。
マイグレーションをするとその内容に基づいてデータテーブルを生成する

`test/fixutres/.yml`
事前に用意したテストデータを読み込み常にDBの内容を一定に保つ仕組み

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
scaffoldは基本的なファイルを多数作成する
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

`rails generate model コントローラー名（キャメル先頭大文字複数） 変数名:属性 変数名:属性`
モデル作成
db/migrate/〇〇.rb
app/models/コントローラー名.rb
test/models/コントロラー名_test.rb
test/fixtures/コントロラー名.yml

`rails generate migration add_index_to_users_email`
制作日_add_index_to_users_email.rbのファイル名でdb/migrateに追加する

インデックスの追加方法の例
```RuBy
class AddIndexToUsersEmail < ActiveRecord::Migration[5.0]
  def change
    add_index :users, :email, unique: true
    #usersテーブルのemailカラムにインデックスを追加する(add_index)
    #uniqueで一意性をつける
  end
end
```

`rails generate migration add_password_digest_to_users password_digest:string`
末尾をto_追加したいテーブル名にするとカラムに追加するマイグレーションが自動的にできるので良い
属性と型を引数に入れること手動で書かなくてもadd_columnを作成してくれる
以下上のコマンドで作成されるファイル内容
```RuBy
class AddPasswordDigestToUsers < ActiveRecord::Migration[5.0]
  def change
    add_column :users, :password_digest, :string
  end
end
```

`rails destroy  controller コントローラー名 アクション名１ アクション名２`
作成取り消しコマンド

`rails db:rollback`
dbを一つ前に戻す

`rails db:migrate VERSION=0`
dbを初期に戻す

`rails console --sandbox`
サウンドボックスモード
ここで行った全ての変更は終了時にロールバックされる
モデルはrequireしなくても読み込まれるので使用できる

## クラス
`ActiveRecord::Base`
OR Mapper
モデルとテーブルをつなぎ合わせることでrailsからテーブルのレコードにアクセスする役割

## メソッド


### model関連

```Ruby
validates :content, length: { maximum: 140 }, presence: true
```
app/models/micropost.rb
contentの長さを140までにする
`presence: ture`は空のみ禁止
全角空白にも対応している

---
```Ruby
validates :content, presence: true
```

app/models/micropost.rb
content空禁止
他のバリデーションと両立させる場合は,で区切って追加
全角対応

---
```RuBy
validates :email, uniqueness: true
一意性を検証する(大文字小文字の区別はしない)
大文字小文字を区別したいときは
validates :email, uniqueness: { case_sensitive: false}
```

```Ruby
VALID_EMAIL_REGEX = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i
validates :email, presence: true, length: { maximum: 255 },
                  format: { with: VALID_EMAIL_REGEX }
```
オプション引数(format)は正規表現（Regular Express)(regexと呼ばれる)を
使う場合に入れる

---
```RuBy
has_secure_password
```
モデル内にpassword_digest属性が含まれている時使用できる
またGamfileにbcryptを追加する
このメソッドをモデルに追加すると以下の機能が使える
* セキュアにハッシュ化したパスワードをデータベース内のpassword_deigestという属性に保存
* passwordとpassword_confirmationという二つの仮想的な属性が使えるようになる。また属性値と値が一致するかバリデーションも追加される
* authenticateメソッドが使える（引数の文字列がパスワードと一致するとそのオブジェクトを、間違っている場合はfalse)


---
```RuBy
app/models/user.rb
before_save { self.email = email.downcase }
```
オブジェクトが保存される時にemail属性を小文字に変換して保存する
before_saveはコールバックメソッド
右のselfは省略
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
`assert_select`

| Code | マッチするHTML |
|:-----------|:-----------
| assert_select "div" | ```<div>foobar</div>``` |
| assert_select "div", "foobar" | ```<div>foobar</div>```  |
| assert_select "div.nav"  | ```<div class="nav">foobar</div>```  |
| assert_select "div#profile"	  | ```<div id="profile">foobar</div>```　|
| assert_select "div[name=yo]"   | ```<div name="yo">hey</div>```  |
| assert_select "a[href=?]", ’/’, count: 1  | ```<a href="/">foo</a>```  |
| assert_select "a[href=?]", ’/’, text: "foo"	   | ```<a href="/">foo</a>```  |

デザインなどがかなり変わるのでテストする範囲はURLぐらいでいい鴨しれない

---
```RuBy
assert_template 'コントローラー名/アクション名'
```
そのviewファイルが使用されているかをチェックする

###　基本的にはどこでも使うメソッド

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
文字列を表示する

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
.valid?
```
オブジェクトが有効かどうか？
railsガイドから引用
>Railsは、Active Recordオブジェクトを保存する直前にバリデーションを実行します。バリデーションで何らかのエラーが発生すると、オブジェクトを保存しません。
>ただし、newでインスタンス化されたオブジェクトは、それが厳密には無効であってもエラーは出力されないので、注意が必要です。これは、createやsaveメソッドなどによってオブジェクトが保存されるときのみ、バリデーションが自動的に実行されるためです。

valid?メソッドを使って、バリデーションを手動でトリガすることもできます。valid?を実行するとバリデーションがトリガされ、オブジェクトにエラーがない場合はtrueが返され、そうでなければfalseが返されます。

`app/models`で記載された`validate`or`validates`の内容を参照し評価する

---
```RuBy
.find(:id値)
```
id以外の検索はできない
idはpramsなどで持ってくる

---
```RuBy
params[:id]
```
getやpostで送られてきた値を受け渡しメソッド
（リンク、フォームによるパラメータの受け渡し)

リンクによるパラメータの受け渡し

ビュー
```RuBy
link_to 'ユーザ名', :controller => 'users', :action => 'show', :id => 1
```

コントローラー
```RuBy
def show
  id = params[:id] # id = 1
end
```

フォームによるパラメータの受け渡し

ビュー
```rails5
<% form_for @user do |f| -%>
  名前：<%= f.text_field :name %>
  説明：<%= f.text_area :body %>
<% end -%>
```

コントローラ
```ruby
def create
  name = params[:name]
  body =  params[:body]
end
```

ファイルの取得などもできる
```Ruby
params[:パラメータ名].original_filename
```

---
```RuBy
.find_by(カラム名: データ)
```
複数検索できる
属性で検索できる

---
```RuBy
.update(カラム: データ)
```
update_attributesのエイリアス
複数のカラムを変更する
またvalidationを行う

---
```RuBy
.save
オブジェクトの全てを保存する
基本的にインスタンスを生成し新しくDBに保存する際に使用する方がいい
更新などで使用するとエラーになる
更新にはupdate(update_attributes)を使用する
```

---
```RuBy
.update_attribute
```
一つのカラムを更新する
validationを行わない


---
```RuBy
.update_attributes
updateの別名（エイリアス）
複数のカラムを更新できる
validationを行う
更新の際はこちらを使う方が良い
```


---
```RuBy
def setup
end
```
`setup`に記載された内容は各テストが走る直前に実行される
変数などを宣言する場合はここで宣言した方が良いだろう


---
```RuBy
.dup
```
レシーバのオブジェクトのコピーを作成し返す
シャローコピーのためオブジェクトの参照先までコピーはできない（同じ参照先を見てしまう）
参照先までコピーしたい場合はrailsの`deep_dup`メソッドを使用する

---
```RuBy
ローマ字文字列.upcase
```
ローマ字で記載されている部分を全て大文字に置き換える

---
```RuBy
y
```
require 'yaml' すると、Kernel#y メソッドが追加され、y obj で YAML 形式で Object の中身を見ることができます。

```RuBy
.to_yaml
```

も同じ挙動することからエイリアスだと考えられる

---
```Ruby
pp
```
オブジェクトなどを見やすく出力するライブラリまたはメソッド


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
modlue ApplicationHelper
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
`<%#= image_tag("kitten.jpg", alt: "Kitten") %>`
`#`を入れる
---

パーシャル
`<%= render 'layouts/shim' %>`
この行では`app/views/layouts/_shim.html.erb` というファイルを探し、結果をビューに挿入する
パーシャル用ディレクトりはsharedディレクトリがよく使用される

---
`名前付きルート`
パスヘルパーやURLヘルパーと呼ばれる
ヘルパーを使用することで可読性が上がる
SQLインゼクション対策にも繋がる

以下の参考資料がかなり参考になった
参考:[名前付きルートを使用する利点](https://ryoutaku-jo.hatenablog.com/entry/2019/05/05/%E5%90%8D%E5%89%8D%E4%BB%98%E3%81%8D%E3%83%AB%E3%83%BC%E3%83%88%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%99%E3%82%8B%E5%88%A9%E7%82%B9)
```RuBy
 get '/アクション名', to:'コントローラー名#アクション名'
```
をrootes.rbで宣言するとアクション名_pathやアクション名_urlという変数が使えるようになる
また'as:'オプションで名前つきルートを変更することができる
```RuBy
get ':username', to: 'users#show', as: :user
```
上記ではuser_pathが生成されコントローラ・ヘルパー・ビューで使えるようになる



---
`Active Record`
RailsでデータベースとやりとりするデフォルトライブラリはActive Record

---

`モデルのバリデーションについて`
`app/models/``
の中に
```RuBy
validates :name, presence: true
```
などを記載する
データが入った変数に`vaild?`　メソッドを使用すると上記で作成した`validates`のオプションを読み込み
バリデーションチェックをする
また、パリデーションに通らなかった場合eroorsオブジェクトを生成してくれるので
`変数.errors.full_messages`などで確認できる


---

`Ruby%記法`

`%()`
ダブルクオート
`%q()`
シングルクオート

---
`%w`
```RuBy
array = %w(one two three for)
p array　=> ["one", "two", "three", "four"]
```
 配列作成

---
`%W`
```RuBy
ruby = 'Ruby'
PYTHON = 'Python'

array = %W(#{ruby} #{PYTHON} PHP)
p array
# => ["Ruby", "Python", "PHP"]
```
式展開配列作成

---
`%i`
```RuBy
array = %i(Ruby Python PHP)
p array
# => [:Ruby, :Python, :PHP]
```

---
`サイトのレイアウトにデバック情報を追加する`
```rails5
<%= debug(params) if Rails.env.development? %>
```
開発環境だけに表示される
Rails.env.development?この分は開発環境かどうかをtrue or falseで返り値をだす
---
```RuBy

```
```RuBy

```


### 豆知識
ほとんどのデータベースは文字列の上限を255としている

メールアドレスのうちドメイン部分だけが大小文字の区別はしない
foo@bar.comとfoo@BAR.comは同じ
Foo@bar.comとfoo@bar.comは本来別アドレス
現実では大文字と小文字を区別するメールサービスやISPは滅多にない
なぜなら区別をしてしまうと相互運用性の問題などが発生してしまうからだ
