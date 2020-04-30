# GitHub Flow完全に理解した。
## GitHub Flowとは
まだわからん。けど、ブランチモデルという何かっぽい。ブランチ戦略とも呼ばれるのか？
https://gist.github.com/Gab-km/3705015


## なぜGitHub Flowなのか
### git-flow
- 難しいらしい。
- リリース（ユーザーアクセス？）が前提

### GitHub Flow
- 簡単らしい。
- デプロイ（ユーザーアクセスなし？）が前提

確かに https://www.atmarkit.co.jp/ait/articles/1708/01/news015.html を読む限り、統一的な扱いは、git-flowよりGitHub Flowが簡単に見える。


## GitHub Flowの思想
- masterブランチのものはデプロイ可能
- 作業の象徴的な単語でmasterからbranch作成
- PRは、masterへのmergeか相談で使用
- レビューからのmergeからの即デプロイ
- masterに動かないものをpushすると命は無い。
- masterでする奴はいないな。
- masterから長期間離れた場合は、masterをmergeしろ。

### 以下わからんこと
- 我々がpushしたすべてのブランチではテストが実行され、その結果がチャットルームに報告される。「もしテストを手元で実行していない場合には、サーバー上のトピックブランチ（たいていは1つのコミットだけのブランチ）にpushして、 Jenkins がその結果を教えてくれるのを待つこともできる。」
- デプロイを行った時だけ更新される deployed ブランチを用意することもできるが、我々はそのようなことはしない。 我々は、現在デプロイされているSHA（ハッシュ）をWebアプリ経由で公開するようにし、比較が必要な場合はそれを単に curl するだけにしている。



