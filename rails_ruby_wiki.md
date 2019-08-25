Rails Ruby wiki
## 詰まったエラー
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

`Expected "poGFEr-zpie0SuBn1jkkfg" to be empty.`
""の中身が毎回変わるのであればクッキーやセッションなどを疑う
またからだと言われる場合は、どこかで必要なものを無くしている可能性がある


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

`test/test_helper.rb`
テスト用のヘルパー
本来のヘルパーメソッドはテストからでは呼び出せないのでここに定義すると良い

`app/views/shared`
複数のビューで使われるパーシャルはこのディレクトリによく置かれる
パーシャルのビューは`_`を先頭につける
よく
```rails
<% render 'shared/error_messages' %>
```
 とform_forの中で記載される

`config/environments/production.rb`
本番環境のRailsコンポーネント設定

`config/puma.rb`
rails5からPumaのデフォルトの設定で使えるようになった
なので最初からpumaのファイルが存在している
使いたいときはpuma gemをGeamfileに追加する

`app/assets/javascripts/application.js`
`app/assets/javascripts/application.css`
マニフェストファイルと呼ばれる
jsやcssをまとめてアセプトパイプラインとして利用する
参考:[Railsのマニフェストファイルを使ったJsとStylesheetの呼び出し](https://qiita.com/samurairunner/items/da22eddb64e867b4e145)

`test/fixtures/users.yml`
fixturesにはテスト用のデータを入れておく
例えばDBで呼び出すuserを作成したいなら以下のようにする
```Rails
michael:
  name: Michael Example
  email: michael@example.com
  password_digest: <%= User.digest('password') %>
```
ハッシュ化されていないパスワードはfixturesには入れられない
またDBにはハッシュ化されていないカラムは存在しないのでエラーになる
実際にはpassword_digestという属性にパスワードのハッシュ化されたパスワードが入っているので
digestメソッドをユーザーモデルに作成してハッシュ化したパスワードを入れておく
ERbコードを使用できる点は覚えておくと良い

なおユーザーmishaelの呼び出し方は
```RuBy
user = users(:mishael)
```
シンボルで見つけられる(test環境のみ)
def set
end
に書いておくとクラス呼び出しの際に呼ばれるので良いだろう

```RuBy
```

## コマンド  

`bundle update`
gemfile.lockを更新する

`bundle install`
gemfile.lockを元にインストール


`rails railsのバージョン new アプリ名`
新規プロジェクト作成

`rails server`
railsアプリケーションを起動する

`rails routes`
現在のルーティングを確認する
`rails routes | grep users#`
とすることで表示制限できる

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
アクション名を書かないとcreateやdestroyなどが作られてしまう

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
カラムの追加をする
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

`rails generate integration_test article`
統合テストtest/integration/article_test.rbを作成する

`rails destroy  controller コントローラー名 アクション名１ アクション名２`
作成取り消しコマンド

`rails db:migrate`
マイグレーションを順番に実行してデータベースに変更を加える

`rails db:migrate:status`
ステータスの確認

`rails db:rollback`
dbを一つ前に戻す(migrationファイル1つ分)
**change_columnはロールバックできない**

`rails db:migrate VERSION=0`
dbを初期に戻す

`rails db:reset`
db/schema.rbからDBの作成
現在のDB破棄してschema.rbからをDBを作成

`rails db:migrate:reset`
databaseを一度削除してもう一度作成し、db:migrate実行
カラムの修正やオプション修正をした時はこちらを使用しないと修正内容を適用できない

`rails console --sandbox`
サウンドボックスモード
ここで行った全ての変更は終了時にロールバックされる

## クラス
`ActiveRecord::Base`
OR Mapper
モデルとテーブルをつなぎ合わせることでrailsからテーブルのレコードにアクセスする役割
rails起動の際にデータベースにアクセスしてクラス名を元に対応するテーブル構造を
読み取り自動で対応するゲッターセッターを作成する（attr_accessorが必要ない)

