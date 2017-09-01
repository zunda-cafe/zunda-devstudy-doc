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
