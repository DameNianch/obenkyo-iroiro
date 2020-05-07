# Toyアプリケーション
どうも、各章の最後にある「本章のまとめ」を理解すればいいことに気が付いた。ということで、それらの項目についてそれぞれ理解することにした。

## Scaffold機能
とりあえず
```
$ rails _5.1.6_ new toy_app
```
してGemfile書き換え、プロダクションとの兼ね合いに注意して
```
$ bundle install --without production
```
する。ここから、弱小twitter的なものをつくる。その前に、データモデルを決定
ああああ。めんどくさいので後回し。

## MVCを使いこなす
Usersリソースとは？

まず、そのデータモデルを自動生成？こいつは何をgenerateしてるんだ？
```
$ rails generate scaffold User name:string email:string
```
Userは、データモデル名にあたり、残りがデータモデルの持つデータの内容の指定を意味する。generate以外にもオプションはあるのか調べておく。
よくわからんが、何かから何かへDBを移行
```
$ rails db:migrate
```
してから
```
$ rails server
```
する。そこから、http://localhost:3000/users をブラウザから見れば、ユーザー作成画面が出現



## RESTをあああ

## データvalidation

## データモデル

## Railsコンソール