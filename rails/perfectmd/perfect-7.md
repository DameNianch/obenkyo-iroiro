# ユーザー登録
## RESTful URI
routes.rbに追加すると色々使えるようになったことを復習しておく。

## 実行環境
Railsは3つの実行環境を持つ
- develop
- test
- production: デバッグを表示するべきでない。

```
<%= debug(params) if Rails.env.development? %>
```
をerbファイルに埋め込んでデバッグの表示を切り替える。（このparamsってなんなんだ！？userモデル（表面ではコントローラ）に紐づいた変数ということっぽい。しかし、id=1ってなんだ？）

または、debuggerメソッドを差し込んで、コンソールからアプリケーションの状態を確認

```
image_tag(gravatar_url, alt: user.name, class: "gravatar")
```
のクラス指定がきもいと思ったけど、しょうがないというか、そうなるべき


## ユーザー登録画面
### formの生成
bootstrap理解していないと半分ぐらい何やっているか理解できん。後で読んでおく。
- http://websae.net/twitter-bootstrap-grid-system-21060224/ 

Active Recordも理解していないと、なんでできるのかわからん。
- https://railsguides.jp/active_record_basics.html
- https://api.rubyonrails.org/classes/ActiveRecord/Base.html
- https://qiita.com/penguin_note/items/adb0b9bf7c13c1b1d44d


### formの処理
1. formからPOSTを/userに送信
2. 新規ユーザーを仮作成
3. 仮作成したユーザーの検証
4. Strong Parametersでパラメータ指定

マスアサインメント脆弱性とは？

もし、formデータを受信後
- errors.full_messagesオブジェクトを参照
-  errors.emptyがfalseでなければ、pluralizeを活用してエラー出力
- errors.emptyがtrueならば、flashを活用して、成功ページにリダイレクト


## デプロイ注意事項
SSL接続に変更
- 誰が
- どのくらい
- できちゃうの？



