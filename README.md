# keibaAI

machine learningを用いた競馬予想勉強

スクレイピング部分やデータ加工処理についてはこちらを主に参考にさせていただきました。ありがとうございます。

zenn url
* https://zenn.dev/dijzpeb/books/848d4d8e47001193f3fb/viewer

## コードの概要

`scraping.ipynb`

スクレイピング用のプログラムです。
NetKeibaのデータベースから過去レースデータ、馬成績、馬血統、オッズデータを取得しています。

スクレイピングに関しては時間がかかるため、2020年の各会場ごとのレースデータをpickleファイルとして保存しています。

そのため、お試しとして使う場合は、ファイルを実行しなくともpickleデータを使えば前へ進むことはできます。（Trainデータを変化させたい場合はパラメタを変えて使用してください)

`DataProcess.ipynb`

スクレイピングしたデータの前処理と加工を行っています。

| 過去レースデータ（訓練データ）|	加工内容	| 出馬表データ |
| ---- | ---- | ---- |
| Results.data |	|	ShutubaTable.data |
| ↓	| |	↓ |
|Results.preprocessing() | 前処理 | ShutubaTable.preprocessing() |
| ↓	| |	↓ |
|Results.data_p	| |	ShutubaTable.data_p |
| ↓	| |	↓ |
|Results.merge_horse_results() | 馬の過去成績データ追加 | ShutubaTable.merge_horse_results() |
| ↓	| |	↓ |
|Results.data_h	| |	ShutubaTable.data_h |
| ↓	| |	↓ |
|Results.merge_peds() |	血統データ追加	| ShutubaTable.merge_peds() |
| ↓	| |	↓ |
|Results.data_pe | | ShutubaTable.data_pe |
| ↓	| |	↓ |
|Results.process_categorical() | |	カテゴリ変数の処理	ShutubaTable.process_categorical() |
| ↓	| |	↓ |
| Results.data_c	| |	ShutubaTable.data_c |
