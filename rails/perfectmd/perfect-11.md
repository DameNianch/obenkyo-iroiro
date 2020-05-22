# アカウントの有効化

仮ユーザーのメールアドレス確認
- 有効化の属性をunactivate（←inactivate、、、？）
- 有効化トークン付きURLをユーザーに送信
- ユーザーがアクセスでactivate
- activateと同時にデータベース保存

## セキュリティーまわりのことをなんか書く
- aaa
- hoge
- huga

## mailer
- HTMLメールとテキストメール選択可能
    - app/views/layouts/
- application_mailer.rb
    - default from
    - layout
- user_mailer.rb
    - 宛先とインスタンス変数
    - application_mailerとuser_mailerの使い分けがわかっていない。
    - 


```
host = 'localhost:3000'                     # ローカル環境
config.action_mailer.default_url_options = { host: host, protocol: 'http' }
```

なぜローカル環境ではhttpなのか？httpsにしたら送られたリンクを踏んだときに死ぬ。

