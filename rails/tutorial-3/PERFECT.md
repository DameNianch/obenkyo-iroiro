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



# Rails風味のRuby
この章は少なそうなので、3章と合併

## ヘルパー
### ヘルパーとは？
- 主にRailsのviewsに用いられるメソッド
- コードの再利用を意識
- https://www.rubyguides.com/2020/01/rails-helpers/
- Railsでは、module ApplicationHelperが自動的にヘルパーモジュールを読み込み

今回は、それの組み込みやつ
```
<%= hogehugapiyo %>
```
というERB記法に従って、実行可能

### 組み込みヘルパー
app/views/layouts/application.html.erb 内の
```
<%= stylesheet_link_tag 'application',
    media: 'all','data-turbolinks-track': 'reload' %>
```
は、4つのRuby概念を含有
- Railsの組み込み関数
- 非かっこメソッド呼び出し
- シンボル
- ハッシュ

これらの4要素が、この章では説明される。

### カスタムヘルパー
組み込みヘルパーだけでなく、自作も可能。/app/helpers/hoge.rb に記述すると思われる。組み込みのそれと同様に、ERB記法に従って実行可能

## 文字列とメソッド
- ナンバー記号#でコメントアウト
- "#{hoge}"で、hogeに代入された文字列を式展開
- 文字列出力
    - puts: put stringの略
    - print: putsの改行なし
- クオーテーション
    - シングル: 式展開なし
    - ダブル: 式展開あり

## オブジェクトとメソッド
- オブジェクト: メッセージに応答するもの
- メソッド: そのメッセージ
- メソッドチェーン: nil.empty じゃなくて nil.to_s.empty とするような操作
## 条件
- and: &&
- or: ||
- not: !
- bang bang: !! は理論値になんでも変更可能

Rubyのメソッド注意点
- メソッドは、かっこなしでもデフォルト値を参照して呼び出し可能
- 最後に評価した式を暗黙的に返す
- 明示的に戻り値の指定も可能

## 配列と範囲演算子
- 配列:  ["foo", "bar", "baz"]
- これも配列:  [42, 8, 17, 6, 7, "foo", "bar"]
- 範囲演算子: 0..9 のように使用

## ブロック
「{}」か「do end」で囲む

あとでやる
4.3.2と4.3.3の演習

## ハッシュとシンボル
ハッシュ≒連想配列であり、ただの配列と異なり整数値以外のキー（インデックス）を使用可能。ただし、並び順の保証は（一応）ない。キーに文字列を使う代わりに、シンボルを用いることが可能。さらに、もっと書きやすくできる。
```
user_str = { "first_name" => "Michael", "last_name" => "Hartl" }
user_sim = { :name => "Michael", :last_name => "Hartl" }

user_more = { name: "Michael", last_name: "Hartl" }
```
ハッシュをメソッドから最後の引数として呼び出すならば、ハッシュの波かっこは不要

```
>> String.class
=> Class
>> String.superclass
=> Object
>> String.classhoge
Traceback (most recent call last):
        1: from (irb):23
NoMethodError (undefined method `classhoge' for String:Class)
Did you mean?  class
```
Classってなんだろう。

4.4はまとめていない



