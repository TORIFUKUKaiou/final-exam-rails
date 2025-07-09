# Ruby on Rails チュートリアルのサンプルアプリケーション

これは、次の教材で作られたサンプルアプリケーションです。
[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
（第7版）
[Michael Hartl](https://www.michaelhartl.com/) 著

## ライセンス

[Ruby on Rails チュートリアル](https://railstutorial.jp/)内にある
ソースコードはMITライセンスとBeerwareライセンスのもとで公開されています。
詳細は [LICENSE.md](LICENSE.md) をご覧ください。

## 使い方

このアプリケーションを動かす場合は、まずはリポジトリをフォークしてください。

フォークしたリポジトリで、「Code」から「Codespaces」タブに移動し、
「Create codespace on main」をクリックすると環境構築がスタートします。
Railsサーバーが立ち上がり、シンプルブラウザが表示されるまでしばらくお待ちください。

次に、データベースへのマイグレーションを実行します。

```
$ rails db:migrate
```

最後に、テストを実行してうまく動いているかどうか確認してください。

```
$ rails test
```

詳しくは、[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
を参考にしてください。

# 本リポジトリについて

このリポジトリは、YassLab 提供のリポジトリ [sample_apps](https://github.com/yasslab/sample_apps) 内の  
7_0/ch14 ディレクトリを教育目的で取り出し、環境構築の手間を省いてすぐに試せるよう再構成したものです。  

学生が [GitHub Codespaces](https://github.com/features/codespaces) で**最小の操作ですぐ動作確認ができるように**、プロジェクトのルートに配置してあります。  

※ 本コードは以下のコミット時点の内容をルートに再構成しています：  
https://github.com/yasslab/sample_apps/tree/4bf1267e0d2e6d461ec1ffd6029b41376e7a4dc0  

⚠️ このリポジトリはテンプレートとして使われることを想定しています。リポジトリ作成後は .github/workflows を削除してください。準備フェーズですので、mainブランチで直接作業する例を示します。  

1. rm -rf .github
1. git add .
1. git commit -m "Finalize ch14"
1. git push -u origin main

