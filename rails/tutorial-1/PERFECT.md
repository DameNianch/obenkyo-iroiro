# ゼロからデプロイまで
- 使った資料: https://railstutorial.jp/chapters/static_pages?version=5.1
- 理由: おすすめされたから（なんも分かっていない）

## できるようになること
- RailsによるWeb開発
- Web開発で重要な内容

## 方針
- 演習問題をたくさん
- 演習問題と本編をなるべく分離
- エラーはググレカス
- 充実した基本的なことからの説明（コマンドラインの説明まである。）

## Railsとは
- Ruby on Rails
- Web開発フレームワーク
- 動的なWebアプリケーションが得意
- RESTという設計思想に基づく
- MVCアーキテクチャパターンを採用
    - Model: DBとのやりとりするRuby object
    - View: ユーザーがブラウザから見るやつ
    - Controller: Modelと対話してViewを生成するやつ

## 気を付けること
- rubyのインデントはスペースx2 

## Railsの入手
rubyのインストール
- https://railsgirls.jp/install
- 適宜良い感じに

おまじない（僕はこれをしなかったため、railsのインストールに時間がかかったと思われる。）
```
$ printf "install: --no-document \nupdate:  --no-document\n" >> ~/.gemrc
```
からのrailsインストール
```
$ gem install rails -v 5.1.6
```
ここでのgemはパッケージマネージャーとしてのgemっぽい。

以下でスケルトン（標準化された雛形）を自動的に作成
```
$ rails _5.1.6_ new hello_app
```
できたスケルトンの構成内容は、全く分からんが後に説明されるっぽい。
bundlerは複数gemの依存関係を良い感じに保ちながら、インストールできるすごいやつっぽい。でもこれはいつインストールされたんだ？

```
$ bundle update
$ bundle install
```
１行目のupdateは無くてもワンチャンあるかもしれないが、ならないはず。
```
$ rails server
```
を実行して、localhost:3000にブラウザからアクセス。（ここら辺の仕組みを理解していないけど、どうせこんな感じでイケるだろぐらいの感覚で進めているので調べておく。）

## Hello Worldする
ブラウザとコントローラーの間にルーターというものを入れる。このルーターは、ブラウザからのリクエストをコントローラーに振り分ける役割を果たす。これにより、デフォルトページの差し替えが可能となったりする。これを実際に行うのは、*config/routes.rb*である。
このファイルの文法は
```
root 'controller_name#action_name'
```
という書き方をする。*app/controllers/application_controller.rb*と*config/routes.rb*は以下のようなあああああ（完全にめんどくさくなった。あとでなんんとかする。）

## git色々
もしかして、gitリポジトリの中でrails newするのはよくない？
なんと無くだが、プロジェクト単位でrails newしてからそこをリポジトリとする気がしてきた。
```
$ tree -aL 5
.
├── .git
│   └── 略
├── README.md
├── github-flow
│   └── PERFECT.md
└── rails
    └── tutorial-1
        ├── PERFECT.md
        └── environment
            └── hello_app
                ├── .git
                ├── .gitignore
                ├── Gemfile
                ├── Gemfile.lock
                略
                └── vendor
```
## デプロイ
デプロイサービスの違いを分かっていないので、調べておく
### Heroku
Herokuは、SQliteが使えないらしい。
- プロダクション環境: PostgreSQL
- テスト環境: SQlite

という設定にGemfileを書き換える。（全部PostgreSQLにすればよくないか？という疑問）








