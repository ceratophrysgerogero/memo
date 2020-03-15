Rails Ruby wiki

######目的
単なるメモ
いつもで検索してもヒットできるようにあらゆることをメモする


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

## 詰まったエラー
`WARN Selenium [DEPRECATION] Selenium::WebDriver::Chrome#driver_path= is deprecated. Use ...`
#### 原因
基本的にタイポだと思っていい
たとえば`test`に`do`を入れわせれたりすると起きる

`Expected "poGFEr-zpie0SuBn1jkkfg" to be empty.`
""の中身が毎回変わるのであればクッキーやセッションなどを疑う
またからだと言われる場合は、どこかで必要なものを無くしている可能性がある

## 詰まったエラー
`ArgumentError: wrong number of arguments (given 0, expected 1)`
#### 原因
エラー内容から引数の問題と言われているが引数を変えても問題は解決しなかった
原因はgemにあった
#### 解決策
参考:[Paginate導入時のエラー](ß)
3.16ではエラーになってしまうのでそれ以降のバージョンが良さそう


## 詰まったエラー
`ActiveRecord::RecordNotUnique:ActiveRecord::RecordNotUnique: SQLite3::ConstraintException: UNIQUE constraint failed: relationships.follower_id, relationships.followed_id: INSERT INTO "relationships" ("follower_id", "followed_id", "created_at", "updated_at", "id") VALUES (1, 1, '2019-10-09 09:12:30.411910', '2019-10-09 09:12:30.411910', 298486374)`
####原因
fixtureのマイグレーションで制約された一意性を満たすことができいない
#### 解決策
`test/fixtures/~~.yml`を正しい値に編集したり一旦全て削除する

## 詰まったエラー
testにて
has no column named "password"
####原因
`gem bcrypt`提供されているメソッド`has_secure_password`をモデルに
使用している場合`has_secure_password`
ymlファイルに`password`属性をいれてテストしてしまっている
#### 解決策
仮想的な属性はymlファイルでは使用できないので`password`を作る際に元になる属性
`password_digest`属性に値をいれてあげると解決する


## 詰まったエラー(警告)
WARN Selenium [DEPRECATION] Selenium::WebDriver::Chrome#driver_path= is deprecated. Use Selenium::WebDriver::Chrome::Service#driver_path= instead.
####原因
[非推奨] Selenium::WebDriver::Chrome#driver_path=

[推奨] Selenium::WebDriver::Chrome::Service#driver_path
#### 解決策
gem 'chromedriver-helper'をの代わりに
gem 'webdrivers', '~> 3.0'を使用する


## 詰まったエラー
/Users/mannbou/Workspace/rails_trial/ptwitter/test/fixtures/microposts.yml:24: Passing `word_count` with the 1st argument of `sentence` is deprecated. Use keyword argument like `sentence(word_count: ...)` instead.
####原因
gem faker最新バージョンでは`sentence(5)`のように記述できなくなった
#### 解決策
`sentence(word_count: 5)`といったようにシンボルを指定する

## 詰まったエラー
xcodeが無いからbudeleが無いやrailtiesというgemが無いといった様々なこと

####原因
macOSの更新
osのバージョンは　Catalina 10.15.2

#### 解決策
bundel installをしようと試みるもxcodeが無いと言われて怒られる
`xcode-select --install`
xcodeをインストール
なぜか使用しているrubyのバージョンがgemと一致しなくて怒られたので
rbenvをインストールしてgemと同じバージョンを指定する
`rbenv install 2.1.2` でインストール
`rbenv versions`インストール確認
`rbenv global 2.1.2`全体で使うrubyを設定
`rbenv local 2.1.2`カレントディレクトリーで使うrubyを設定
rbrnvでインストールしたあとは`rbenv rehash`する必要がある
もし切り替えできない場合は
`which ruby`でrubyをみている場所をチェックする
`/.rbenv/shims/ruby`ではなかった場合
`~/.bash_profile`ファイルに
`export PATH="~/.rbenv/shims:/usr/local/bin:$PATH"
eval "$(rbenv init -)"`を記載して
`source ~/.bash_profile`変更反映させる

gemが怪しいので`bundle install`したら以下のエラーが出た
`The `bundle' command exists in these Ruby versions:`
bundleが無いようなので
`gem install bundler`でbundleをインストールする
`/Users/mannbou/.rbenv/versions/2.3.7/lib/ruby/2.3.0/rubygems.rb:241:in `bin_path': can't find gem railties (>= 0.a) (Gem::GemNotFoundException)
	from /usr/local/bin/rails:22:in `<main>'`
`railties`というgemが見えないエラーが吐き出される

