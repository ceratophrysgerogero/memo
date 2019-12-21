##　特に重要なメモ

`sqlに変数を入れる時は必ずクエリする`
```RuBy
def feed
  Micropost.where("user_id = ?", id)
end   
```

`全てのオブジェクトをエラーとして吐き出せるパーシャルを作っておくと良い`
```RuBy
<% if object.errors.any? %>
  <div id="error_explanation">
    <div class="alert alert-danger">
      The form contains <%= pluralize(object.errors.count, "error") %>.
    </div>
    <ul>
    <% object.errors.full_messages.each do |msg| %>
      <li><%= msg %></li>
    <% end %>
    </ul>
  </div>
<% end %>
```


---
`モデルの情報順序変え(古い順)`
```RuBy
  default_scope -> { order(created_at: :desc) }
```


---
`modelとmodelの紐付け`
マイクロポストから見たときマイクロポストとユーザーは一対一の関係にある
```RuBy
app/models/micropost.rb
class Micropost < ApplicationRecord
  belongs_to :user
end
```
ユーザから見たときユーザーとマイクロポストの関係は一対多の関係にある
```RuBy
app/models/user.rb
class User < ApplicationRecord
  # 一緒に削除されることを保証する
  has_many :microposts, dependent: :destroy
end
```

`DB内のデータを順序をつけて取り出したいときはindexをつける`
```RuBy
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
この例では複合インデックスを使用している
これは二つ目の引数をインデックスに指定することにより条件が一致しているuser_idを全て
メモリーにロードせずにcreated_atでロードする情報を絞れやすくなる

---
`ページネート`
`Gemfile
gem 'will_paginate'
gem 'bootstrap-will_paginate'
`

```RuBy
#アクションにpaginateメソッドを使う
def index
  @users = User.paginate(page: params[:page])
end
```

htmle.erbにページネート表示を追加する(表示が英語でいいなら変数を指定する必要はない)
```rails
<%= will_paginate @books, :previous_label => ' &lt 前へ', :next_label => '次へ &gt' %>
```
テストはdiv.paginateがあるかを確認
ユーザーからpaginateメソッドを使用して最初に表示されるユーザーを取り出し
実際に表示されているかをa[href=?]で調べると良い

---
`game faker 使い方`
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

`ログイン強要した後にログイン前のurlに遷移させる方法(sessionで実装)`
```RuBy
# 記憶したURL (もしくはデフォルト値) にリダイレクト
def redirect_back_or(default)
  redirect_to(session[:forwarding_url] || default)
  session.delete(:forwarding_url)
end

# アクセスしようとしたURLを覚えておく
def store_location
  session[:forwarding_url] = request.original_url if request.get?
end
```


`統合テストでコントローラーが定義したインスタンス変数にアクセスする`
テスト内部で`assigns(:user)`とすると`@user`が呼べる
なのでできるだけテストで使いそうな変数はインスタンス変数にした方が良いかもしれない

`return false if ~`
```RuBy
if ~
 false
else
end
```

`仮想属性追加`
models
```RuBy
  attr_accessor :remember_token
```

`ユーザーログイン状態永続化などの注意点まとめ`
cookiesを使用する
sessionメソッドを使用した情報の保持はブラウザが閉じるまでしか有効ではないので
一定の安全性が確保できるが永続化できない
永続化するとセッションハイジャックされ悪用される可能性がある
主にセッションに保持しているトークンを盗み出す方法は四通り

1.管理の甘いネットワークでパケットスニッファというアプリを使用してcookieを抜き出す
2.データベースからトークを抜き出す
3.クロスサイトスクリプティングを使う
4.物理的にパソコンやスマホを操作してアクセスを奪い取る

対策
1.SSL化
2.ハッシュ値で保存
3.railsでは入力した内容を全てエスケープ文字に変えてくれる
4.ログアウトしたときにトークンを必ず変更するようにするまた重要な情報を表示するときはデジタル署名を行う

`テストのときのリダイレクトの仕様`
例えば
post通信したときにリダイレクトするような構図をテストする場合は
リダイレクト先は決定しているが実際にリダイレクトする訳ではない
```RuBy
#リダイレクト先があっているか
assert_redirected_to @user
#リダイレクトする
follow_redirect!
#リダイレクト先のviewが正しいか
assert_template 'users/show'
```
といった感じでテストすると良い

`ヘルパーメソッドをテストで使いたい場合`
test/test_helper.rbに丸ごとメソッドをコピーする
ただし元とわかりにくくなるの命名には気をつけること

`redirect_toは省略できる`
```RuBy
redirect_to(user_url(@user.id))
```
は、
```RuBy
redirect_to @user
```
に省略できる

`ハッシュ化`
modelにて
```RuBy
# 渡された文字列のハッシュ値を返す
def User.digest(string)
  cost = ActiveModel::SecurePassword.min_cost ? BCrypt::Engine::MIN_COST :
                                                BCrypt::Engine.cost
  BCrypt::Password.create(string, cost: cost)
