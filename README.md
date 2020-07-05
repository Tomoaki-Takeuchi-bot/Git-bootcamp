# Git bootcamp について

- 個人で Git・GitHub・擬似チーム開発練習を行うために作成したレポジトリです。
- 初期 Set ファイル数 20,ブランチ 20, master ブランチのみ html ファイルに記載あり

![Uploading スクリーンショット 2020-07-05 23.43.56.png…]()

---

# **_Git Cheatsheet_**

---

## Git が関連する環境

- ローカル

1. リポジトリ
2. ステージ
3. ワークツリー <br>
   上記３種類がある

- リモート <br>
  GitHub

---

### ローカルリポジトリの作成

- `git init` .git ディレクトリが作成される

### Git リポジトリのクローンを作る（リモートから）

- `git clone <リポジトリ名>`

### 変更をステージに追加する

- `git add <ファイル名>` ファイル名を指定してステージに
- `git add <ディレクトリ名>` ディレクトリ名を指定してステージに
- `git add .` 全てのファイル、ディレクトリ
- `git add *.css` 全ての CSS ファイル（ワイルドカードで指定）

### 変更を記録する

- `git commit` コマンドの後にメッセージ入力
- `git commit -m "<メッセージ>"` メッセージも一緒にコミット可能
- `git commit -v` 変更点を表示してコミット

### 現在の変更状況を確認する

- `git status`

### 変更差分の確認

- `git diff` git add する前の変更分
- `git diff<ファイル名>` git add する前の変更分（ファイル名指定）
- `git diff --staged` git add した後の変更分（ステージとリポジトリの差分確認）

### 変更履歴を確認する（コミット）

- `git log`
- `git log --online` 一行で表示する
- `git log -p index.html` ファイルの変更差分を表示する
- `git log -n <コミット数>` 表示するコミット数を制限する

### ファイルの削除を記録する

- `git rm <ファイル名>` ファイル名を指定して削除
- `git rm -r <ディレクトリ名>` ディレクトリ名を指定して削除
- `git rm --cached<ファイル名>` ファイルを残して削除

### ファイルの移動を記録する

- `git mv <旧ファイル><新ファイル>` mv +git rm +git add と同じ動作をワンコマンドで

### リモートリポジトリを新規追加する

- `git remote add origin ***` origin という名前で GitHub リポジトリを追加する

### リモートリポジトリへ送信する

- `git push <リモート名><ブランチ名>` ローカルリポジトリの内容をリモートに送る（プッシュする）
- `git push origin master`

### コマンドにエイリアス（短縮入力コマンド）をつける

- `git config --global alias.ci commit` commit を ci で入力できるようにする
- `git config --global alias.st status` status を st で入力できるようにする
- `git config --global alias.br branch` branch を br で入力できるようにする
- `git config --global alias.co checkout` checkout を co で入力できるようにする
  \*\* global とつけると PC 全体設定となり便利

### Gitignore(Git 管理対象ファイルの設定)

ファイル設定

- `# で始まる行はコメント`
- `ファイルを管理対象から除外 index.html`
- `ディレクトリを管理対象から除外 /root.html`
- `ディレクトリ以下を管理対象から除外 dir/`
- `/以外の文字列にマッチしたものを管理対象から除外（ワイルドカード） /*/*.css`

### ファイルへの変更を取り消す（ステージ => ワークツリーへ）

- `git checkout -- <ファイル名>`
- `git checkout -- <ディレクトリ名>`
- `git checkout -- .` 全変更を取り消す
  --とコマンドするのはブランチ名とファイル名が被った際に Git 側で判別がつくように

### ステージ後の変更を取り消す

- `git reset HEAD <ファイル名>`
- `git reset HEAD <ディレクト名>`
- `git reset HEAD . <全変更を取り消す>`
  ステージからの取り消しなのでワークツリーには影響を及ぼさない

### 直前のコミットをやり直す

- `git commit --amend`
  リモートにプッシュしたものは取り消し NG

### リモートを表示する

- `git remote`
- `git remote -v` 対応する URL を表示する

### リモートリポジトリを新規追加する

- `git remote add <リモート名><リモートURL>`

### リモートからの情報取得（フェッチ）

- `git fetch<リモート名>`
  ローカルリポジトリに保存、ワークツリーへの反映（マージ）は行われない

### リモートからの情報取得（プル）

- `git pull<リモート名><ブランチ名>`
  ローカルリポジトリへの反映、ワークツリーへの反映を一度に行う

### リモートの詳細情報を表示する

- `git remote show <リモート名>`
  Fetch,Push の URL、リモートブランチ、git pull の動作、git push の動作を表示
  SSH 暗証番号を聞かれる

### リモートを変更・削除する

- `git remote rename<旧リモート名><新リモート名>` 変更の場合
- `git remote rm<リモート名>` 削除の場合

### ブランチの作成

- `git branch <ブランチ名>`

### ブランチの表示

- `git branch`
- `git branch -a` 全ブランチ表示

### ブランチの切替

- `git checkout <既存ブランチ名>`
- `git checkout -b <新ブランチ名>` ブランチを作成して切り替える

### 変更履歴をマージする

- `git merge <ブランチ名>`
- `git merge <リモート名/ブランチ名>`

### ブランチを変更・削除する

- `git branch -m <ブランチ名>` 変更する
- `git branch -d <ブランチ名>` 削除する
- `git branch -D <ブランチ名>` 強制削除する

### リベースで履歴を整えた形で変更を統合する

- `git rebase <ブランチ名>`

### プルのリベース取得

- `git pull --rebase <リモート名> <ブランチ名>`
  マージコミットが残らなくなる

### プルをリベース型に修正する

- `git config --global pull.rebase true`
- `git config branch.master.rebase true` マスターブランチで git pull する時のみ

### 複数のコミットをやり直す

- `git rebase -i <コミットID>`
- `git rebase -i HEAD~3`

- -i は interactive の略で対話方式による変更を求められる
- やり直したい commit を `edit` にする
- やり直したら実行 `git commit --amend`
- 次のコミットへ進む `git rebase --continue`リベース完了

### コミットの並び替え、削除

- `git rebase -i HEAD~3`

- 対象コミットを削除する
- 並び替えしたいコミットの順番修正

### コミットをまとめる

- `git rebase -i HEAD~3`

- コミットをまとめたい物以外に`squash`をつける

### コミットを分割

- `git rebase -i HEAD~3`

- 分割したいコミットを`edit`にする
- `git reset HEAD<*対象コミットを指定する ex1 ^ etc>`
- `git add ***`
- `git commit -m`
- `add` `commit` 上記コマンドを分割分繰り返し

### タグの一覧表示

- `git tag`
- `git tag -l "2020-07-01` パターン指定の場合

### タグを作成する

- `git tag -a [タグ名] -m "[メッセージ]"` 名前、コメント、注釈
- `git tag [タグ名]` 名前だけのシンプルタイプ

### タグデータ表示

- `git show [タグ名]`

### タグをリモートリポジトリにプッシュする

- `git push [リモート名] [タグ名]`
- `git push origin --tags` タグの一斉送信

### 作業の一時避難（スタッシュ）

- `git stash`

### 避難した作業を確認する

- `git stash list`

### 避難した作業を復元する

- `git stash apply` 最新の作業を復元する
- `git stash apply --index` ステージの状況も復元する
- `git stash apply [スタッシュ名]` 特定の作業を復元する

### 避難した作業を削除する

- `git stash drop` 最新の作業を削除する
- `git stash drop [スタッシュ名]` 特定の作業を削除する
- `git stash clear` 全作業を削除する