[rails githubから](https://github.com/rails/rails/tree/master/railties)
`railties`とは
簡単に説明するとフレームワークを統合して処理するもの
主にプロセス管理や`rails`コマンドライン管理、ジェネレータコア提供をする
`ダウンロード`の項目に
`gem install railties`と記載されていることからrailsプロジェクトの一部として
`railties`gem(パッケージ)をダウンロードできる
このことから`gem install railties`を実行するとエラー解消できそうだが
そもそもrailsフレームワークの依存しているgemが抜け落ちているのは普通に考えると
ありえないことなのでrails全体に不具合がありそうなので
`gem install rails`コマンドを使い再度入れ直す(依存関係などを修復する)

以上で解決した...が実際にはもっと色々試行錯誤しているので直った原因と思われる手順を
示しているだけなので注意してください


## 詰まったエラー
The `rails` command exists in these Ruby versions:2.6.0
####原因
ruby 2.6.0にrailsが入っていない
おそらくローカルもしくはグローバルで使ってるrubyのバージョンを変えたせい
#### 解決策
ruby 2.6.0を使用するように設定する
おすすめはBundlerを使うこと



## 詰まったエラー
Rails6 Webpacker
```RuBy
Traceback (most recent call last):
    80: from bin/rails:3:in <main>
    79: from bin/rails:3:in load
```

####原因
Rails6を使うとエラーする人がいる
#### 解決策
rails webpacker:install
yaruが無いと言われたらyaruインストール
brew install yarn


## 詰まった事
それぞれのユーザーを取り出したいのに毎回一番最初のユーザーを取り出してしまう
####原因
検索メソッドの記述ミス
#### 解決策
User.find_by(params[:id])
を
User.find_by(id: params[:id])
に修正する

## 詰まったエラー
One or more of this task's arguments is invalid. They cannot start with '-', and must follow git ref-format rules: https://www.kernel.org/pub/software/scm/git/docs/git-check-ref-format.html
####原因
sourcetreeでプッシュしようとしたら起きた問題
#### 解決策
おそらくリモートリポジトリを指定する名前が間違っている

## 詰まったエラー

####原因

#### 解決策


## 詰まったエラー

####原因

#### 解決策

## 詰まったエラー

####原因

#### 解決策



## ファイルやフォルダ解説
`Gemfile.lock`
インストールされたgemを記録したファイル

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
password_digestが正常に動いている場合はpasswordやpassword_confirmationが呼べる

なおユーザーmishaelの呼び出し方は
```RuBy
user = users(:mishael)
```
シンボルで見つけられる(test環境のみ)
def set
end
に書いておくとクラス呼び出しの際に呼ばれるので良いだろう



`test/fixtures/microposts.yml`
マイクロポストのテスト用のデータ

```rails
test/fixtures/microposts.yml
orange:
  content: "I just ate an orange!"
  created_at: <%= 10.minutes.ago %>

tau_manifesto:
  content: "Check out the @tauday site by @mhartl: http://tauday.com"
  created_at: <%= 3.years.ago %>

cat_video:
  content: "Sad cats are sad: http://youtu.be/PKffm2uI4dk"
  created_at: <%= 2.hours.ago %>

most_recent:
  content: "Writing a short test"
  created_at: <%= Time.zone.now %>
```
`created_at`は本来railsによって自動的にされるため基本的には手動では更新できないが
fixtureファイルの中では更新可能になっている。これを利用して意図的に順序を更新することができる。
一番したのサンプルは最後に生成されるので更新順に並べられるかというテストを行うことができる。


`test/mailers/previews/user_mailer_preview.rb`
urlでhtmlメールやテキストメールをプレビューすることができる
rails/mailers/user_mailer/password_reset
rails/mailers/user_mailer/password_reset.txt



## コマンド  
`pwd`
現在のカレントディレクトリまでのパス表示s


`ls -a`
隠しファイルも表示

ホームビューインストール
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`


`rails --version`
`gem update`
`gem install bundler`
`gem install rails`


`gem install gem名`
最新のものを導入
`gem install gem名 -v <バージョン>``

`gem uninstall gem名`

`gem list`


`bundle init`
Gemfileを作成

`bundle install`
gemfile.lockを元にインストール

`bundle init`

`bundle update`
gemfile.lockを更新する

`bundle lock`
Gemfileを参照しないでGemfile.lockを参照してgemを更新する

`git init`
gitファイル作成
`git -A`


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
		add_foreign_key :tweets, :users
    # add_foreign_key :対象のテーブル名, :指定先のテーブル
  end
end
```



複合キーインデックスの場合
```RuBy
db/migrate/[timestamp]_create_relationships.rb
class CreateRelationships < ActiveRecord::Migration[5.0]
  def change
    create_table :relationships do |t|
      t.integer :follower_id
      t.integer :followed_id

      t.timestamps
    end
    add_index :relationships, :follower_id
    add_index :relationships, :followed_id
    add_index :relationships, [:follower_id, :followed_id], unique: true
  end
end
```
これは`follower_id`と`followed_id`の組み合わせが必ずユニークであることを保証する仕組み

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

`rails generate mailer UserMailer account_activation password_reset`
create  app/mailers/user_mailer.rb
invoke  erb
create    app/views/user_mailer
create    app/views/user_mailer/account_activation.text.erb
create    app/views/user_mailer/account_activation.html.erb
create    app/views/user_mailer/password_reset.text.erb
create    app/views/user_mailer/password_reset.html.erb
invoke  test_unit
create    test/mailers/user_mailer_test.rb
生成されるHTMLメイラーのレイアウトやテキストメイラーのレイアウトはapp/views/layoutsで確認
生成されたコードには自動生成されたインスタンス変数@greetingを使用できる(user_mailer.rb)


` rails generate model Micropost content:text user:references`
`references`を付け加えると`belongs_to`が追加される
referencesは型であり、自動的にインデックスと外部キーの`user_id`カラムが追加することができる
これは外部キー参照と呼ばれるデータベースレベルの制約である。これによってMicropostsテーブルの
user_idは、Usersテーブルのidカラムを参照するようになります。
**この制約は全てのデーターベースで章できる訳ではない(例えばHerokuのPostgreSQLではサポートされていますが、開発用のSQLiteではサポートされていません)**
```RuBy
app/models/micropost.rb
class Micropost < ApplicationRecord
   belongs_to :user
end
```

```RuBy
db/migrate/[timestamp]_create_microposts.rb
class CreateMicroposts < ActiveRecord::Migration[5.0]
  def change
    create_table :microposts do |t|
      t.text :content
      t.references :user, foreign_key: true

      t.timestamps
    end
    add_index :microposts, [:user_id, :created_at]
  end
end
```
このようにuser_idがなくてもindexをつけることができる
これは`User`クラスから`user_id`が外部キーだと推測できるためである
外部キーをしてしたいなら`foreign_key`を使用する
```RuBy
has_many :active_relationships, class_name:  "Relationship",
                                foreign_key: "follower_id",
```

**上記のようにuser_idを追加する場合バリデーションやテストは必ず元のデータとは別に行うように**


---
メイラーのテキストレビュー
`app/views/user_mailer/account_activation.text.erb`
メイラーのhtmlレビュ-
`app/views/user_mailer/account_activation.html.erb`
アプリケーションのメイラー
`app/mailers/application_mailer.rb`
生成されたuserメイラー
`app/mailers/user_mailer.rb`



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

`rails db:seed`
db/seeds.rb のサンプルデータを書き換えた時に上のリセットと一緒に使うことが多いい

`rails console --sandbox`
サウンドボックスモード
ここで行った全ての変更は終了時にロールバックされる

## クラス
`ActiveRecord::Base`
OR Mapper
モデルとテーブルをつなぎ合わせることでrailsからテーブルのレコードにアクセスする役割
rails起動の際にデータベースにアクセスしてクラス名を元に対応するテーブル構造を
読み取り自動で対応するゲッターセッターを作成する（attr_accessorが必要ない)
このようなクラスを使わない場合は`PORO, Plain Old Ruby Object`と呼ばれる事がある

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
`composed_of`
例
```RuBy
class Person ActiveRecord::Base
  composed_of :location, mapping: [ %w(country country), %w(city city) ]
end
```
`:location`から`Location`クラスを推測して`Person`と結びつく
オプション`class_name:`を使用すると明示的にクラスを指定する事ができる
%wの第一引数は`Location`クラス、第二引数は`Person`クラスのものを

---
`attr_reader`
例
```RuBy
attr_reader :user_id
```
は
```RuBy
def user_id
	@user_id #インスタンス 変数
end
```
として定義される


---
```RuBy
<=>
```
例
```
10 <=> 20   #  -1
20 <=> 10   #   1
20 <=> 20   #   0
20 <=> '20' # nil
```
```
[ 1, 2, 3 ] <=> [ 1, 3, 2 ]       #=> -1
[ 1, 2, 3 ] <=> [ 1, 2, 3 ]       #=> 0
[ 1, 2, 3 ] <=> [ 1, 2 ]          #=> 1
```

自身（左辺)と other(右辺) の各要素をそれぞれ順に <=> で比較していき、結果が 0 でなかった場合にその値を返します。各要素が等しく、配列の長さも等しい場合には 0 を返します。各要素が等しいまま一方だけ配列の末尾に達した時、自身の方が短ければ -1 をそうでなければ 1 を返します。 other に配列以外のオブジェクトを指定した場合は nil を返します。
`include Comparable`する必要性があるかもしれない



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

```RuBy
validates :password, presence: true, length: { minimum: 6 }, allow_nil: true
```
allow_nilはパスワードがからだった時例外処理を加える

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
* オブジェクト作成時にpasswordがnilになってしまっているかバリーデーションしてくれる
* ↑のおかげで編集時にpasswordがなくても編集できるような実装ができる（そのためにはnil許可を追加する必要がある）


---
```RuBy
app/models/user.rb
before_save { self.email = email.downcase }
```
オブジェクトが保存される時にemail属性を小文字に変換して保存する
before_saveはコールバックメソッド
右のselfは省略
`self.email.downcase!`を使えば代入を省略できる
---
```RuBy
before_action :logged_in_user, only: [:edit, :update]
```
editアクションまたはupdateアクションが実行される前にlogged_in_userメソッドを実行する
onlyをつけない場合は全てのアクションに適用される
単数ならonly: :edit

---
```Ruby
app/models/user.rb
class User < ApplicationRecord
  has_many :microposts, dependent: :destroy
end
```
app/models/user.rb
userモデルは、複数のmicropostsを所持する（関連づける）
**micropostsとはデータモデルのこと**
belongs_toで関連ずけをする必要がある
[rails チュートリアル13](https://railstutorial.jp/chapters/user_microposts?version=5.1#cha-user_microposts)

`dependent: :destroy`は`app/models/micropost.rb`で宣言した` belongs_to :user`（マイクロポストが属しているユーザーが）
破棄されると同時にマイクロポストも一緒に破棄することを保証する

belongs_to/has_many関連付けを使うことで、表に示すようなメソッドをRailsで使えるようになる

| メソッド　| 用途 |
|:-----------|:-----------
| micropost.user | Micropostに紐付いたUserオブジェクトを返す |
| user.microposts | Userのマイクロポストの集合をかえす |
| user.microposts.create(arg) | userに紐付いたマイクロポストを作成する |
| user.microposts.create!(arg) | userに紐付いたマイクロポストを作成する (失敗時に例外を発生) |
| user.microposts.build(arg)	 | userに紐付いた新しいMicropostオブジェクトを返す |
| user.microposts.find_by(id: 1) | userに紐付いていて、idが1であるマイクロポストを検索する |

`build`はそのまま新しいオブジェクトで返してくれるのでそのまま`save`メソッドでDBに登録できる
しかしこれはクラスが`User`だった場合のみ利用できる
理由としてrailsが自動的に`User`クラスから`user_id`が外部キーだということを推測してくれるからだ
もし外部キーを指定する場合は以下のように`foreign_key`する

```RuBy
class User < ApplicationRecord
  has_many :microposts, dependent: :destroy
  has_many :active_relationships, class_name:  "Relationship",
                                  foreign_key: "follower_id",
                                  dependent:   :destroy
end
```
```RuBy
class Relationship < ApplicationRecord
  belongs_to :follower, class_name: "User"
  belongs_to :followed, class_name: "User"
end
```

また多対多の場合 `has_many through`を使用する
```RuBy
has_many :followeds, through: :active_relationships
```

---


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
また一部のアクションだけ使用したい場合は
`resources :blogs, :only => [:index, :show]`
などと言ったように宣言する

またmemberというurlの深掘りオプションが存在する
例えば
```RuBy
resources :users do
  member do
    get :followings
  end
end
```
と記載されていると
`followings_user GET    /users/:id/followings(.:format) users#followings`
とルーティングが追加される
また`member`ルーティングが一つだけしかないなら以下のように省略できる
```RuBy
resources :users do
    get :following, :followers
end
```

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

```RuBy
assert_select 'h1>img.gravatar'
```
h1タグの内側にある`gravatar`クラス付きのimgタグがあるかどうかチェックできるs

`assert_select`は、必ずHTMLタグを伝え必要があるが、`assert_match`はそれがない

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
assert_match 'foo', 'foobar'      # true
assert_match 'baz', 'foobar'      # false
assert_match /\w+/, 'foobar'      # true
assert_match /\w+/, '$#!*+@'      # false
```
正規表現でテストできる
`asset_equal`との違いは正規表現でstringにマッチするかどうかを調べられるだけ


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

```RuBy
def setup
  ActionMailer::Base.deliveries.clear
end
assert_equal 1, ActionMailer::Base.deliveries.size
```
送信した数をチェックする
deliveriesは変数なので最初にクリアーにしておかなければ他の
メール送信チェックで数がおかしくなってしまう必要がある

---
```RuBy
follow_redirect!
```
postリクエスト送信した結果をみて指定されたリダイレクト先に移動するメソッド

---
`パスワードをリセットしたらダイジェストをnilにしないと履歴からパスワード再設定にアクセスされてログインまで突破される`
```RuBy
def update
  if params[:user][:password].empty?
    @user.errors.add(:password, :blank)
    render 'edit'
  elsif @user.update_attributes(user_params)
    log_in @user
    @user.update_attribute(:reset_digest, nil)
    flash[:success] = "Password has been reset."
    redirect_to @user
  else
    render 'edit'
  end
end
```


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
```rails
blank?
```
empty?とnil?を合わせたもの
railsで使用できる
nilや空ならtrue


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
>> [1, 2, 3, 4].map { |i| i.to_s }
=> ["1", "2", "3", "4"]
```
短縮することも可能
```RuBy
>> [1, 2, 3, 4].map(&:to_s)
=> ["1", "2", "3", "4"]
```
jsonを使えば文字列として繋げることができる(配列で取らないということ)
```RuBy
>> [1, 2, 3, 4].map(&:to_s).join(', ')
=> "1, 2, 3, 4"
```
user.followingの各要素idを呼び出すには
```RuBy
>> User.first.following.map(&:id)
=> [3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22,
23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41,
42, 43, 44, 45, 46, 47, 48, 49, 50, 51]
```
とできるがよく使われるのでActiveRecordで以下のメソッドが用意されている

```RuBy
>> User.first.following_ids
=> [3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22,
23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41,
42, 43, 44, 45, 46, 47, 48, 49, 50, 51]
```
***following_idsメソッドは、has_many :followingの関連付けをしたときにActive Recordが自動生成したものです***


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


```rails
<% if current_user.admin? && !current_user?(user) %>
  | <%= link_to "delete", user, method: :delete,
                                data: { confirm: "You sure?" } %>
<% end %>
```
httpメソッドを指定する

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
引数にidの値が入っていればそれを参照して探してくる事ができる

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
save
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
バリデーションが行われない時に使用する
特にパスワード要求がいらない状態タイムスタンプ更新のみなど

---
```RuBy
.update_attributes
```
updateの別名（エイリアス）
複数のカラムを更新できる
validationを行う
更新の際はこちらを使う方が良い
またセキュリティのため更新はストロングパラメーターを使用すると良い↓
```RuBy
def user_params
  params.require(:user).permit(:name, :email, :password,
                               :password_confirmation)
end
を使用して
@user.update_attributes(user_params)
```
などとすること

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
form_for(@user)を使ってフォームを構築すると@user.new_record?がtrueの場合post(作成アクション)
違う場合はpatch(更新アクション)のHTTPリクエスト使用する
つまり自動で新しく作成するか更新するかを判断してくれる
DELETEリクエストの時だけmethodパラメーターで指定しなくてはならない

`form_for`は引数によって吐き出されるテンプレートが違う
例 form_for :post　以下の場合

シンボルで生成
`<form action="/posts" method="post">`

`@post = Post.new` オブジェクトを使用
`<form action="/posts/create" class="new_account" id="new_account" method="post">`

`@post = Post.find(1)`したオブジェクト
`<form action="/posts/update" class="edit_account" id="edit_account_1" method="post">
<input name="_method" type="hidden" value="put">`





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
使用頻度の高いこの設定は以下のpermanentメソットとして追加された（同じ処理）

permanetは永続化のため
signedはcokiesを暗号化するため（デジタル署名と暗号化を同時する)
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
で呼びだせるようになる
ここのsignedは暗号化を解除する役割になる

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
reload
```
app配下あたりにあるソースコードの読み直し
ただしconfig/initializer配下などの一部は読み込まない
使用用途はロードしたインスタンスがある状態でDBが変更した場合
メモリにあるインスタンスはDBが変更した部分を更新できないのでreloadで更新する
つまりDBに変化を与えたテストでよく使用される

---
```RuBy
toggle
```
属性を反転させる
返り値　self
---
```RuBy
toggle!
```
属性を反転させ保存する
返り値 boole

---
```RuBy
UserMailer.XXXXXX(メール情報).deliver_now
```
メールを送信する

---
`send`
```RuBy
>> user = User.first
>> user.activation_digest
=> "$2a$10$4e6TFzEJAVNyjLv8Q5u22ensMt28qEkx0roaZvtRcp6UZKRM6N9Ae"
>> user.send(:activation_digest)
=> "$2a$10$4e6TFzEJAVNyjLv8Q5u22ensMt28qEkx0roaZvtRcp6UZKRM6N9Ae"
>> user.send("activation_digest")
=> "$2a$10$4e6TFzEJAVNyjLv8Q5u22ensMt28qEkx0roaZvtRcp6UZKRM6N9Ae"
>> attribute = :activation
>> user.send("#{attribute}_digest")
=> "$2a$10$4e6TFzEJAVNyjLv8Q5u22ensMt28qEkx0roaZvtRcp6UZKRM6N9Ae"
```
動的にメソッドの名前を変えて実行することが可能
文字列でも実行することが可能だが一般的にはシンボルで行う



---
```RuBy
assigns(:シンボル)
```
対応するアクション内のインスタンス変数にアクセスすることができる
例えば
```RuBy
def create
  @user = find_by(email: params[:email])
