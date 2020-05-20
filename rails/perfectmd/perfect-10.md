# ユーザーの更新・表示・削除

## ユーザーの更新
ユーザーデータの変更editを考える。
- 基本姿勢は、newアクションと同様
- newのcreateはPOST
- editのupdateはPATCH
- PATCHリクエストは、普通には送信不可
- どっちのリクエストを用いるかはrailsが内部で判断
    - データベース上の存在ユーザー向けフォーム
    - データベース上の非存在ユーザー向けフォーム


*i このコードがリスト 7.15と極めて似通っていることに注目してください。重複が多いということは、それらのコードの繰り返しをパーシャルにまとめることができるということです。* パーシャルの役割をようやく理解した。


認証と認可の差異
- 認証: サイトのユーザー識別
- 認可: ユーザーの実行可能操作の管理
管理・制御機構をセキュリティモデルと呼ぶ


```
  test "should redirect destroy when not logged in" do
    assert_no_difference 'User.count' do
      delete user_path(@user)
    end
    assert_redirected_to login_url
  end
```
assert_no_differenceの書き方わかっていないから調べておく。

*i 試しにリスト 10.59にある管理者ユーザーのbeforeフィルターをコメントアウトしてみて、テストの結果が redに変わることを確認してみましょう。*
変わらなかったので調べておく