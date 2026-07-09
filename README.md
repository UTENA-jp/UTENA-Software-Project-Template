# UTENA Software Project Template

このリポジトリは、UTENAで作成するソフトウェアプロジェクトの標準テンプレートです。

このテンプレートの目的は、会話履歴がなくても、人間・ChatGPT・Codexの誰が参加しても、ドキュメントだけで次のことが分かる状態にすることです。

- このプロジェクトは何を作るのか
- なぜ作るのか
- 現在どこまでできているのか
- 何が未完成・未確認なのか
- 次に何をすればいいのか
- どのルールで開発するのか

## UTENA標準ルール

このプロジェクトでは、以下を必ず守ります。

- 会話履歴に依存した書き方をしない
- 初めて読む人でも理解できるように書く
- 現在の状態を必ず書く
- 次にやることを必ず書く
- 未確認のことを「完了」と書かない
- 仕様変更・実装変更をしたら、ソースコードとドキュメントを同時に更新する
- ChatGPTやCodexへ渡す前提で、ドキュメント単体で意味が通じるように書く

## ドキュメント構成

```text
docs/
├── PROJECT_OVERVIEW.md   プロジェクト概要
├── CURRENT_STATUS.md     現在の状態
├── ROADMAP.md            今後やること
├── DEVELOPMENT_RULES.md  開発ルール
├── KNOWN_ISSUES.md       既知の不具合・未確認事項
├── CHANGELOG.md          更新履歴
└── HANDOFF.md            引き継ぎメモ
```

## 最初にやること

新規プロジェクトをこのテンプレートから開始したら、最初に以下を書き換えてください。

1. この `README.md` に実プロジェクト名と概要を追加する
2. `docs/PROJECT_OVERVIEW.md`
3. `docs/CURRENT_STATUS.md`
4. `docs/ROADMAP.md`
5. `docs/DEVELOPMENT_RULES.md`

最低限、次の3つは空欄にしないでください。

- プロジェクトの目的
- 現在の状態
- 次にやること

## ChatGPT / Codex への依頼例

```text
README.md と docs/ 以下のドキュメントを読んでから作業してください。

目的:
〇〇を修正したい。

条件:
- 会話履歴に依存しない形で判断してください。
- 未確認のことを完了扱いしないでください。
- 修正後はソースコードとドキュメントを両方更新してください。
- 最後に現在の状態と次にやることを docs に反映してください。
```

## GitHub Template Repositoryとして使う方法

このリポジトリをGitHubでTemplate Repositoryに設定すると、新しいプロジェクトを同じドキュメント構成から開始できます。

GitHub上での設定:

1. Repository の `Settings` を開く
2. `General` を開く
3. `Template repository` にチェックを入れる

新規プロジェクト作成時:

1. GitHub上で `Use this template` を押す
2. 新しいリポジトリ名を入力する
3. 作成後、READMEとdocsをプロジェクト内容に合わせて更新する