end
```
とした時
```RuBy
assigns(:user)
```
で呼べる


---
```rails
<ul class="users">
  <% @users.each do |user| %>
    <%= render user %>
  <% end %>
</ul>
```
のようにコレクションを使わないとdo eachで回さなければならない上処理効率も悪い
しかし以下のように表示する内容をパーシャルにして(アンダーバーがついたviewファイルを準備して)
呼び出すことによってdo eachを使わなくても全て表示できる
このことをコレクションを使うという
```rails
<ul class="users">
  <%= render @users %>
	#<%= render partial: 'posts/post', collection: @users %>と同じことをしている
</ul>
```


render
Railsは@usersをUserオブジェクトのリストであると推測します。
さらに、ユーザーのコレクションを与えて呼び出すと、Railsは自動的にユーザーのコレクションを列挙し
それぞれのユーザーを_user.html.erbパーシャルで出力します
Action内で、呼び出すViewを指定するメソッド。そのAction内で@〜〜(インスタンス変数)として格納されたものは、Viewからrubyの構文で呼び出せます。
呼び出すViewの形式は、RHTML形式です。(RHTML形式は、普通のfoo.htmlや、hogehoge.html.erb等のruby構文が実行できる形式のHTMLのこと)
また部分テンプレートを指定することができる。
`_tweet.html.erb`のように必ず_から始めます。
参考資料:[忘れがちなrenderメソッドの使い方まとめ](https://qiita.com/hayashino/items/c2a4e7d3edbdcce3cd2a)



---
```RuBy
redirect_to
```
HTTPリクエストをサーバーに送り、ユーザーはそこから返ってくるHTMLが表示される。

HTTPリクエストとは
URL(http://〜〜)
HTTPメソッド(GETとかPOSTとか)
その他クッキーとか、ユーザーが送りたいデータとか
を含みますが、
railsのredirect_toでは、HTTPメソッドはGETに固定されています。
また、自サーバーにredirect_toした場合は、routeを通り、routeに指定されたアクションを実行します。
ので、redirect_toが記載されているActionのインスタンス変数はView側から使えません。

---
基本的にユーザーに編集させたくない値で次のアクションに値を渡したい時に使用する隠しフォームフィールド

```rails
<%= form_for(@user, url: password_reset_path(params[:id])) do |f| %>
 <%= hidden_field_tag :email, @user.email%>
