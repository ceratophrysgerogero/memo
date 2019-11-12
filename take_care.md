##忘れてそうなこと
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
end
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

```css
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
