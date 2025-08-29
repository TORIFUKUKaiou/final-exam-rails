# Ruby on Rails チュートリアルのサンプルアプリケーション

これは、次の教材で作られたサンプルアプリケーションです。
[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
（第7版）
[Michael Hartl](https://www.michaelhartl.com/) 著

期末試験の問題にする意図で、故意に動かなくしている箇所があります。  

## ライセンス

[Ruby on Rails チュートリアル](https://railstutorial.jp/)内にある
ソースコードはMITライセンスとBeerwareライセンスのもとで公開されています。
詳細は [LICENSE.md](LICENSE.md) をご覧ください。

## 使い方

このアプリケーションを動かす場合は、GitHubにログインし、[Use this template] > [Open in a codespace]で起動してください。  

Railsサーバーが立ち上がり、シンプルブラウザが表示されるまでしばらくお待ちください。  
データベースのマイグレーションをしていないため、エラー画面が表示されますが、ご安心ください。  
次のコマンドで、データベースのマイグレーションをすれば解決します。  

```
$ rails db:migrate
```

詳しくは、[*Ruby on Rails チュートリアル*](https://railstutorial.jp/)
を参考にしてください。

# 本リポジトリについて

このリポジトリは、YassLab 提供のリポジトリ [sample_apps](https://github.com/yasslab/sample_apps) 内の  
7_0/ch14 ディレクトリを教育目的で取り出し、環境構築の手間を省いてすぐに試せるよう再構成したものです。また、期末試験の問題にする意図で、故意に動作しないようにしている箇所があります。  

学生が [GitHub Codespaces](https://github.com/features/codespaces) で**最小の操作ですぐ動作確認ができるように**、プロジェクトのルートに配置してあります。  

※ 本コードは以下のコミット時点の内容をルートに再構成しています：  
https://github.com/yasslab/sample_apps/tree/de6a39f447aa0460b0561a5e23eb87ba2ceb8ee6  