<% end %>
```
はparams[:email]に保存されるが

```rails
<%= form_for(@user, url: password_reset_path(params[:id])) do |f| %>
 <%= f.hidden_field :email, @user.email %>
<% end %>
```
だとparams[:user][:email]に保存される
適切にプログラミングしよう

---
```rails
Posted <%= time_ago_in_words(micropost.created_at) %> ago.
```
`time_ago_in_words`は「3分前に投稿」といった文字列を出力

---
```RuBy
def cat(s1, s2)
  s1.to_s + s2.to_s
end

puts cat("hello", 123) => hello123
puts cat(456, "hello") => 456hello
```
`to_s`は
レシーバー自身を返す。strのクラスがStringのサブクラスである場合は文字列を
コピーして新しく作成したStringオブジェクトを返す。

---
```RuBy
モデル.where
```
任意のデータベースから任意の条件を指定して条件に当てはまる全てのレコードを取得する
一件だけ欲しい場合はfind_byを利用する

[Railsのwhereメソッドと仲良くなろう](https://qiita.com/yu-croco/items/c175583cd65585e1058c)

---
```RuBy
animals = ["dog", "cat", "mouse"]
puts animals.include?("cat")
puts animals.include?("elephant")
```
配列の要素に引数objが含まれて入ればtrue
例えば以下のように定義したとする
```RuBy
#app/models/user.rb
class User < ApplicationRecord
  has_many :following, through: :active_relationships, source: :followed
