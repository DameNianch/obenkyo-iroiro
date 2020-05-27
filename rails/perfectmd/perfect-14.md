# hogee


*i 無意味なテストではないことに注意してください (followersについても同様です)。つまり、もし@user.following.empty?の結果がtrueであれば、assert_select内のブロックが実行されなくなるため、その場合においてテストが適切なセキュリティモデルを確認できなくなることを防いでいます。*
セキュリティーモデルとは？

```
respond_to do |format|
  format.html { redirect_to @user }
  format.js
end
```
わからんです。

```
# 認証トークンをremoteフォームに埋め込む
config.action_view.embed_authenticity_token_in_remote_forms = true
```
さっぱりだ