`ApplicationController`
railsのコントローラーはこれを継承するrubyクラス
また`ActiveRecord::Base`を継承している
アプリケーションがブラウザからのリクエストを受け取るとルーティングによって
コントローラとアクションが指定され、railsはそれに応じてコントローラのインスタンスを生成して
アクション名と同じ名前のメソッドを実行する
インスタンス変数を宣言するときはイニシャライズ（new)に記載すること
```RuBy
def new
  @user = user
end
```


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
resource :users
```

config/routes.rb
以下のルーティングをその一行だけで代用できる

| HTTPリクエスト | URL | アクション | 名前つきルート | 用途 |
|:-----------|:----------- |:----------- |:----------- |:-----------
| GET | /users | index | users_path | 全てのユーザーを一覧にするページを表示する |
| GET | /users/1  | show | user_path(user) | 特定のユーザーを表示するページ  |
| GET  | /users/new  | new  | new_user_path | ユーザーを新規作成するページ（登録) |
| POST  | /users  | create | users_path | ユーザーを新規作成するアクション  |
| GET   | /users/1/edit  | edit | edit_user_path(user) | id=1のユーザーを編集するページ  |
| PATCH  | /users/1  | update | user_path(user) |  ユーザーを更新するアクション  |
| DELETE   | /users/1  | destroy | user_path(user) |  ユーザーを削除するアクション  |

複数ではない場合は`resource :micropost`
users_urlといった_url系もこれでresourceで定義できている
確認したければこちらのURL参照
[デベロッパー環境でアクセス](http://localhost:3000/rails/info/routes#)
`root 'コントローラー#アクション'`


## 主にテスト

---
```Ruby
assert_response :success
```
http 200 OK
リクエストは成功し、レスポンスとともに要求に応じた情報を返せた

---
`assert_select`

参考:[assert_selectの使い方](https://zariganitosh.hatenablog.jp/entry/20080405/1207455670)

| Code | マッチするHTML |
|:-----------|:-----------
| assert_select "div" | ```<div>foobar</div>``` |
| assert_select "div", "foobar" | ```<div>foobar</div>```  |
| assert_select "div.nav"  | ```<div class="nav">foobar</div>```  |
| assert_select "div#profile"	  | ```<div id="profile">foobar</div>```　|
| assert_select "div[name=yo]"   | ```<div name="yo">hey</div>```  |
| assert_select "a[href=?]", ’/’, count: 1  | ```<a href="/">foo</a>```  |
| assert_select "a[href=?]", ’/’, text: "foo"	   | ```<a href="/">foo</a>```  |


またアクションの確認もできる
`assert_select 'form[action="/signup"]'`
デザインなどがかなり変わるのでテストする範囲はURLぐらいでいいかもしれない

名前付きルートでも確認できるぞ
```RuBy
assert_select "a[href=?]", user_path(@user), count: 0
```

---
```RuBy
assert_template 'コントローラー名/アクション名'
```
そのviewファイルが使用されているかをチェックする

---
```RuBy
assert_no_difference 'User.count' do
  post users_path, params: { user: { name:  "",
                                     email: "user@invalid",
                                     password:              "foo",
                                     password_confirmation: "bar" } }
end
```
式を評価した結果の数値は、ブロックで渡されたものを呼び出す前と呼び出した後で違いがないと主張する。
以下と等価

```Ruby
before_count = User.count
post users_path, ...
after_count  = User.count
assert_equal before_count, after_count
```


---
```RuBy
assert_difference 'User.count',1 do
end
```
ブロックを実行した直前と直後の第一引数を比較して
差異を第二引数と比較します

---
```RuBy
assert_redirected_to @user
```
最後に実行されたアクションで呼びされたリダイレクトと一致するか
(リダイレクトするわけではない)
```RuBy
@userは以下のように省略できる
#/users/:idへのリダイレクトを、相対パスで指定する(1)
redirect_to("/users/#{@user.id}")     

