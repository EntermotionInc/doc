```
[10-29 19:44:23 s_suzuki]
git clone git@github.com:EntermotionInc/github_flow_test.git
Cloning into 'github_flow_test'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (3/3), done.
Checking connectivity... done
[10-29 19:44:31 s_suzuki]
cd github_flow_test
[10-29 19:44:34 s_suzuki/github_flow_test]
git st
## master
[10-29 19:45:27 s_suzuki/github_flow_test]
git co -b dev-login_point
Switched to a new branch 'dev-login_point'
[10-29 19:45:31 s_suzuki/github_flow_test]
git st
## dev-login_point
[10-29 19:45:34 s_suzuki/github_flow_test]
vi login_point.php
[10-29 19:46:04 s_suzuki/github_flow_test]
git st
## dev-login_point
?? login_point.php
[10-29 19:46:07 s_suzuki/github_flow_test]
git add login_point.php
[10-29 19:46:09 s_suzuki/github_flow_test]
git ci -m"add login_point.php."
[dev-login_point d249da7] add login_point.php.
 1 file changed, 2 insertions(+)
 create mode 100644 login_point.php
[10-29 19:46:22 s_suzuki/github_flow_test]
git push -u origin dev-login_point
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 328 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To git@github.com:EntermotionInc/github_flow_test.git
   637c08d..d249da7  dev-login_point -> dev-login_point
Branch dev-login_point set up to track remote branch dev-login_point from origin.
[10-29 20:01:12 s_suzuki/github_flow_test]
vi login_point.php
[10-29 20:01:31 s_suzuki/github_flow_test]
git st
## dev-login_point
 M login_point.php
[10-29 20:01:34 s_suzuki/github_flow_test]
git di
diff --git a/login_point.php b/login_point.php
index cf4f292..d93e255 100644
--- a/login_point.php
+++ b/login_point.php
@@ -1,2 +1,2 @@
<?php
echo('"login point!'\n");
[10-29 20:01:35 s_suzuki/github_flow_test]
git ci -m"改行追加"
# On branch dev-login_point
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   login_point.php
#
no changes added to commit (use "git add" and/or "git commit -a")
[10-29 20:01:45 s_suzuki/github_flow_test]
git add login_point.php
[10-29 20:01:51 s_suzuki/github_flow_test]
git ci -m"改行追加"
[dev-login_point d74771f] 改行追加
 1 file changed, 1 insertion(+), 1 deletion(-)
[10-29 20:01:52 s_suzuki/github_flow_test]
git push -u origin dev-login_point
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 339 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To git@github.com:EntermotionInc/github_flow_test.git
   d249da7..d74771f  dev-login_point -> dev-login_point
Branch dev-login_point set up to track remote branch dev-login_point from origin.
[10-29 20:01:59 s_suzuki/github_flow_test]
```
