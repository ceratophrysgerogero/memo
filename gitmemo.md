#gitよく使うもの

git branch -a
git checkout master
git checkout -b 作成するブランチ名
git push -u origin 作成したブランチ名
git diff HEAD(前回コミットからの差分)
git status
git config --global user.name "メインアカウント"(~/.gitconfig)
git config --local user.name "サブアカウント"(./.git/config)
git add -u(バージョン管理されたファイルの変更点)
git add -A(変更あったファイル全て)
git push origin :ブランチ名
git checkout .
git clean -df .
git reset HEAD .
git reset --hard HEAD^
git push origin +ブランチ名
git commit -m ‘最初のコミット’

前とコミットしたアカウントと違うと怒られた場合(sshだとだめくさい)
git remote set-url origin https://使用したいアカウントの名前@github.com/使用したいアカウントの名前/プロジェクトの名前.git
