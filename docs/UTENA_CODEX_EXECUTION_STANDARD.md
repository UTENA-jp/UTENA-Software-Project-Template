# UTENA Codex Execution Standard

この文書はUTENAの全アプリ／全ソフトウェア開発に適用する共通標準である。OMOIDAS、UTENA-Estimate、NumberCompass、LUTENA、UTENA-Copy、Switcher-DIT-Control、UTENA AI Development Manager、および今後作成する全プロジェクトに適用する。

## 1. 同一指示の連続二重実行を禁止

VS Code / Codex IDE側で、ユーザーが1回しか送っていない同一指示が、完了後にもう一度配送・キュー投入される事象を前提に防御する。

### 判定

直前に完了したユーザー指示と、次に受信した指示が以下をすべて満たす場合、2件目は「新しいユーザー意図」ではなく重複配送とみなす。

- 本文が完全一致、または空白・改行・UI付加情報を正規化後に完全一致
- 直前の指示が完了・停止・ユーザー確認待ちのいずれか
- ユーザーから「再実行」「もう一度」「やり直して」等の明示指示がない
- 2件の間に新しい仕様・条件・データ・画像・ファイル・回答がない

### 2回目の動作

重複配送と判定した場合は次を厳守する。

- コード変更 0件
- ファイル作成／削除／移動 0件
- Git commit 0件
- push 0件
- build 0回
- test 0回
- device install / uninstall 0回
- restore / sync / migration / backup apply 0回
- 外部API write 0回
- destructive/state-changing operation 0回

返答のみ行い、内容は「同一指示は直前に完了済みのため、重複実行していません。再実行が必要なら明示してください。」とする。

## 2. Instruction Receipt

各ユーザー指示の開始時に以下を記録する。

- instruction_id: project + UTC/JST timestamp + sequence
- canonical prompt hash: SHA-256
- received_at
- repository
- branch/worktree
- starting Git SHA

完了時に以下を追記する。

- finished_at
- result: PASS / FAIL / BLOCKED / USER_CONFIRMATION_REQUIRED
- changed files
- commits
- tests actually executed
- device operations
- data-changing operations

Receiptはプロジェクトの非機密な作業ログ領域へ保存する。パスワード、token、秘密鍵、個人データ本文は記録しない。

## 3. Prompt canonicalization

重複判定用に、prompt本文を以下の範囲だけ正規化する。

- CRLF/LF統一
- 行末空白除去
- 連続する空行の差を無視
- IDEが自動付加した送信時刻・表示用prefix等を除外

ユーザーが変更した数字、条件、対象、ファイル名、画像、URL、IDは絶対に無視しない。1文字でも実質的仕様差があれば新規指示として扱う。

## 4. 再実行を許す条件

以下のいずれかがある場合のみ、同一内容でも再実行可能。

- ユーザーが明示的に「再実行」「もう一度」「やり直して」と指示
- 前回FAIL/BLOCKEDの原因が解消され、ユーザーが再開を指示
- 入力データ／device state／branch／Git SHAが変わり、それをユーザーが再実行対象として明示

Codex自身の判断で同一指示を再実行してはいけない。

## 5. State-changing操作の二重適用防止

特に以下は同一instruction_idまたは同一canonical prompt hashで二度適用してはいけない。

- database restore
- sync apply
- migration
- delete
- file move/rename
- attachment import
- billing/paid operation
- bundle uninstall
- production device install
- conflict resolution
- backup overwrite
- external publication/send

処理自体がidempotentでも、重複実行は禁止する。

## 6. Quality / Speed / No Regression

重複実行防止の目的は安全だけではない。UTENA開発では以下を同時に満たす。

- 品質を落とさない
- 無駄なbuild/testを減らす
- Codex quota/時間を浪費しない
- タカシ確認までの時間を短縮する
- NEW PASS / OLD FAIL を許さない

既にPASS済みで対象コードに変更がないfull test suiteを、同一指示の重複配送だけを理由に再実行してはいけない。

## 7. 完了判定

Codexが完了できるのは技術的な「完了候補」まで。

ユーザー受入が必要な工程は、タカシ本人の確認前に「完成」「完了」と宣言しない。

## 8. 全UTENAプロジェクト共通

この標準は特定アプリ専用ではない。新規repositoryを作る際は、この文書をプロジェクトテンプレートから必ず引き継ぐ。

標準原則：

> 同じ文章の指示が完了直後にもう一度届いても、ユーザーが明示的に再実行を求めていない限り、二度目は実行しない。
