# Railsの実務で学んだことやテクニックについて書いていく

## まず実務に取り掛かるにあたっての心構え

### 1人で悩みすぎない

- 実務は基本的に期日があるので、悩みすぎてスケジュールが遅れるのが1番迷惑となります。

- 報告は細かくしていこう、また遅れているときは遅れている原因も一緒に報告できたら良さそう。

- エラーで煮詰まった時や実装が全くわからない時は、一旦休憩しょう！！

- 辛い時は溜め込まずに誰かに相談しよう！！

### 人に質問するときはわかりやすく簡潔に

- 先輩たちの時間を奪わないように分かりやすく！！

- ポイントとしては結論から話す事や太字・句読点・改行を使って文字が詰め詰めにならないように！！

- エラーの場合はエラーログを調べて調査してから質問をする

### 先方へのPRを作成するときは慎重に、レビューをもらう前にこれだけは確認しよう!!

- コミットメッセージは綺麗か

- そもそも仕様をもれなく満たしているか

- 変数名は適切か？・N＋1(バックエンドなら)等は起きていないか？

- ブランチ名に問題はないか

- PRを作成する先を間違ってはいないか

- unlessを多用してないか条件分岐をネストしていないか

### まずチケットに取り掛かる前に、下記の記事を読んでおくと良さそう