#/users/:idへのリダイレクトを、絶対パスで指定する(2)
redirect_to("https://228e5b796b37495aa0c17e02856dccfa.vfs.cloud9.us-east-2.amazonaws.com/users/#{@user.id}")

#/users/:idへのリダイレクトを、user_url(id)ヘルパーを使って、絶対パスで指定する(3)
redirect_to(user_url(@user.id))    

#リンクのパスとしてモデルオブジェクトが渡されると自動でidにリンクされるので、.idを省略する(4)
redirect_to(user_url(@user))                            

#_urlヘルパーは、省略できる(5)
redirect_to(@user)                     

#Rubyでは、()は省略できる(6)
redirect_to @user
```
参照:[redirect_to @userが何を省略しているかわかりますか？](https://qiita.com/Kawanji01/items/96fff507ed2f75403ecb)


---
```RuBy
assert_equal 期待値　実際の値
```

---
```RuBy
follow_redirect!
```
postリクエスト送信した結果をみて指定されたリダイレクト先に移動するメソッド



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

```RuBy
flash.now[:danger] = 'invalid email/password conmbination'
```
ハッシュで管理します
ビュー側では

```rails5
<%= flash[:danger] %>
```
で表示できる
`now`をつけることで今のアクションのみ有効にできる
有効期限が欲しいなら`keep`がある

参考 [lashメッセージの使い方とメッセ....](https://pg-happy.jp/rails-flash-message.html)

---
```RuBy
empty?
```
空ならtrue
何か入っていたらfalse
エラーオブジェクトにも使える

---
```RuBy
any?
```
要素が１つでもあればfalse
なければtrue
empty?と逆

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
利用用途としては読み書きを行いたいオブジェクト属性を定義したい時に使うと良い
型は動的に変わる（代入した型になる）
参考:[attr_accessorって？1](https://qiita.com/Hassan/items/0e034a1d42b2335936e6)
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
DBを検索する
id以外の検索はできない
idはpramsなどで持ってくる
検索できないIDだと例外処理

```RuBy
.find_by(カラム名: データ)
```
DBを検索する
カラムによる条件指定で複数レコードを出力するs
属性で検索できる
検索できないIDだとnil

```RuBy
if session[:user_id]
  User.find_by(id: session[:user_id])
end
```
などのようにすると1リクエスト無いで何回も呼び出されてもアクセスは１回だけですむ



---
```RuBy
params[:id]
```
getやpostで送られてきた値を受け渡しメソッド
（リンク、フォームによるパラメータの受け渡し)
リンクによるパラメータの受け渡し

もし有効なオブジェクトではない場合はメソッドが見えない
```RuBy
user = nil
user.authenticate(params[:session][:password])
=>NameError: undefined local variable or method `params` for main:Object
```

`user && user.authenticate(params[:session][:password]) `
などとすると左辺がfalseなら右辺の処理はしないのでエラーを吐き出さなくて便利

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


---
```RuBy
redirect_to @user
```
リダイレクトする
この場合
user_url(@user)へのルーティングとして変換される


---

`フォーム作成メソッド`
アカウントを作る際に便利
`form_for`
```rails5
<%= form_for(@user) do |f| %>
  <%= f.label :name %>
  <%= f.text_field :name %>

  <%= f.label :email %>
  <%= f.email_field :email %>

  <%= f.label :password %>
  <%= f.password_field :password %>

  <%= f.label :password_confirmation, "Confirmation" %>
  <%= f.password_field :password_confirmation %>

  <%= f.submit "Create my account", class: "btn btn-primary" %>
