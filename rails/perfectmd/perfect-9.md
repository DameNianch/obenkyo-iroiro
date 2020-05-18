# Remember me

- sessionメソッドでは、ブラウザを閉じると同時にユーザーIDは消える。
- cookiesメソッドで、半永続化可能


*i ブラウザのcookiesに保存するユーザーIDは暗号化しておく。* なんでだ？というか、あんまり流れを理解していないんだろうなぁ。

*i 記憶ダイジェストはユーザーが直接読み出すことはないので (かつ、そうさせてはならないので)、remember_digestカラムにインデックスを追加する必要はありません。* わざわざ書いた理由がわからん。


*i そのトークンをダイジェストに変換したものをデータベースに保存します。fixtureをテストするときにdigestメソッドを既に作成してあった* っけ？という気持ち



```
  # 渡されたトークンがダイジェストと一致したらtrueを返す
  def authenticated?(remember_token)
    BCrypt::Password.new(remember_digest).is_password?(remember_token)
  end
```
ちょっとこれの理解は後回し。

modelsに書くのかhelperに書くのか。controllerに書くのか。全くわかっていない問題

```
<%= f.label :remember_me, class: "checkbox inline" do %>
```
がなぜdouble quotesなのか理解していないのでヤバイ。


rubyのraise何してんのか確認

*i assert_equalの引数は「期待する値, 実際の値」の順序で書く点に注意してください。*　はいごめんなさい。全くすれていました。