[【新人プログラマ応援】開発タスクをアサインされたらどういう手順で進めるべきか](https://qiita.com/jnchito/items/017487cd882091494298)


## 便利なメソッド等のまとめ(Ruby,Rails)

### モデル・DB（リレーション）周りはここら辺押さえておくと良さそう

- [scope](https://qiita.com/ngron/items/14a39ce62c9d30bf3ac3)

- [Railsで別名の外部キーを設定する方法](https://qiita.com/j-sunaga/items/ee1fb558807c04243f0f)

- [polymorphic](https://qiita.com/sibakenY/items/7d984267995e8ce408c2)

- [inverse_of](https://www.sejuku.net/blog/66868)

### SQLを扱うならここら辺押さえておくと良さそう

- N+1対策はここら辺を使えば問題ない（includes・preload・eager_load）

- [ActiveRecordのjoinsとpreloadとincludesとeager_loadの違い](https://qiita.com/k0kubun/items/80c5a5494f53bb88dc58)

- [joins](https://qiita.com/yuyasat/items/c2ad37b5a24a58ee3d30)

- この記事も良さそう[joinsメソッドの使い方 ~ テーブル結合からネストまで学ぶ](https://pikawaka.com/rails/joins)

- joinsの注意点(joinsメソッドの基本的な使い方は、joinsメソッドを実行したモデルのレコードを取得するもので関連付けしたデータは取得していない)

- joinsでリレーション先のテーブルのカラムを取得する方法
```
モデル名.joins(:アソシエーションの名前).select("アソシエーションの名前.取得したいカラム名")
カラム名がかぶる場合は、select内で名前付けをする。
ASで名前づけ
モデル名.joins(:アソシエーションの名前).select("アソシエーションの名前.取得したいカラム名 AS 任意の名前")
```

- [orderで関連テーブルのカラムで並び替え](https://zenn.dev/a_da_chi/articles/a2d08c17347289)

- [eachは空の配列でも[]でも対応可能だから、条件分岐等で場合分けは不要](https://teratail.com/questions/168508)

  (個人的にDBから取得したデータをView側表示する際に使う機会が多い気がしている)

- [where](https://www.sejuku.net/blog/13363)

 割とwhereはこんな書き方をするのが多いイメージ(User.where("name = ?", @name))

 whereを複数使うやり方(User.where(kind: 0).where(name: ‘yamada’))

- [論理削除したデータを扱う](https://www.task-notes.com/entry/20170813/1502618254)

- [関連テーブルの条件をON句に書きたい！](https://blog.logicoffee.tech/posts/programming/scoped-association.html)

- [present?とexists?のSQLでデータ取得する際のパフォーマンスの違い](https://mikamisan.hatenablog.com/entry/2017/09/26/223137)

- [SQLをRailsで扱う時の色々な便利なもの](https://qiita.com/yut_h1979/items/4cb3d9a3b3fc87ca0435)

- [find_by_sqlでRailsから生SQLクエリを直接実行する](https://qiita.com/natsuokawai/items/7bc330e9a6f6f4ef0359)

  (基本的にRailsに既存であるメソッドでSQLを組むことを推奨)


  (どうしても厳しい場合や複雑なSQLを組むときはプレースホルダー等を用いて動的に変更できるようなSQLを書いていく)

### その他の便利なメソッド

- pluck

- all?

- [map](https://qiita.com/s_tatsuki/items/869af9c0c33d9d650f3f)

- [Railsで変数の中身が空か確認する空チェックメソッド4種](https://materializer.co/lab/blog/27)

- to_sql→ActiveRecordのオブジェクトに対して使うことでSQLを見ることができる(主にデバックで確認するように使う)

- inspect→ActiveRecordのオブジェクトに対して使うことでオブジェクトの中身を確認できる(主にデバックで確認するように使う・めっちゃおすすめ)

- [配列の要素と何番目にあるかを一緒に取り出す_each_with_indexメソッド](https://satoru103.hatenablog.com/entry/2020/02/09/225503)

- [ぼっち演算子でNIlエラーを回避する](https://qiita.com/yoshi_4/items/e987b698c1978d248cfc)(割と使う)

### その他実務で見たもの

- [バッチの実行方法などで使う(rails-runner)](https://qiita.com/port-development/items/61c0f74c123955f45f8e)

- [rails-runnerに引数を持たせる方法](http://nomnel.net/blog/rails-runner-keyword-arg/)

- [CanCanCanで特定のユーザーがアクセスできるリソースを制限する](http://319ring.net/blog/archives/2179/)

- [decoratorの使い方](https://qiita.com/ykemoemo/items/b2c5c68f853a5cc91446)

  （例）Viewに関係するメソッドでかつModelに関係するメソッドの記述
  ユーザーの名前とかのフォーマットetc
- [Serializers](https://zenn.dev/emono/articles/8211ad5ec036e9)※重要JSONとしてデータを返す時によく使う

- [attr_accessor](https://qiita.com/Hassan/items/0e034a1d42b2335936e6)

  (Railsでのマイグレーションファイルを作成する際にも自動で使われているはず)
  User.name→この値を取得できるのもgetterメソッドのおかげ

- [I18nで日本語化まとめ](https://qiita.com/Kta-M/items/bd4ba36a58ad602a9d8b)

- [i18nで引数を渡して動的にする](https://takuyan.hatenablog.com/entry/20111120/1321741426)

- [ラッパークラスの概念](https://wa3.i-3-i.info/word191.html)

- [早期returnを使って無駄な処理をしない](https://zenn.dev/media_engine/articles/early_return)※記事はJSだけどRubyでもある

- [RubyのModuleの使い方](https://qiita.com/shiopon01/items/fd6803f792398c5219cd)※重要モジュールで名前空間やインスタンスの生成でinitializeとセットでよく使う

- [initialize](https://www.sejuku.net/blog/21170)個人的にはモジュールとセットで使う印象・また、インスタンスを作成する時に使う印象が強い

## プログラミングの考え方編

[中／大規模開発のためのRails設計パターン](https://qiita.com/ktsujichan/items/2899d337ecbd90474c46)

### ソースコードの書き方

- 変数名は既存と命名規則等合っているか

- 処理を書くときはどのファイルに書くかを気をつける

- 自分の書いたコードが影響範囲はないかを確認する

- 配列等は変数名は複数形を使う

- 同じようなソースコードを何個も書いていないか(重複してる内容はメソッド化する)

- 基本的に責務は1つに統一する

### ソースコードの読み方

- メソッドジャンプを使用して処理の流れを理解

- Rails.logger.debugを使って処理の流れとは格納されている値を確認していく

- あるページに対応するファイルを探すときは、日本語・特別な処理など、なるべく少なそうなものを全体検索かけるようにする


### エラーの対処方

- エラーが出たときはバックエンドORフロントエンドどちらでエラーが出ているかを確認する

- フロント側ならコンソールを確認・バックエンド側ならログを確認

- ログを確認してどこまで処理が通って、どこでコケているのか確認する

- APIを使ってフロントと繋いでいる場合はディベロッパーツールのネットワークタブも確認してAPIの返してる値や、エラー出ていないかチェックする

- Rails.logger.debugを使って格納されている値を確認していく