end
```
このときフォロしているユーザーを配列のように扱うことができるので以下のようにオブジェクトを検索することができる
```RuBy
user.following.include?(other_user)
user.following.find(other_user)
```
ここでは、`user.followes`では適切な英語にならないので`user.following`にするため
`:source`パラメーターを使って、「following配列の元はfollowed idの集合である」ということを明示的にRailsに伝える

---
```RuBy
composed_of
```
値オブジェクトをエンティティに含ませると同時に値オブジェクトをクラスにして抜き出す時に使用する

例えば
```ruby
class User
  attr_accessor :city_address, :town_address, :building_address
  def address
    city_address + town_address + building_address
  end
end
```
は

問題点

*  addressのような整形用メソッドがモデルを汚してしまう
*  本来意味を持つのはaddressなのに、メソッドで返ってくるのは単なる文字列
*  一旦addressを取得しても、そこからcity_addressを取り出すのは容易ではない

というデメリットを持ち込んでいる。根本的にな問題はDBのUserに`address`を内包した為に起きた事であると考えられる。これを改善するためaddresをクラスに分ける。

```ruby
class User
  attr_accessor :city_address, :town_address, :building_address
  def address
    Address.new(city_address, town_address, building_address)
  end
end

class Address
  attr_reader :city, :town, :building
  def initialize(city, town, building)
    @city, @town, @building = city, town, building
  end
end
```

改善点

* `address`メソッドが使いやすくなった
* `city`などの情報も取りやすくなった

問題点

* `Address`クラスを作るために`address`メソッドを宣言しているのは単純すぎてわかりにくい

そこで`composed_of`を使用してリファクタリングしてみる。


```ruby
class User
  attr_accessor :city_address, :town_address, :building_address
  composed_of :address, mapping: [%w(city_address city), %w(town_address town), %w(building_address building)]
end

class Address
  attr_reader :city, :town, :building
  def initialize(city, town, building)
    @city, @town, @building = city, town, building
  end
end
```

`mapping`はモデルの仮想カラムを呼び出すためです。第一引数がエンティティクラス、第二引数は値クラスになります。これにより`user.city_address`が`user.address.city`マッピングされるようになります。

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
サーバを起動しているターミナル上`byebug`が記載されているところで処理が止まり
コンソール上でデバックできるようになる
使い方
n               ステップオーバー(next)
s               ステップイン(step)
c               実行継続(continue)
fin             ステップアウト(finish)

h               ヘルプ表示(help)
h COMMAND       コマンドのヘルプを表示

変数名          変数の中身を表示
p 変数名        変数の中身を表示
eval 変数名     変数の中身を表示
変数名 = 値     変数に代入
v l             ローカル変数表示
disp 変数名     変数をウォッチする

---
デフォ以外
`gem 'minitest-reporters'`
test/test_helper.rb
testクラスに以下を追記するとminitestの結果が見やすくなる
```RuBy
require "minitest/reporters"
Minitest::Reporters.use!
```

`gem 'sqlite3', '1.3.13'`
sqlite

`gem 'faker'`
ユーザーを仮で複数作成する

`gem 'will_paginate','3.1.7'`
`gem 'bootstrap-will_paginate', '1.0.0'`
ページネーションする
例えば100人のユーザーを1ページに出力するのではなく
複数に分けて表示する

例
```rails
<% provide(:title, 'All users') %>
<h1>All users</h1>

<%= will_paginate %>

<ul class="users">
  <% @users.each do |user| %>
    <li>
      <%= gravatar_for user, size: 50 %>
      <%= link_to user.name, user %>
    </li>
  <% end %>
</ul>

<%= will_paginate %>
```
`will_paginate`はusersビューコードから@usersオブジェクトを自動で見つけ出し
ページネーションリンクを作成する。
```RuBy
$ rails console
  User.paginate(page: 1)
  #これで1ページ目30のユーザー分のデータが取り出せる nilの場合最初のページを表示

