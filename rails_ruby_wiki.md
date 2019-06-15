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
rails4まではrailsとrakeコマンドは別れていたがrails5になってからrailsでもrakeを実行できるようになった

## railsファイル解説x
`gemspec`
gemの依存関係を記述する

`gemfile`
依存するgemの取得先を記述している

`Gemfile.lock`
開発環境と運用カントで同じgemをインストールする時に使用する  
-

## コマンド  

`bundle update`
gemfile.lockを更新する

`bundle install`
gemfile.lockを元にインストール


`rails railsのバージョン new アプリ名`
新規プロジェクト作成

`rails server`
railsアプリケーションを起動する

`rails generate scaffold モデル名 カラム名1:データ型1, カラム名2:データ型2`
マイグレーション
モデル
コントローラー（index show new edit create update destroy アクションを作成)
ルーティング追加
コントローラーで適宜されたアクションに対応するビュー
が生成される
注意：テーブルの作成はしてないので`rails db:migrate`を忘れないこと

## メソッド

`validates :content, length: { maximum: 140 }`
app/models/micropost.rb
contentの長さを140までにする

`has_many :microposts`
app/models/user.rb
userモデルは、複数のmicropostsを所持する（関連づける）
`belongs_to :user`
app/models/micropost.rb
micropostモデルは一つのuserをもつ（関連づける）
関連づけが完了すると以下のようにUserクラスからファースト
ユーサーのマイクロポストを取得できるようになる
User.first.microposts.first.user

`resources :microposts`
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
