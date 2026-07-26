# UTENA Software Project Template

このリポジトリは、UTENAで作成するソフトウェアプロジェクトの標準テンプレートです。

このテンプレートの目的は、会話履歴がなくても、人間・ChatGPT・Codexの誰が参加しても、ドキュメントだけで次のことが分かる状態にすることです。

- このプロジェクトは何を作るのか
- なぜ作るのか
- 現在どこまでできているのか
- 何が未完成・未確認なのか
- 次に何をすればいいのか
- どのルールで開発するのか

## 最重要ファイル

ルート直下の `PROJECT_STATE.md` を、プロジェクトの現在地を示す唯一の基準ファイルとして使用します。

人間・ChatGPT・Codexは、必ず以下を守ります。

1. 作業開始時に `PROJECT_STATE.md` を最初に読む
2. 実装・仕様・確認結果が変わったら同じ作業内で更新する
3. 最終報告の前に `PROJECT_STATE.md` を更新してコミットする
4. 会話履歴やPR本文だけに現在地を残さない
5. 未確認の内容を「完了」「動作確認済み」と書かない

`PROJECT_STATE.md` が存在しないプロジェクトは、開発開始前に必ず作成してください。

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
PROJECT_STATE.md          現在地・確認状況・未完成・次の作業（必須）
docs/
├── PROJECT_OVERVIEW.md   プロジェクト概要
├── CURRENT_STATUS.md     状態の詳細資料
├── ROADMAP.md            今後やること
├── DEVELOPMENT_RULES.md  開発ルール
├── KNOWN_ISSUES.md       既知の不具合・未確認事項
├── CHANGELOG.md          更新履歴
└── HANDOFF.md            引き継ぎメモ
```

`docs/CURRENT_STATUS.md` は詳細資料として残せますが、最新の現在地・未完成・次にやることは必ず `PROJECT_STATE.md` にも反映します。

## 最初にやること

新規プロジェクトをこのテンプレートから開始したら、最初に以下を書き換えてください。

1. `PROJECT_STATE.md`
2. この `README.md` に実プロジェクト名と概要を追加する
3. `docs/PROJECT_OVERVIEW.md`
4. `docs/CURRENT_STATUS.md`
5. `docs/ROADMAP.md`
6. `docs/DEVELOPMENT_RULES.md`

最低限、`PROJECT_STATE.md` の次の項目は空欄にしないでください。

- プロジェクト名
- 目的
- 現在の到達点
- 未完成
- 次にやること
- 完成条件

## ChatGPT / Codex への依頼例

```text
最初に PROJECT_STATE.md、README.md、docs/ 以下を読んでください。
PROJECT_STATE.md が存在しない場合は、実装前に作成してください。

目的:
〇〇を修正したい。

条件:
- 会話履歴に依存しない形で判断してください。
- 未確認のことを完了扱いしないでください。
- 修正後はソースコードとドキュメントを両方更新してください。
- 最終回答の前に PROJECT_STATE.md を現在の状態へ更新し、コミットしてください。
- PROJECT_STATE.md の「次にやること」が空のまま終了しないでください。
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
3. 作成後、最初に `PROJECT_STATE.md` をプロジェクト内容に合わせて更新する
4. READMEとdocsをプロジェクト内容に合わせて更新する