```
なお`@user = User.paginate(page: params[:page])`コントローラー等で代入して置かないと
上記のコードは機能しない
デフォルトは30個表示する
**params[:page]はwill_paginateによって自動生成される**

またコンテキストが違う場合（Usersコントローラのコンテキストからマイクロポストを
ページネーションしている場合など）明示的に渡す必要がある

またNextの表示を変える場合は変数を指定して表示設定を決める
`<%= will_paginate @books, :previous_label => ' &lt 前へ', :next_label => '次へ &gt' %>`


```RuBy
app/controllers/users_controller.rb
class UsersController < ApplicationController
  .
  .
  .
  def show
    @user = User.find(params[:id])
    @microposts = @user.microposts.paginate(page: params[:page])
  end
  .
  .
  .
end
```

追記
```RuBy
app/controllers/static_pages_controller.rb
def home
  if logged_in?
    @micropost  = current_user.microposts.build
    @feed_items = current_user.feed.paginate(page: params[:page])
  end
end
```

```rails
app/views/shared/_feed.html.erb
<% if @feed_items.any? %>
  <ol class="microposts">
    <%= render @feed_items %>
  </ol>
  <%= will_paginate @feed_items %>
<% end %>
```

このとき olタグのclassから@feed_itemsは各要素がMicropostを持っていることになるので
railsは勝手にMicropostのパーシャル(`app/views/microposts/_micropost.html.erb`)を
呼び出すことができた。
一つのマイクロポストを表示するパーシャル
```rails
app/views/microposts/_micropost.html.erb
<li id="micropost-<%= micropost.id %>">
  <%= link_to gravatar_for(micropost.user, size: 50), micropost.user %>
  <span class="user"><%= link_to micropost.user.name, micropost.user %></span>
  <span class="content"><%= micropost.content %></span>
  <span class="timestamp">
    Posted <%= time_ago_in_words(micropost.created_at) %> ago.
  </span>
</li>
```

`gem 'pg', '0.20.0'`
PostgreSQLを使用する

`gem 'carrierwave',             '1.2.2'`
CarrierWaveを導入するとrailsのジェネレータで画像アップすることができるようになる
`rails generate uploader Picture`
を実行してアップローダーを生成する(app/uploaders/image_uploader.rb　が生成される)
あとは`rails generate migration add_picture_to_microposts picture:string`などを行い
使用したいモデルにマイグレーションファイルから追加することで使用できる
例
```RuBy
app/models/micropost.rb
class Micropost < ApplicationRecord
  belongs_to :user
  default_scope -> { order(created_at: :desc) }
  mount_uploader :picture, PictureUploader
  validates :user_id, presence: true
  validates :content, presence: true, length: { maximum: 140 }
end
```
```rails
app/views/microposts/_micropost.html.erb
<li id="micropost-<%= micropost.id %>">
  <%= link_to gravatar_for(micropost.user, size: 50), micropost.user %>
  <span class="user"><%= link_to micropost.user.name, micropost.user %></span>
  <span class="content">
    <%= micropost.content %>
    <%= image_tag micropost.picture.url if micropost.picture? %>
  </span>
  <span class="timestamp">
    Posted <%= time_ago_in_words(micropost.created_at) %> ago.
    <% if current_user?(micropost.user) %>
      <%= link_to "delete", micropost, method: :delete,
                                       data: { confirm: "You sure?" } %>
    <% end %>
  </span>
</li>
```
上記のように真理値で画像があるかないかを返す`picture?`メソッドを提供してくれる

また拡張子のバリデーションは以下のように行う
```RuBy
class PictureUploader < CarrierWave::Uploader::Base
  storage :file

  # アップロードファイルの保存先ディレクトリは上書き可能
  # 下記はデフォルトの保存先  
  def store_dir
    "uploads/#{model.class.to_s.underscore}/#{mounted_as}/#{model.id}"
  end

  # アップロード可能な拡張子のリスト
  def extension_whitelist
    %w(jpg jpeg gif png)
  end
end
```

こちらは画像のサイズ（容量)のバリデーション
```RuBy
app/models/micropost.rb
class Micropost < ApplicationRecord

  validate  :picture_size

  private

    # アップロードされた画像のサイズをバリデーションする
    def picture_size
      if picture.size > 5.megabytes
        errors.add(:picture, "should be less than 5MB")
      end
    end
end
```

`gem 'mini_magick',             '4.7.0'`
環境に`brew install imagemagick`をインストールして
gem mini_magickを利用してrubyでも使えるようにできる
以下は400*400を超えた場合適切なサイズに縮小するオプション
```RuBy
app/uploaders/picture_uploader.rb
class PictureUploader < CarrierWave::Uploader::Base
  include CarrierWave::MiniMagick
  process resize_to_limit: [400, 400]
end
```
もしテストでこれがゲインでエラーになってしまう場合は以下のように設定すると
テスト時にはリサイズしないようになる
```RuBy
config/initializers/skip_image_resizing.rb
if Rails.env.test?
  CarrierWave.configure do |config|
    config.enable_processing = false
  end
end
```






その他
`Sprockets`
Rils3から導入されたgem
アセットファイル（js,cssなど）を効率よく管理するためのアセットパイプライン
の仕組みの基盤gem


---
開発環境のテスト環境
`group :development, :test do
  gem 'sqlite3', '1.3.13'
  gem 'byebug',  '9.0.6', platform: :mri
end`
主にデバックやDBについて記載する

開発環境
`group :development do
  gem 'web-console',           '3.5.1'
  gem 'listen',                '3.1.5'
  gem 'spring',                '2.0.2'
  gem 'spring-watcher-listen', '2.0.1'
end`


本番環境
`group :production do
  gem 'pg', '0.20.0'
end`

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
ただし、testでしようする場合は記載されてあると良いかもしれない

railsチュートリアル参考資料では以下のように書かれているが
```ruby
test/integration/users_profile_test.rb
require 'test_helper'

class UsersProfileTest < ActionDispatch::IntegrationTest
  include ApplicationHelper

  def setup
    @user = users(:michael)
  end

  test "profile display" do
    get user_path(@user)
    assert_template 'users/show'
    assert_select 'title', full_title(@user.name)
    assert_select 'h1', text: @user.name
    assert_select 'h1>img.gravatar'
    assert_match @user.microposts.count.to_s, response.body
    assert_select 'div.pagination'
    @user.microposts.paginate(page: 1).each do |micropost|
      assert_match micropost.content, response.body
    end
  end