end
```



---
`headerとshimはパーシャルとして（_header.html.erb)分けた方がいい`

---
`html5対応`
```rails
<!--[if lt IE 9]>
  <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/r29/html5.min.js">
  </script>
<![endif]-->
```

---
`埋め込みrubyを使ってタグの生成`
```rails
<% flash.each do |message_type, message| %>
  <%= content_tag(:div, message, class: "alert alert-#{message_type}") %>
<% end %>
```

---
`postやgetをしたときに正しい先にリダイレクトできているかテスト`
```rails
follow_redirect!
assert_template 'users/show'
```

---
`flash使い方`
コントローラーなどで`flash[:success] = "Welcome to the Sample App!"`宣言
viewで
```rails
<% flash.each do |message_type, message| %>
  <div class="alert alert-<%= message_type %>"><%= message %></div>
<% end %>
```
リダイレクトするとリクエストなのでflashは消えるがrenderメソッドでレンダリングしてもリクエスト
としてみなさないので消えない。そのため
コントローラーで` flash.now[:danger] = "~"`といったようにすると次のリクエストが発生したときに
消えるようになる


---
`formforの送信先変更`
以下だと resources :usersが優先される為URLは、post /usersになる

app/views/users/new.html.erb
```rails
<%= form_for(@user) do |f| %>
```

以下だと名前付きルートに変更される
```rails
<%= form_for(@user, url: signup_path) do |f| %>
```

---
`postやgetのアクセスの書き方(主にtestから)`
```rails
post users_path, params: { user: { name:  "",
                                     email: "user@invalid",
                                     password:              "foo",
                                     password_confirmation: "bar" } }
```

---
`ルート変更`
プロトコル　'名前付きルートにしたい名', to: 'コントローラー#アクション'
例
get  '/signup',  to: 'users#new'


---
`複数のビューでしよするパーシャルを格納しておくディレクトリの慣習`
mkdir app/views/shared
またファイル名の最初にアンダーバーを付け加える
例　`_error_messages.html.erb`

呼び出し方
` <%= render 'shared/error_messages' %>`

また `<%= render @user %>`とした時Userオブジェクトリストを推測して
users/`_user_html.erb`を呼び足してくれる

---
`saveメソッドがfalseの場合に使えるエラーメッセージ`
`user.errors.full_messages`にメッセージを生成する


---
`重要なデーターを取り扱うときに使うストロングパラメーター`
更新するカラムを指定し権限をつけること
基本的にコントローラーで行う
```RuBy
params.require(:user).permit(:name, :email, :password,
                             :password_confirmation)
```

---
`クロスサイトフォージェナリー対策`
protect_from_forgery with: :exception
主にapp/controllers/application_controller.rbにつけておく

---
selfを使用しなければローカル変数を作成してしまう罠
```RuBy
class User < ApplicationRecord
  attr_accessor :remember_token
  .
  .
  .
  def remember
    self.remember_token = ...
    update_attribute(:remember_digest, ...)
  end
end
```
このようにclassの最初で宣言したものを使うならselfで指定する必要がある



---
=を使わずに属性を変更するメソッド
例えば
`name.downcase!`
などがある

---
読み込んだcssファイルに`*= require_tree .`記載されていたら全てscssファイルを統合して適用する

---
`gem bcrypt を使用しているときにymlファイルを使用したtest`
password_digest属性をymlファイルに追加する

---
`リクエストパラメータを取り出す`
```rails
params[:カラム名  ]
```

---
`layoutにデータを引き渡す`
```rails
<% provide :title, "ページ個別タイトル" %>
```

```rails
<title><%= yield :title %></title>
```

---
test用のuserデータ作成方法
```Rails
michael:
  name: Michael Example
  email: michael@example.com
  password_digest: <%= User.digest('password') %>