<% end %>
```
勝手にアクションは/userというURLのPOSTと解釈する
任意のmodelに基づいたformを使う時に使うと良い
セッションを使うときはリソースの名前と対応するURLの指定が必要になる

追記
form_for(@user)を使ってフォームを構築すると@user.new_record?がtrueの場合post
違う場合はpatch(更新)のHTTPリクエスト使用する

```rails
<input name="_method" type="hidden" value="patch" />
```
webブラウザではpatchリクエストを送信できないので偽造して送ってる


```RuBy
form_for(:session, url:login_path)
```

参考:[【Rails】form_for/form_tagの違い・使い分けをまとめた](https://qiita.com/shunsuke227ono/items/7accec12eef6d89b0aa9)
参考:[Railsにのフォーム基本](https://qiita.com/ykyk1218/items/2541a313aac0f0e5d81a)


---
`form_tag`
参考[form_for/form_tagの違い・使い分け](https://qiita.com/shunsuke227ono/items/7accec12eef6d89b0aa9)



---
```RuBy
pluralize(3,"erratum") =>"3 errata"
```
英語専用メソッド第一引数が単数の場合第二引数を単数形に複数形の場合は複数形にする
不規則活用を含む    

---
```RuBy
$ rails console
>> flash = { success: "It worked!", danger: "It failed." }
=> {:success=>"It worked!", danger: "It failed."}
>> flash.each do |key, value|
?>   puts "#{key}"
?>   puts "#{value}"
>> end
success
It worked!
danger
It failed.
```
リダイレクトしたあとに一時的に表示する

```RuBy
flash[:success] = "Welcome to the Sample App!"
```
は
```HTML
<div class="alert alert-success">Welcome to the Sample App!</div>
```
のようになる
フラッシュのkyeによって表示するクラスを動的に変化させることができる
例
```rails5
<% flash.each do |message_type, message| %>
   <div class="alert alert-<%= message_type %>"><%= message %></div>
<% end %>
```
上記のようにかけるのはブートストラップを導入しているため注意

---
```RuBy
content_tag(:div)
#=> "< div >< /div >"

content_tag(:div, "content")
#=> "< div >content< /div >"

content_tag(:div) do
  content_tag(:strong, "header")
end
#=> "< div >< strong >header< /strong >< /div >"


content_tag(:div, "header", class: 'link')
#=> "< div class="link" >header< /div >"

```
ACtionViewsモジュールのヘルパーの一種
参考: [`content_tag`のあまり知られていないオプション](https://techracho.bpsinc.jp/hachi8833/2018_04_10/54701)

---
```RuBy
include SessionsHelper
```
モジュールを読み込む
applicationコントローラにモジュールを読み込ませると
どのコントロラーでも使用できる

---
```RuBy
session[:user_id] = user.id
```
ユーザーのブラウザ内の一時的にcookiesに暗号化済みのユーザーIDが自動で作成される
ブラウザが閉じられるまで次のページでsession[:user_id]を使用することができる
ここで作成されたcookiesを使って攻撃者がユーザーとしてログインすることはできない（一時セッションの場合のみ）
セッションは基本ブラウザがなくなると消えてしまう
ブラウザによってはセッションを復元できる機能があるものもある

---
```RuBy
session.delte(:user_id)
```
現在のユーザーをnilにする（ログアウトする）

---
```RuBy
has_secure_token
```
ランダムなトークンを発行する
ハッシュ化した値がデータベースに保存されるのでセキュリティ上使う場合は重要じゃない時に使う（基本は使わなくていい

---
```RuBy
SecureRandom.urlsafe_base64
```
A–Z、a–z、0–9、-、_
のいずれかの文字 (64種類) からなる長さ22のランダムな文字列を返します

---
```RuBy
>> 1.year.from_now
=> Wed, 21 Jun 2017 19:36:29 UTC +00:00
>> 10.weeks.ago
=> Tue, 12 Apr 2016 19:36:44 UTC +00:00

>> 1.kilobyte
=> 1024
>> 5.megabytes
=> 5242880
```
年や月、単位で計算してくれるメソッドがある

---
```RuBy
cookies[:remember_token] = { value:   remember_token,
                             expires: 20.years.from_now.utc }
