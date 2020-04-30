# GitHub Flow完全に理解した。
## GitHub Flowとは
頭ゆるふわでもイケるブランチ戦略
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

### メリット

