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

* git clone （svn で言うと、svn checkout）
* git st （= git status。svn で言うと svn status）
* git co （= git checkout。svn で言うと svn update）
* git ci （= git commit。svn で言うと svn commit）
* git di （= git diff --color-words。svn で言うと svn diff）


## github の使い方（社内向け）