```
よく二十年期限ん切れになるクッキーが使われる
使用頻度の高いこの設定は以下のperemanetメソットとして追加された（同じ処理）

```RuBy
cookies.permanent[:remember_token] = remember_token
```

```RuBy
cookies.permanent.signed[:user_id] = user.id
```
さらに署名クッキー化すると
```RuBy
User.find_by(id: cookies.signed[:user_id])
```
で呼びさるようになる

---
```RuBy
BCrypt::Password.new(remember_digest).is_password?(remember_token)
```
（ハッシュ化されている）記憶トークンと（ただのトークン）記憶ダイジェストを比較するやり方

---
```RuBy
raise
```
任意で例外を発生させることができる
明示的にエラーを発生させ処理を中断するs
テストしてるかわからないところにい記載してテストを実行して例外が発生しなかったら
テストを網羅できていないことがわかる
---
```RuBy

```

---
```RuBy

```

---
```RuBy

```

---
```RuBy

```

---
```RuBy

```

---
```RuBy

```

---
```RuBy

```

## gemfile(パッケージ)
デフォ
`gem 'byebug'`
デバック用
`debugger`メソッドを入れてブラウザからメソッドを使うところにアクセスすると
サーバを起動しているターミナル上`debugger`が記載されているところで処理が止まり
コンソール上でデバックできるようになる

---
デフォ以外
`gem 'minitest-reporters'`
test/test_helper.rb
require "minitest/reporters"
Minitest::Reporters.use!
testが見やすくなる

その他
`Sprockets`
Rils3から導入されたgem
アセットファイル（js,cssなど）を効率よく管理するためのアセットパイプライン
の仕組みの基盤gem



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
module ApplicationHelper
```
ヘルパーを使うときは上記のように書く
＊コントローラーは全部のヘルパーをインクルードするがビューはコントローラ名と同名のヘルパーしか読み込まない
ヘルパーメソッドはテストからは呼べないtest/test_helper.rbに記載すると良い
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

`パーシャル`
`<%= render 'layouts/shim' %>`
この行では`app/views/layouts/_shim.html.erb` というファイルを探し、結果をビューに挿入する
パーシャル用ディレクトりはsharedディレクトリがよく使用される

---
`名前つきルート　名前付きルート`
パスヘルパーやURLヘルパーと呼ばれる
ヘルパーを使用することで可読性が上がる
SQLインゼクション対策にも繋がる

