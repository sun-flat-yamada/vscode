# How to setup development environment - 開発環境の構築方法

## Gitを使いやすくするおススメ設定

Gitのログインアカウントを記憶させたり、Diffを見るときにGUIのWinMergeが自動的に立ち上がるようにしたい、といったことが出来ます。
使い始めたら以下を設定しましょう。

[参考サイト](https://blog.katsubemakito.net/git/git-config-1st)

```
# 名前とメールアドレス(アカウント)
git config --global user.name '<your name>'
git config --global user.email '<your mail address>'

# 改行コードを自動変換しない
git config --global core.autocrlf false

# 日本語ファイル名をエンコードさせず化けないようにする
git config --global core.quotepath false

# 表示をグラフィカルにする
git config --global color.ui true

# pushする時には今作業しているリモートを暗黙に指定する
# これはGitの仕組み、操作に慣れていない人は設定しない方が良いです。
# 間違って別のbranchにpushしてしまうことがあるので。
git config --global push.default current
```

## Gitが設定を保持する仕組みの説明

Gitは以下の階層で設定を保持できます。

|     | Scope   | Description               | Location
|:--- |:---     |:---                       |:---
|1    | system  | そのPC全体の設定         | (GitのInstall方法による)
|2    | global  | そのユーザー全体の設定   | %USERPROFILE%\.gitconfig
|3    | local   | 対象リポジトリのみの設定 | 対象リポジトリの.git/config

下に行くほど強く、上のものを上書きします。

現在設定されているgit configの一覧は以下のコマンドで確認できます。

```
# 全リスト出力
git config -l

# 対象Scopeのリスト出力
git config --global -l
```

## その他のTips

### clangがない、的なエラーが出る。

以下から自分のPC環境に合ったバイナリをInstallして、clang-formatにpathを通せば解決します。

https://releases.llvm.org/download.html
