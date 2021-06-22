# keibaAI

machine learningを用いた競馬予想勉強

スクレイピング部分やデータ加工処理についてはこちらを主に参考にさせていただきました。ありがとうございます。

zenn url
* https://zenn.dev/dijzpeb/books/848d4d8e47001193f3fb/viewer

## コードの概要

### `scraping.ipynb`

スクレイピング用のプログラムです。
NetKeibaのデータベースから過去レースデータ、馬成績、馬血統、オッズデータを取得しています。

スクレイピングに関しては時間がかかるため、2020年の各会場ごとのレースデータをpickleファイルとして保存しています。

そのため、お試しとして使う場合は、ファイルを実行しなくともpickleデータを使えば前へ進むことはできます。（Trainデータを変化させたい場合はパラメタを変えて使用してください)

### `Data/scraping.py`

上記スクレイピング用のpythonファイル
レースが行われるごとにデータをupdateする処理も追記

実行例
` python scrape_keibadata.py --year 2021 --place 05 `

### `keibaAI.ipynb`

### 前処理
スクレイピングしたデータの前処理と加工を行っています。
またクラスの中にscrapするメソッドも含まれていますが、上記スクレイピング用のipynbで取得したpickleファイルをそのまま使うこともできます。

### モデル作成
LightGBMとXGBMとTabNetによる学習