```
呼び出し方
```RuBy
def setup
 user = users(:mishael)
end
```

---
modelバリデーションなど
app/models/user.rb
```RuBy
class User < ApplicationRecord
  #"" "  "を禁止する
  validates :name,  presence: true
  #文字列の長さを制限する(50)
  validates :name,  length: { maximum: 50 }

  #メールフォーマット(簡易)
  #..comみたいなドットが連続した物にも対応
  VALID_EMAIL_REGEX = /\A[\w+\-.]+@[a-z\d\-]+(\.[a-z\d\-]+)*\.[a-z]+\z/i
  validates :email, format: {with: VALID_EMAIL_REGEX}
  #一意性
  validates :email, uniqueness:true
  #大文字小文字を無視した一意性(これではデータベースLVの一意性を保てない)
  validates :email, uniqueness:{case_sensitive: false}
  #DBにpassword_digest属性(string)を保存できるようになる(rails g　で作る必要はある)
  #仮装属性　passwordとpassword_confirmationを使用できる　一意性バリデーションメソッド追加
  # authenticateメソッド　引数の文字列がパスワードと間違っているとfalse
  #パスワードをハッシュ化するために gem bcryptを使うことがおすすめ
  has_secure_password
  validates password, allow_nil: true
  #空でも更新できる
end
```

---
`has_secure_passwordを使ったデータベースからデータの探し方`
```RuBy
user = User.find_by(email: params[:session][:email].downcase)
#引数をハッシュ化してDBにあるpassword_digestカラムの値を比較している
if user && user.authenticate(params[:session][:password])
```


---
データベースLVで一意性を保つ方法

```RuBy
db/migrate/[timestamp]_add_index_to_users_email.rb

class AddIndexToUsersEmail < ActiveRecord::Migration[5.0]
  def change
    #一意性
    add_index :users, :email, unique: true
  end
end
```

---
メールアドレスバリデーションチェックテンプレ(簡易版)
```RuBy
test "email validation should accept valid addresses" do
  valid_addresses = %w[user@example.com USER@foo.COM A_US-ER@foo.bar.org
                       first.last@foo.jp alice+bob@baz.cn]
  valid_addresses.each do |valid_address|
    @user.email = valid_address
    assert @user.valid?, "#{valid_address.inspect} should be valid"
  end
end
```
inspectはオブジェクトを文字列の状態に変換して取得する
%wは配列を作る


---
オブジェクトの複製
```RuBy
origin = "hoge"
=> "hoge"

copy = origin.dup
=> "hoge"

origin.object_id
=> 70118270776180

copy.object_id
=> 70118270801780
```

---
WEB上でデバック方法
```rials
<%= debug(params) if Rails.env.development? %>
```

```
@mixin box_sizing {
  -moz-box-sizing:    border-box;
  -webkit-box-sizing: border-box;
  box-sizing:         border-box;
}

/* miscellaneous */

.debug_dump {
  clear: both;
  float: left;
  width: 100%;
  margin-top: 45px;
  @include box_sizing;
}
```

---
##テンプレ
---
`test`
```RuBy
require 'test_helper'

class UsersLoginTest < ActionDispatch::IntegrationTest

  test "login with invalid information" do
    get login_path
    assert_template 'sessions/new'
    post login_path, params: { session: { email: "", password: "" } }
    assert_template 'sessions/new'
    assert_not flash.empty?
    get root_path
    assert flash.empty?
  end
end

```

---
`ログインやログアウトといった入力フォーム`
```rails3
<% provide(:title, "Log in") %>
<h1>Log in</h1>

<div class="row">
  <div class="col-md-6 col-md-offset-3">
    <%= form_for(:session, url: login_path) do |f| %>

      <%= f.label :email %>
      <%= f.email_field :email, class: 'form-control' %>

      <%= f.label :password %>
      <%= f.password_field :password, class: 'form-control' %>

      <%= f.submit "Log in", class: "btn btn-primary" %>
    <% end %>

    <p>New user? <%= link_to "Sign up now!", signup_path %></p>
  </div>
</div>
```
