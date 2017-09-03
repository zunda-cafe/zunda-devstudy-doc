# zunda-devstudy のためのドキュメント

## Sphinxをビルドするのための環境準備

このリポジトリのSphinxでは、ドキュメントに各種 UML 図を埋め込むための Sphinx 拡張「PlantUML」使用しています。
PlantUMLについては以下のサイトを参照してください。

* http://tweeeety.hateblo.jp/entry/2014/10/24/173359
* http://kuttsun.blogspot.jp/2016/10/sphinx-plantuml.html

本来であれば、下記URLにアクセスしてjarをダウンロードし適当なディレクトリに置くのですが、
既にplantuml配下にplantuml.jarを配置していますので、ダウンロード不要です。

http://sourceforge.net/projects/plantuml/files/plantuml.jar/download

また、conf.py に以下を追加しています。

    extensions += ['sphinxcontrib.plantuml']
    import os
    plantuml = 'java -jar ' + os.path.abspath('../plantuml/plantuml.jar')

さらに、シーケンス図以外の UML を使う場合には Graphvizが必要になります。
GraphvizのインストールはMac/Windows/Linuxで異なりますので詳細はインターネットで検索してみてください。

（Macでのインストール方法は http://tweeeety.hateblo.jp/entry/2014/10/24/173359 を参照）

## TravisCIでのビルド

masterブランチにpushされたタイミングをTravisCIが検知してビルドが走ります。TravisCIのURLは以下の通り。

* https://travis-ci.org/zunda-cafe/zunda-devstudy-doc

GitHubとTravisCIの連携については以下のサイトが参考になります。

* http://knowledge.sakura.ad.jp/tech/3754/

TravisCIにGitHubのアカウントでログインすると、所有しているGitHubリポジトリと連携することができます。TravisCIにどのような動作をさせるかはGitHubに登録した `.travis.yml` ファイルに記載します。本リポジトリでは以下の内容を記載しています。

    language: python
    addons:
        apt:
            packages:
                - graphviz
                - fonts-ipafont
    python:
      - "3.6"
    install: "pip install -q -r requirements.txt"
    script: sphinx-build -E -nW -b html -d build/doctrees source build/html
    before_deploy:
      - "touch build/html/.nojekyll"
    deploy:
      provider: pages
      skip_cleanup: true
      github_token: $GH_TOKEN
      local_dir: build/html
      on:
        branch: master

$GH_TOKEN は後述するGitHub Pages専用のgh-pagesブランチにTravisCIがpushするためのアクセストークンです。取得や設定方法は以下のサイトを参考にしてください。

* http://qiita.com/myyasuda/items/5186fcee00e68ed1bb32

## GitHub Pages での公開（デプロイ）

TravisCIがビルドしたhtmlフォルダをGitHubのgh-pagesブランチにpushすることで、以下のURLでビルド結果を公開しています。

* https://zunda-cafe.github.io/zunda-devstudy-doc/
