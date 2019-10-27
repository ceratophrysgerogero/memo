`クロスサイトフォージェナリー対策`
protect_from_forgery with: :exception
主にapp/controllers/application_controller.rbにつけておく

---
`rails g controller 複数形大文字（StaticPages）　必要なアクション名`

---
読み込んだcssファイルに`*= require_tree .`記載されていたら全てscssファイルを統合して適用する
