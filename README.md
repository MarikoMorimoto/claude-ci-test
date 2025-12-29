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

Googleの認証にはGemini API Key、GitHubの認証には[推奨](https://github.com/google-github-actions/run-gemini-cli?tab=readme-ov-file#github-authentication)されているCustom GitHub Appを使用しています。

### トリガー

#### `@gemini-cli`

イシュー本文とコメント・プルリクエストのコメントにて `@gemini-cli` を使用すると、Gemini CLIにレビュー依頼ができます。

内部的に、`@gemini-cli` は `@gemini-cli /review`と変換されるようにカスタマイズしています。

レビュー出力の詳細はドキュメントを参照してください。: https://github.com/google-github-actions/run-gemini-cli/tree/v0.1.18/examples/workflows/pr-review#review-output-format

## セキュリティと権限制御

このリポジトリの GitHub Actions（Claude / Gemini）は、外部ユーザーによる任意コード実行やリポジトリ改変を防ぐために、以下の制約を設けています。

- Claude Code / Gemini CLI ともに、リポジトリの内部ユーザーのみを対象に動作します
  - `OWNER` / `MEMBER` / `COLLABORATOR` のいずれかに該当するユーザーのみ、ワークフローが実行されます
- fork 由来のプルリクエストでは自動レビューが実行されません

そのため、外部コントリビュータや fork リポジトリから、このリポジトリ上で Claude / Gemini による処理を直接走らせることはできません。
