## git の使い方（社内向け）
### お勧め設定
以下のような .gitconfig ファイルをホームディレクトリに置く
```
[color]
	ui = auto
[user]
	name = Hogeta Fugao
	email = hoge@example.jp
[alias]
  co = checkout # checkout長い…
  st = status -sb # シンプルなstatus
  pr = pull --rebase # pull するときにmergeコミットを作らない
  fo = fetch origin
  ro = rebase origin # branchでfoしてroすればmasterにrebaseできる
  rc = rebase --continue
  wd = diff --word-diff # 単語単位のdiff
  gp = grep -n # grepに行番号を付ける
  lg = log --graph --pretty=oneline --decorate --date=short --abbrev-commit --branches
  # ログをtreeで表示(簡易tig) via http://webtech-walker.com/archive/2010/03/04034601.html
  ci = commit
  di = diff --color-words
  br = branch
```
  
### 基本的な操作コマンド

* git clone （=~ svn checkout）
* git st （= git status。=~ svn status）
* git add（ステージ領域へファイルを追加。=~ svn add だけど、add するのは新規ファイルだけじゃない。）
* git ci （= git commit。svn commit は git add と git ci を合わせたもの）
* git di （= git diff --color-words。=~ svn diff）
* git lg （= git log --graph --pretty=oneline ..(ry。=~ svn log）
* git pull （svn には相当するコマンドは無い。リモートリポジトリの変更をローカルリポジトリに取り込んでマージする）
* git push （svn には相当するコマンドは無い。ローカルリポジトリの変更をリモートリポジトリに取り込んでマージする）
* git br （= git branch。ブランチの一覧表示）
* git co -b hoge（= git checkout -b。hogeブランチを作って、hogeブランチに切り替える）
* git co master（= git checkout master。masterブランチに切り替える）
* git merge --no-ff hoge （hogeブランチから今いるブランチにマージする）

## github の使い方（社内向け）

## 開発フロー

1. 案件にアサインされたら、GitHub上のマスターとなるリポジトリをForkボタンからForkする。
1. Forkされたリポジトリからローカル環境にgit cloneしてくる。
1. ローカル環境上で、開発すべき機能のブランチを作る。
1. ローカル環境上で、修正→テスト→コミットという流れで開発する。
1. 開発完了したと判断できたら、2でForkしたGitHub上のリポジトリにpushする。
1. 2でForkしたリポジトリから1のリポジトリにpull requestを送る。
2. pull requestがmergeされたら完了。rejectされたらコメントのメールが来る。その場合は、
3. ローカル環境で修正→テスト→コミット
1. 開発完了したと判断できたら、2でForkしたGitHub上のリポジトリにpushする。
1. 7.のコメントへの返信として、修正した旨連絡する。
2. 7に進む