end
```
インクルードしなくとも
```RuBy
app/helpers/application_helper.rb
module ApplicationHelper

  # ページごとの完全なタイトルを返します。
  def full_title(page_title = '')
    base_title = "Ruby on Rails Tutorial Sample App"
    if page_title.empty?
      base_title
    else
      page_title + " | " + base_title
    end
  end
end
```
を呼ぶことができることを確認している(ruby 2.37 rails 5.2.3)

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

```rails
<ul class="users">
  <% @users.each do |user| %>
    <%= render user %>
  <% end %>
</ul>
```
とした時に`render`は@userを参照する`(app/views/users/_user.html.erb)`
また以下のように持っているクラスから推測して参照することもできる
```RuBy
user.rb
def feed
  Micropost.where("user_id = ?", id)
end
```
```RuBy
home.rb
def home
  if logged_in?
    @feed_items = current_user.feed.paginate(page: params[:page])
  end
```
```rails
_feed.html.erb
<%= render @feed_items %>
```
この場合はfeedメソッドのMicropostクラスを参考にして_micropost.html.erbを参照しに行く


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
<%= debug @user %>

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
.requireメソッドがデータのオブジェクト名定め
.permitメソッドで変更を加えられるキーを指定する
permitmethodで許可していない項目については変更できないので
少なくともやらないよりはかなり安全性が上がる
返り値は許可された`params`ハッシュ(:user属性がない場合はエラーになります)


---
`本番環境のSSL化`
**config/environments/production.rb**
からconfig.force_sslをコメントアウトを解除する
本番用のWEBサイとでSSLを使える等にするためにはドメインごとにSSl証明書を購入
する必要があるがHeroku上ではHerokuのSSL証明書に便乗することができる(サブドメインのみ)

`||による条件分岐`
```RuBy
redirect_to(session[:forwarding_url] || default)
```
とすると`:forwarding_url`がnullならばdefaultを処理する

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


`テスト中にログインステータスを返す方法`
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
あとはテスト内でインスタンス変数を`assigns(:シンボル)`でよびだす

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

`html　aタグのhref属性target="_blank"のセキュリティ対策`
このタグを使用すると新しいウィンドウで開く
新しいオブジェクトを作ってしまうので悪意のあるコンテンツを導入されてしまう
危険性がある(フィッシングサイト(詐欺サイト))
対策としてrel属性にnoopenerを知っていする

`リクエスト先を保存する`
```RuBy
def store_location
  session[:forwarding_url] = request.original_url if request.get?
end
```
ログインしていないユーザーがフォームを使って送信した場合
転送先のURLを保存させないようにしとくと
ユーザがセッション用のcookieを手動で削除してフォームから送信するケースなどした場合の
対応ができる
ログインしているかチェックする時に使うと良いだろう

`一つ前の遷移元のリンクを取得する`
```RuBy
# root_urlはreferrerがなかったようのため
redirect_to request.referrer || root_url
```


`片方がnilの場合の評価演算テク`
```RuBy
session[:forwarding_url] || default
```
nilでなければsession[:forwarding_url]を使う

`サンプルユーザーを大量に作る方法`
gem 'faker'をbundle install
db/seeds.rb
```RuBy
User.create!(name:  "Example User",
             email: "example@railstutorial.org",
             password:              "foobar",
             password_confirmation: "foobar")

99.times do |n|
  name  = Faker::Name.name
  email = "example-#{n+1}@railstutorial.org"
  password = "password"
  User.create!(name:  name,
               email: email,
               password:              password,
               password_confirmation: password)
end

```
`rails db:migrate:reset`
`rails db:seed`

Example Userという名前とメールアドレスを持つ1人のユーザと
それらしい名前とメールアドレスを持つ99人のユーザーを作成する
create!にすることでユーザーが無効になった時falseではなく例外を
出すことができるのでデバックでは便利

また　
```RuBy
db/seeds.rb
.
.
.
users = User.order(:created_at).take(6)
50.times do
  content = Faker::Lorem.sentence(5)
  users.each { |user| user.microposts.create!(content: content) }
end
```
のようにするとorderメソッドで作成されたユーザーの最初の6にんを明示的に呼び
それぞれ50個分のマイクロポストを追加するようにできる。
`Faker::Lorem.sentence(5)`=> "Quaerat reiciendis optio voluptatum et."(ランダムな文章五つの単語のながさを設定)
**ユーザ毎に一遍にマイクロポストを作成すると見栄えが全て同じユーザーになってしまうのでわざわざ50times do users.eachで回している**

---
`テスト用のユーザーを大量に作る方法`
test/fixtures/user.yml
```RuBy
<% 30.times do |n| %>
user_<%= n %>:
  name:  <%= "User #{n}" %>
  email: <%= "user-#{n}@example.com" %>
  password_digest: <%= User.digest('password') %>
<% end %>
```

---

`論理値属性をDBに追加すると疑問符のついたメソッドを使えるようになる`
例
```RuBy
class AddAdminToUsers < ActiveRecord::Migration[5.0]
  def change
    add_column :users, :admin, :boolean, default: false
  end
end
#rails db:migrate
```

のように`admin`を`boolean`で追加すると

```RuBy
user = User.first
user.admin? => false
user.toggle!(:admin) => true
user.admin? => true
```
`admin?`メソッドが使用できる

---
`Strong Parameters(ストロングパラメータ)`
```RuBy
#これだとparamsの全てを初期化してしまうので
#セキュリティ面に問題が出る userのadmin権限をtureにできたりする
@user = User.new(params[:user])

#対策としてpermitを使用する
params.require(:user).permit(:name, :email, :password, :password_confirmation)
```

`before_actionなどのbeforeだけでメソッドを使うときのメソッドの隠し方`
```RuBy
class User < ApplicationRecord
  before_save   :downcase_email
  before_create :create_activation_digest

  private

    # メールアドレスをすべて小文字にする
    def downcase_email
      self.email = email.downcase
    end

    # 有効化トークンとダイジェストを作成および代入する
    def create_activation_digest
      self.activation_token  = User.new_token
      self.activation_digest = User.digest(activation_token)
    end