以下の参考資料がかなり参考になった
参考:[名前付きルートを使用する利点](https://ryoutaku-jo.hatenablog.com/entry/2019/05/05/%E5%90%8D%E5%89%8D%E4%BB%98%E3%81%8D%E3%83%AB%E3%83%BC%E3%83%88%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%99%E3%82%8B%E5%88%A9%E7%82%B9)
```RuBy
 get '/アクション名', to:'コントローラー名#アクション名'
```
をrootes.rbで宣言すると`アクション名_path`や`アクション名_url`という変数が使えるようになる
もちろん
  get    '/login',   to: 'sessions#new'
  post   '/login',   to: 'sessions#create'
  delete '/logout',  to: 'sessions#destroy'
などでもそれぞれ
名前付きルート
login_path
login_path
logout_path
を使うことができる
```RuBy
match '/about', to: 'static_pages#about'
#なら
about_path => '/about'
about_url  => 'http://localhost:3000/about'
#となる
```


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
Digest::MD5::hexdigest(変換する値)
```
MD5に変換する

---
`オプション引数`

```RuBy
def hoge(one, opt1 = {}, opt2 = {})
  pp one, opt1, opt2
end

# 期待どおりにならない
hoge :lion, lion: :female, tiger: :male, jibanyan: :cat
#=> [:lion, {:lion=>:female, :tiger=>:male, :jibanyan=>:cat}, {}]

# エラー
hoge :lion, lion: :female, tiger: :male, {jibanyan: :cat}
#=> SyntaxError: unexpected '\n', expecting =>

# 期待どおり
hoge :lion, {lion: :female, tiger: :male}, jibanyan: :cat
#=> [:lion, {:lion=>:female, :tiger=>:male}, {:jibanyan=>:cat}]
```
呼び出し側で最初のオプション引数を{}で囲まないと最初のopt1に全て入ってしまいopt2が空になる
opt1だけ{}で切り出してもエラーになる
**={}の時の場合省略できる**
参考資料[Railsフレームワークで多様される....](https://techracho.bpsinc.jp/hachi8833/2017_03_22/37313)

---
`キーワード引数`
```RuBy
def f51(a, *b, l: 0, r: 1)
  p [a, b, l, r]
end
f51(42) # => [42, [], 0, 1]
f51(42, 'answer', [4, 8, 10]) # => [42, ["answer", [4, 8, 10]], 0, 1]
f51(42, 'answer', [4, 8, 10], {l: 6, r: 9})
# => [42, ["answer", [4, 8, 10]], 6, 9]
f51(42, l: 6, r: 9) # => [42, [], 6, 9]
f51(42, :l => 6, :r => 9) # => [42, [], 6, 9]
f51(42, {:l => 6, :r => 9}) # => [42, [], 6, 9]
```
参照 [Rubyのメソッドの引数受け渡しまとめ](https://qiita.com/raccy/items/1168c7e8849dedf70fa4#%E3%82%AD%E3%83%BC%E3%83%AF%E3%83%BC%E3%83%89%E5%BC%95%E6%95%B0)


---
`ストロングパラメータ`
DBに入れる値を制限することで不正なパラメータ入力を防ぐ仕組み
Rails3のMassAssignmentの脆弱性からストロングパラメータの導入に至った
例
```RuBy
params.require(:user).permit(:name, :email, :password, :password_confirmation)
```
使い方解説
:user属性を必須とする
名前、メールアドレス、パスワード、パスワード確認の属性をそれぞれ許可する
それ以外は許可しない
返り値は許可された`params`ハッシュ(:user属性がない場合はエラーになります)


---
`本番環境のSSL化`
**config/environments/production.rb**
からconfig.force_sslをコメントアウトを解除する
本番用のWEBサイとでSSLを使える等にするためにはドメインごとにSSl証明書を購入
する必要があるがHeroku上ではHerokuのSSL証明書に便乗することができる(サブドメインのみ)


`||=`
Rubyでよく使えるイディオム（よく使われる用語）
```RuBy
@foo =nil
@foo = @foo || "bar" => "bar" # nil || "bar"
@foo = @foo || "bar" => "bar" # "bar" || "bar"

x = x+1
x += 1

@foo = @foo || "bar"
@foo ||= "bar"
```
変数の値がnilなら変数に代入するがnilでなければ代入しないという処理になる

`代入した結果代入したものが存在した時だけに処理する方法`
```RuBy
if (user_id = session[:user_id]){}
```
ユーザーIDにユーザーIDのセッションを代入した結果ユーザーIDのセッションが存在すれば
という意味

わかりやすい例
```RuBy
user = find_user
if user
  send_mail_to(user)
end
```
上は実質下と同じ

```RuBy
if user = find_user
  send_mail_to(user)
end
```

`||=`との違いはこちらは何が入ってようとも入れる
`||=`は元がnilでなければ入らないs   


`ログイン`
sessionにユーザーIDが存在している状態のこと


`protect_from_forgery with: :exception`
application_controller.rbでよく記載する
csrf対策（クロスサイトリクエストフォージェリ）
サイトに攻撃用のコードを仕込むことでアクセスしたユーザーに対し知恵意図しない動作を行わせること

**ただしフォームやリンクを生成すると
対策の恩恵を受け入れられないのでビューヘルパー（form_forとか）を使用するべき**
参考:[CSRF対策を行うprotect_from_forgeryメソッド](https://kossy-web-engineer.hatenablog.com/entry/2018/10/13/062454)


`クラスメソッド`
メソッドがクラス自身 (この場合はnew) に対して呼び出されるとき、このメソッドをクラスメソッドと呼びます。クラスのnewメソッドを呼び出した結果は、そのクラスのオブジェクトであり、これはクラスのインスタンスとも呼ばれます。lengthのように、インスタンスに対して呼び出すメソッドはインスタンスメソッドと呼ばれます。

```RuBy
def self.メソッド名
def クラス名.メソッド名
```
の書き方はクラスメソッドだと思っていい逆に

```RuBy
def メソッド名
```
はインスタンス メソッドであると思っていい

参考:[クラスメソッドとインスタンスメソッドについてザクッと分かりやすく](https://qiita.com/amidara/items/27221675638cdc9bde6b)


`テスト中二ログインステータスを返す方法`
test/test_helper.rb
に以下を定義する
```RuBy
# テストユーザーがログイン中の場合にtrueを返す
def is_logged_in?
  !session[:user_id].nil?
end
```
テストからヘルパーメソッドは呼べないのでセッションか直接確認した方が良いだろう
ちなみに本来使っているヘルパーメソッドは以下の通り
app/helpers/sessions_helper.rb

```RuBy
# ユーザーがログインしていればtrue、その他ならfalseを返す
def logged_in?
  !current_user.nil?
end
```
`current_user`メソッドはapp/helpers/sessions_helper.rb
つまり同じ場所に書かれている


`_pathメソッドと_urlメソッドの使い分け`
```RuBy
root_path => '/' ※ルート以下の文字列を返す
root_url  => 'http://www.example.com/'　※完全なURLの文字列を返す

help_path => '/help'
help_url  => 'http://www.example.com/help'
```
リダイレクトする時は_url
それ以外はpath
assert_templateの引数は
`users/new`などで指定しないといけない

`開発環境のみで使えるパス`
ActionMailer::Previewのプレビュー（要はメール内容）
http://localhost:3000/rails/mailers

アプリケーションの各情報
http://localhost:3000/rails/info/properties

名前付きルートなどのルート確認
http://localhost:3000/rails/info/routes


`return false if remember_digest.nil?`
一行で即座にメソッドを実行して終了できるテクニック

`コントローラーで定義したインスタンス 変数にテストからアクセスする方法`
app/controller/**
```RuBy
@user = User.find_by(email: params[:session][:email].downcase)
```
といったようにインスタンス 変数（@変数）を記載する
test/**
```RuBy
assert_equal cookies['remember_token'], assigns(:user).remember_token
```
あとはテスト内でインスんタンス変数を`assigns(:シンボル)`でよびだす

`スコープ変数まとめ`
```RuBy
$global = "global" #グローバル変数　プロジェクト全てから呼び出せる
@name = name #インスタンス変数　インスタンス(.new)内ならどこでも
@@name = name #クラス変数　クラス内のみ

# クラス変数の出力例
user1 = User.new("taroo")
user2 = User.new("hanako")
user1.put_name => “hanako”
user2.put_name => ”hanako”
#インスタンスごとではないことがわかる

name = name #ローカル変数　メソッド内でしか使用できない

#以下は擬似変数 変数といっても代入できない　どこでも使える
true
false
nil

```


##vimメモ
**書くことが多かったら別ファイルにする**
`:vim 探したい文字列 **/* | cw`
vimを開いたカレントディレクトリ以下でグループ検索して一覧表示
エンターでみて:qで閉じる

### 豆知識
ほとんどのデータベースは文字列の上限を255としている

メールアドレスのうちドメイン部分だけが大小文字の区別はしない
foo@bar.comとfoo@BAR.comは同じ
Foo@bar.comとfoo@bar.comは本来別アドレス
現実では大文字と小文字を区別するメールサービスやISPは滅多にない
なぜなら区別をしてしまうと相互運用性の問題などが発生してしまうからだ
