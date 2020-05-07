# ほぼ静的なページの作成

## 関係ないけど
- ドキュメントが、日本語なので助かる。
    - 「あなたの全データの安全な家」のような日本語ではなさそう）
    - https://railsdoc.com/rails_base
- 質問になっていない形式の何かをまとめておかないと、長期連休後に死ぬ。


## セットアップ
いつも通り以下の手順
```
$ rails "railsのver" new "アプリ名"
```
からの"アプリ名"ディレクトリ内のGemfile編集
```
$ bundle install --without production
```
ダメなら
```
$ bundle update
```

app/controllers/application_controller.rb にアクションの追加と config/routes.rb にルーティング設定

```
$ git commit -am "なんかコメント"
$ heroku create
$ push heroku master
$ heroku open
```

## 静的ページ
方針
- まず静的なページ作成
- MVCのC内にアクション追加
- 動的なページに移行

まず、いろいろ生成
```
$ rails generate controller StaticPages home help
```
controllerの生成だけではなく、config/routes.rb
とapp/views/static_pagesにも注目。あとで出てくるtest/を気に留めておく。

キャメルケースで書いたのに、スネークケースの何かが生成されるのは、いい感じにやってくれることになっているの？（コーディング規約的なもので世界共通にするため？）という疑問に対する答え
https://api.rubyonrails.org/classes/ActiveSupport/Inflector.html#method-i-underscore

### railsの振る舞い
- hogeというURLへのアクセス
- hogeというアクションを実行
- 対応するMVCのVを出力

## テストから始める
自動化テストを作成することで以下のメリット。後でまとめておく。
- バグを追跡するため時間減少
- テストコードがドキュメントになる。
- TDDという開発方式も可能

Guardfile書けるようになる気がしない。
Guard使用時のSpringとGitの競合を防ぐってなんなん