end
```
privateメソッドを使う
この場合は以下のようには呼べない
```RuBy
User.first.create_activation_digest
```
---
URLにメールアドレスを組み込みたいとき`
`account_activations/q5lt38hQDc_959PVoo6b7A/edit?email=foo%40example.com`
`%40を使用する`
これはエスケープ記法と呼ばれるものでURLで扱えない文字を扱えるようにするために使用される
`edit_account_activation_url(@user.activation_token, email: @user.email)`
のように名前付きルートでクエリパラメータを定義すると自動でエスケープしてくれる
コントローラでprams[:emaill]からメールアドレスを取り出すときも自動で解除してくれる

---
`クエリパラメーター`
名前つきルートに対してハッシュを引数として入れる
例
`edit_account_activation_url(@user.activation_token, email: @user.email)    `
**edit_account_activationsをresourceで宣言している**
参考:[Railsのlink_toにパラメータを追加する](https://ruby-rails.hatenadiary.com/entry/20150114/1421161200)

`メイラーテストはドメインホストを設定する必要がある`
```RuBy
config/environments/test.rb
Rails.application.configure do
  .
  .
  .
  config.action_mailer.delivery_method = :test
  config.action_mailer.default_url_options = { host: 'example.com' }
  .
  .
  .
end
```

`モデルはselfを省略できる`
```RuBy
class User < ApplicationRecord
  .
  .
  .
  # アカウントを有効にする
  def activate
    update_attribute(:activated,    true)
    update_attribute(:activated_at, Time.zone.now)
  end

  # 有効化用のメールを送信する
  def send_activation_email
    UserMailer.account_activation(self).deliver_now
  end

  private
    .
    .
    .
end
```

`自分で呼び出して自分を引数にするときはselfが使える`
```RuBy
# 有効化用のメールを送信する
def send_activation_email
  UserMailer.account_activation(self).deliver_now
end
```

```RuBy
def create
    @user.send_activation_email
end
```

`renderとredirect_toの違い`
render
アクション内で呼び出すviewメソッド。そのアクション内で@インスタンス変数として格納されたものは
ビューからruby構文で呼び出せる(RHTML)

redirect_to
httpリクエストをサーバーに送る
URL(http://~~)
HTTPメソッド(redirect_toはgetで固定)
クッキーとか

参考資料:[railsのrenderとredirect_toの違い](https://qiita.com/1ulce/items/282cccba1e44158489c8)

---
`パスワード期限をつける`
例えばuserモデルに
```RuBy
def password_reset_expired?
  reset_sent_at < 2.hours.ago
end
```
を実装する
意味としてはパスワード再設定メールの送信時刻が、現在時刻より2時間以上前 (早い) の場合
`reset_sent_at`はユーザーモデルのカラム名　方はdatetime

---
`有効期限切れにしてテストしたいとき`
`assert_match "expired", response.body`
response.bodyは、そのページのHTML本文をすべて返すメソッドで「expired」という語があるかどうかでチェックできる

`マジックカラム`
migrateでcreate_tableメソッドで呼ばれるtimestampsは、created_atとupdated_atという2つの「マジックカラム」を作成する
作成した時やsaveをした時にタイムスタンプのように自動で日付が書き込まれる


`モデルの順序を設定する`
```RuBy
app/models/micropost.rb
class Micropost < ApplicationRecord
  belongs_to :user
  default_scope -> { order(created_at: :desc) }
  validates :user_id, presence: true
  validates :content, presence: true, length: { maximum: 140 }
end
```

`default_scope`に`order(:created_at)`を設定すると昇順になる
`order(created_at: :desc)`は降順
descはrails3で使われた`order('created_at DESC')`名前のSQLを引数に入れる時の名残


`テストデータにてマイクロポストとユーザーを紐付ける方法`
```rails
test/fixtures/microposts.yml
orange:
  content: "I just ate an orange!"
  created_at: <%= 10.minutes.ago %>
  user: michael

tau_manifesto:
  content: "Check out the @tauday site by @mhartl: http://tauday.com"
  created_at: <%= 3.years.ago %>
  user: michael

cat_video:
  content: "Sad cats are sad: http://youtu.be/PKffm2uI4dk"
  created_at: <%= 2.hours.ago %>
  user: michael

most_recent:
  content: "Writing a short test"
  created_at: <%= Time.zone.now %>
  user: michael

<% 30.times do |n| %>
micropost_<%= n %>:
  content: <%= Faker::Lorem.sentence(5) %>
  created_at: <%= 42.days.ago %>
  user: michael
<% end %>
```
一番最後のコードは埋め込みrubyを使った複数のテストデータの作成

`procオブジェクト`
ブロックとはdo~endの塊
procとはブロックをオブジェクト化したもの
ブロック単体では実体はない
ブロックをオブジェクトに変換することで引き渡されたメソッド内で実行する
ブロックの引数は一つだけ
参考:Ruby block/proc/lambdaの使いどころ[https://qiita.com/kidach1/items/15cfee9ec66804c3afd2]


`エラー内容の日本語化`
`gem 'rails-i18n'`をbundle install

`config/application.rb`に`config.i18n.default_locale = :ja`をクラス内に追加

これでモデル以外の日本語化ができます。
モデル名の日本化はymlファイルに出力したいモデル名を記載します。

私の場合

config/locales/models/ja.yml


```rails
ja:
  activerecord:
    models:
      user: ユーザー
    attributes:
      user:
        name: 名前
        email: メールアドレス
        password: パスワード
        password_confirmation: パスワード確認

  activerecord:
    models:
      micropost: マイクロポスト
    attributes:
      micropost:
          content: 内容
```

としました。

models: はモデル名、attributes: はモデルの attributeの訳になります。

このファイルを読み込むために
config/application.rbに以下の内容をクラス内に書き込みます。

`config.i18n.load_path += Dir[Rails.root.join('config', 'locales', '**', '*.yml').to_s]`

これは正規表現を使用した`config/locales`以下のディレクトリ内にある全てのymlファイルを読み込むように指示するものになります。

するとエラー内容だけではなくなりlabelに記載されているものまで
動的に和訳することができます。

---

`多重代入`
`a, b = 1, 2 #=> [1, 2]`

---
`外部キーがnilで保存できるように許可する`
```RuBy
class Customer < ApplicationRecord
  has_many :orders
end

class Address < ApplicationRecord
  belongs_to :customer, optional: true
end
```
optional: trueを用いる





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

###　よく参考にするurl
[わかりそうでわからないでもわかった気になれるIT用語辞典](https://wa3.i-3-i.info/index.html)
[]()
[]()
[]()
[]()
[]()
