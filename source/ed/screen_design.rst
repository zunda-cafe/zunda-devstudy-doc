===================
画面一覧
===================

.. list-table::
   :widths: 10, 40, 40, 20, 50, 70, 50
   :header-rows: 1

   * - No
     - ユースケースグループ名
     - ユースケース名
     - 画面ID
     - 画面名
     - 説明
     - 備考
   * - 1
     - ログイン
     - ログインする
     - A101
     - ログイン画面
     - ログインする画面
     -
   * - 2
     - 記事閲覧
     - 記事を閲覧する
     - B101
     - 記事一覧画面
     - 全ての記事のタイトルを表示する画面
     -
   * - 3
     - 記事閲覧、コメント投稿
     - 記事を閲覧する、コメントを投稿する
     - B102
     - 記事詳細画面
     - 特定の記事の本文やコメントを表示、コメントを投稿する画面
     -
   * - 4
     - 記事投稿
     - 記事を投稿する
     - C101
     - 記事投稿画面
     - 投稿する記事を入力する画面
     -
   * - 5
     - 記事投稿
     - 記事を投稿する
     - C102
     - 記事投稿確認画面
     - 投稿する記事を確認する画面
     -
   * - 6
     - 記事修正
     - 記事を修正する
     - D101
     - 記事修正画面
     - 既存の記事を修正する画面
     -
   * - 7
     - 記事修正
     - 記事を修正する
     - D102
     - 記事修正確認画面
     - 記事の修正を確認する画面
     -
   * - 8
     - 記事削除
     - 記事を削除する
     - E101
     - 記事削除確認画面
     - 既存の記事を削除する画面
     -

===================
画面遷移図
===================

.. uml::

  left to right direction
  skinparam defaultFontName IPAGothic

  A101 : ログイン画面
  B101 : 記事一覧画面
  B102 : 記事詳細画面
  C101 : 記事投稿画面
  C102 : 記事投稿確認画面
  D101 : 記事修正画面
  D102 : 記事修正確認画面
  E101 : 記事削除確認画面

  [*] --> A101
  A101 --> B101 : ログイン
  B101 --> B102 : 記事タイトル
  B101 --> C101 : 記事を投稿する
  C101 --> C102 : 投稿
  C102 --> B101 : 確定
  B102 --> D101 : 修正
  D101 --> D102 : 修正
  D102 --> B102 : 確定
  B102 --> E101 : 削除
  E101 --> B101 : 削除
  B102 --> B102 : コメント投稿
  B102 --> B101 : 一覧へ戻る
  C101 --> B101 : 戻る
  C102 --> C101 : 戻る
  D101 --> B102 : 戻る
  D102 --> D101 : 戻る
  E101 --> B102 : 戻る
  B101 --> B101 : ログアウト

===================
画面仕様
===================

ログイン画面
===================

:画面ID: A101
:画面名: ログイン画面

.. uml::

  skinparam defaultFontName IPAGothic

  @startuml
  salt
  {+
    |　|Zunda-Cafe Blog   |*|*|.
    |　| --- |*|*|.
    |　|ユーザID|"foo@bar.ne.jp         "|.| (1)
    |　|パスワード|"***********         "|.| (2)
    |　| --- |*|*|.
    |　|{[ログイン]|[リセット]}|*|*| (3)(4)
  }
  @enduml

.. csv-table::
  :file: screen_item_A101.csv
  :encoding: utf-8
  :header-rows: 1
  :stub-columns: 1
  :widths: 5,20,20,5,5,5,5,5,40

記事一覧画面
===================

:画面ID: B101
:画面名: 記事一覧画面

.. uml::

  skinparam defaultFontName IPAGothic

  @startuml
  salt
  {+
    |　|Zunda-Cafe Blog   |*|*|.
    |　|[記事を投稿する]|*|*| (1)
    |　| --- |*|*|.
    |　|記事タイトル|*|.| (2)
    |　|記事タイトル|*|.| (2)
    |　|記事タイトル|*|.| (2)
    |　|記事タイトル|*|.| (2)
    |　|記事タイトル|*|.| (2)
    |　| --- |*|*|.
    |　|[ログアウト]|*|*| (3)
  }
  @enduml

