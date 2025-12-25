# 生成AIによる自動レビューのテスト用リポジトリ

このリポジトリは、GitHub Actionsを用いた生成AIでの自動レビューを試してみるリポジトリです。

## 説明
ここに生成AIを使ったCI/CDについての説明文を記述します。

### 参考

- Claude Code GitHub Actions について: https://code.claude.com/docs/ja/github-actions
- Claude Code GitHub Actions のGitHub Actionsのリポジトリ: https://github.com/anthropics/claude-code-action
- YMLファイルの記載例: https://github.com/anthropics/claude-code-action/blob/main/examples/claude.yml



## Claude Code

Claude Codeによるレビューの結果はイシュー / プルリクエストのコメントに投稿されます。

### トリガー
#### プルリクエスト作成
プルリクエストを作成すると、自動でClaude Codeによるレビューが行われます。

Claude Codeによるレビューの結果はプルリクエストのコメントに投稿されます。

#### `@claude`
イシュー本文とコメント・プルリクエストのコメントにて
`@claude` を使用すると、Claude Codeに指示ができます。

Claude Codeへ指示する`@claude`という文字列は `.github/workflows/claude-auto-review.yml` にて定義されています。ファイル内の記述を変更すれば、他の文字列に変更することも可能です。

## Gemini CLI

Gemini CLI によるレビューの結果はイシュー / プルリクエストのコメントに投稿されます。

### トリガー

#### `@gemini-cli`
