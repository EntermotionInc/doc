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
[merge]
	ff = false
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
### Forkするやり方
1. 案件にアサインされたら、GitHub上のマスターとなるリポジトリをForkボタンからForkする。
1. Forkされたリポジトリからローカル環境にgit cloneしてくる。
1. ローカル環境上で、開発すべき機能のブランチを作る。具体的には、機能追加や仕様変更は feature/XXX というブランチ名、不具合修正は bugfix/YYY というブランチ名で作業をしてください。
   - git checkout -b bugfix/issue-611 master
1. ローカル環境上で、修正→テスト→コミットという流れで開発する。
   - 修正・テスト
   - git add <修正したファイル...>
   - git commit -m "○○を修正。"
1. 開発完了したと判断できたら、2でForkしたGitHub上のリポジトリにpushする。
   - git push origin bugfix/issue-611
1. 2でForkしたリポジトリから1のリポジトリにpull requestを送る。
2. pull requestがmergeされたら完了。rejectされたらコメントのメールが来る。その場合は、
3. ローカル環境で修正→テスト→コミット
1. 開発完了したと判断できたら、2でForkしたGitHub上のリポジトリにpushする。
1. 7.のコメントへの返信として、修正した旨連絡する。
2. 7に進む

### GitHub Flow式（Forkしないやり方）
1. 案件にアサインされたら、GitHub上のマスターとなるリポジトリをローカル環境にcloneする。
2. ローカル環境上でトピックブランチを作る（例：dev-login_point）。
3. GitHub側のリモートリポジトリにも同名のブランチを作成する。
3. ローカル環境上で、修正->テスト->コミットという流れで開発する。
4. 適当にキリのよいところで定期的にリモートリポジトリにpushする。（pushするとGitHub側のリモートリポジトリのブランチも更新される。）
4. masterへpull requestしたければGitHub上で「Compare & pull request」をクリックする。
5. pr（pull request）がmergeされたら完了。rejectされたら4.に戻って修正するなり対応する。

* 作業例 https://github.com/EntermotionInc/doc/blob/master/worklog1.md
* テスト用リポジトリ https://github.com/EntermotionInc/github_flow_test

## ブランチについて

ブランチを用いた開発では、以下のようなブランチで作業を進めることになります。

- releaseブランチ: 本番デプロイ用。ログを表示しない、本番サーバに接続、本番モード等
- masterブランチ: 動作部分は製品版と同じ。ログを表示する、開発サーバに接続、開発モード等
- feature/hogehogeブランチ: masterブランチから作った特定の機能の作業用ブランチ
  ex. feature/point_list_sort_order
- bugfix/hogehogeブランチ: masterブランチから作った特定の機能のバグ修正用ブランチ
  ex. bugfix/issue-611
