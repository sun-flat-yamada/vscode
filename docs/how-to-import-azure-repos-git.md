# How to Import Azure repos Git - Azure Repos Git に違う Azure Repos Git から引っ越す方法

Azure Repos (Git) は、他のリポジトリからImportする機能がある。
しかし、別のAzure ReposからのImportは出来ない様だ。

Clone URLがSSHアドレスでも通常のURLでもIncorrect URLとなってImportできなかった。
(GitHubなど別サービスからのImport機能の様だ)

このため、マニュアルで実施する手順でImportした。

[Azureの説明サイト](https://docs.microsoft.com/en-us/azure/devops/repos/git/import-git-repository?view=azure-devops#manually-import-a-repo)

```ps
# 引っ越し用の作業ディレクトリを作って移動
cd workingspace
mkdir move-to-main-repos
cd move-to-main-repos

# 対象リポジトリをClone
# この時管理用情報が目的なので--bareで管理情報だけ引っ張る
git clone --bare https://<organization>@dev.azure.com/<path to repos>

# そうすると以下の様に.gitと付いたbareリポジトリが取得できる
ls
    ディレクトリ: D:\repos\azure\move-to-main-repos
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----       2020/08/13      9:58                <project name>.git

# 引っ越し先のURLを引っ越し先プロジェクトのAzure Reposで確認
# [Azure DevOps] -> [Azure Repos] -> [Clone URL]
# 今回の場合は以下。どうやらSSHアドレスでなく通常のHTTPのURLの模様。
# https://dev.azure.com/<path to repos>
# つまり、以下ではない。
# https://<organization>@dev.azure.com/<path to repos>

# 取得したBareリポジトリのディレクトリに入ってから、以下のコマンドでリモートリポジトリに強制Pushして全上書きする。
# このコマンドはリモートリポジトリ (つまりサーバー側の神様) を問答無用で上書きします。
# 同名ブランチは上書きされ、存在しないブランチは削除されます。
# 宛先を充分確認して実行すること。
cd .\<project name>.git
git push --mirror https://dev.azure.com/<path to repos>

# Git LFS (Large File Storage) で管理しているものがある場合は追加手順あり。
# リンク先を参照のこと。
# https://docs.microsoft.com/en-us/azure/devops/repos/git/import-git-repository?view=azure-devops#manually-import-a-repo
```