.. csv-table::
  :file: screen_item_B101.csv
  :encoding: utf-8
  :header-rows: 1
  :stub-columns: 1
  :widths: 5,20,20,5,5,5,5,5,40

全ての記事の記事タイトルを表示する。

記事詳細画面
===================

:画面ID: B102
:画面名: 記事詳細画面

.. uml::

  skinparam defaultFontName IPAGothic

  @startuml
  salt
  {+
    |　|Zunda-Cafe Blog   |*|*|.
    |　| --- |*|*|.
    |　|タイトル|最近の天気について           |.| (1)
    |　|本文|昨日も雨、今日も雨…             |.| (2)
    |　| --- |*|*|.
    |　|コメントです|*|*| (3)
    |　|コメントです|*|*| (3)
    |　|"新しいコメントを入力します         "|*|*| (4)
    |　| --- |*|*|.
    |　|{[コメント投稿]|[修正]|[削除]|[一覧に戻る]}|*|*| (5)(6)(7)(8)
  }
  @enduml

.. csv-table::
  :file: screen_item_B102.csv
  :encoding: utf-8
  :header-rows: 1
  :stub-columns: 1
  :widths: 5,20,20,5,5,5,5,5,40

「修正」「削除」ボタンはログインユーザが投稿した記事の場合のみ表示する。

記事投稿画面
===================

:画面ID: C101
:画面名: 記事投稿画面

.. uml::

  skinparam defaultFontName IPAGothic

  @startuml
  salt
  {+
    |　|Zunda-Cafe Blog   |*|*|.
    |　| --- |*|*|.
    |　|タイトル|"最近の天気について           "|.| (1)
    |　|本文|"昨日も雨、今日も雨…             "|.| (2)
    |　| --- |*|*|.
    |　|{[投稿]|[戻る]}|*|*| (3)(4)
  }
  @enduml

.. csv-table::
  :file: screen_item_C101.csv
  :encoding: utf-8
  :header-rows: 1
  :stub-columns: 1
  :widths: 5,20,20,5,5,5,5,5,40

記事修正画面
===================

:画面ID: D101
:画面名: 記事修正画面

.. uml::

  skinparam defaultFontName IPAGothic

  @startuml
  salt
  {+
    |　|Zunda-Cafe Blog   |*|*|.
    |　| --- |*|*|.
    |　|タイトル|"最近の天気について           "|.| (1)
    |　|本文|"昨日も雨、今日も雨…             "|.| (2)
    |　| --- |*|*|.
    |　|{[修正]|[戻る]}|*|*| (3)(4)
  }
  @enduml

.. csv-table::
  :file: screen_item_D101.csv
  :encoding: utf-8
  :header-rows: 1
  :stub-columns: 1
  :widths: 5,20,20,5,5,5,5,5,40

記事修正確認画面
===================

:画面ID: D102
:画面名: 記事修正確認画面

.. uml::

  skinparam defaultFontName IPAGothic

  @startuml
  salt
  {+
    |　|Zunda-Cafe Blog   |*|*|.
    |　| --- |*|*|.
    |　|タイトル|最近の天気について           |.| (1)
    |　|本文|昨日も雨、今日も雨…             |.| (2)
    |　| --- |*|*|.
    |　|{[確定]|[戻る]}|*|*| (3)(4)
  }
  @enduml

.. csv-table::
  :file: screen_item_D102.csv
  :encoding: utf-8
  :header-rows: 1
  :stub-columns: 1
  :widths: 5,20,20,5,5,5,5,5,40

記事削除確認画面
===================

:画面ID: E101
:画面名: 記事削除確認画面

.. uml::

  skinparam defaultFontName IPAGothic

  @startuml
  salt
  {+
    |　|Zunda-Cafe Blog   |*|*|.
    |　| --- |*|*|.
    |　|タイトル|最近の天気について           |.| (1)
    |　|本文|昨日も雨、今日も雨…             |.| (2)
    |　| --- |*|*|.
    |　|{[削除]|[戻る]}|*|*| (3)(4)
  }
  @enduml

.. csv-table::
  :file: screen_item_E101.csv
  :encoding: utf-8
  :header-rows: 1
  :stub-columns: 1
  :widths: 5,20,20,5,5,5,5,5,40
