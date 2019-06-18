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

## 忘れそうな知識
`rake`
rails4まではrailsとrakeコマンドは別れていたがrails5になってからrailsでもrakeを実行できるようになった

`spring`
rails4.1から標準で付属したアプリケーションプリローダー

`テンプレート`
railsでのテンプレートはビューをさす


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

f2(42, "answer", [4, 8, 10]) # => [42, "answer", [4, 8, 10]]


## ファイル解説
`gemspec`
gemの依存関係を記述する

`gemfile`
依存するgemの取得先を記述している

`Gemfile.lock`
開発環境と運用カントで同じgemをインストールする時に使用する  

`_helper.rb`
app/helpers/ビューに対応したコントロラー名.rb
ここで記載したメソッドは対応したビューで使用できる

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
```Ruby
validates :content, presence: true
```
app/models/micropost.rb
content空禁止
他のバリデーションと両立させる場合は[,]で区切って追加
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


```Ruby
assert_response :success
```
http 200 OK
リクエストは成功し、レスポンスとともに要求に応じた情報を返せた
```Ruby
assert_select "htmlタグ","タグ内に記載されて欲しい記述"
```
指定したタグ内に記載されて欲しい記述があるかどうかチェックする
```Ruby
yield
```
処理された内容を埋め込む先を指定する
`provide`で指定された内容や共通なレンタリング（application.html.erbを使用して）を使いそれぞれのビューをレンタリングする際に使用する
application.html.erbで`<%= yield %>`と使用すると各ページの内容がここで挿入される
`provide`で指定された場合は`<%= yield(:タグ名) %> `と記述することで文字通り`provide`提供された物を`yield`産出することができる
```Ruby
provide(:タグ名, "yieldに入れたい内容")
```
個別レイアウトから共通レイアウトに画面を表示する際に使う
`content_for`と同じ挙動だが`content_for`ではアセットパイプラインがうまく動作しなかったりrailsのストリーミングの挙動が違ったりする
参照 https://qiita.com/pochi355/items/02dd10e32bf5034b383b
基本は`provide`を使用して問題ない


## gemfile(パッケージ)
デフォ

---
デフォ以外
`gem 'minitest-reporters'`
test/test_helper.rb
require "minitest/reporters"
Minitest::Reporters.use!
testが見やすくなる
