# Claude Code API テスト用リポジトリ

このリポジトリは、GitHub Actionsを用いたClaudeでの自動レビューを試してみるリポジトリです。

## 説明
ここにClaude Code APIを使ったCI/CDについての説明文を記述します。

## トリガー

### プルリクエスト作成
プルリクエストを作成すると、自動でClaude Codeによるレビューが行われます。

Claude Codeによるレビューの結果はプルリクエストのコメントに投稿されます。

### `@claude`
イシュー本文とコメント・プルリクエストのコメントにて
`@claude` を使用すると、Claude Codeに指示ができます。

Claude Codeへ指示する`@claude`という文字列は `.github/workflows/claude-auto-review.yml` にて定義されています。ファイル内の記述を変更すれば、他の文字列に変更することも可能です。

Claude Codeによるレビューの結果はイシュー / プルリクエストのコメントに投稿されます。
