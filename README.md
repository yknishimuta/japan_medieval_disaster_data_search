## **概要**

このスクリプトは、藤木久志 編『日本中世気象災害史年表稿』（高志書院）に関して提供されているデータセットcsvファイルから特定の条件に一致するデータを抽出し、別のCSVファイルに保存するスクリプトです。

データセットは以下から入手可能です。

https://lab.hi.u-tokyo.ac.jp/datasets/saigai

「天変地異などの記事」 の条件検索の他に 「原出典」 での部分一致検索、グレゴリオ暦の範囲指定による検索を可能にしました。
[公式のビューア](https://www.hi.u-tokyo.ac.jp/collection/digitalgallery/disaster_events/)の検索機能を拡張したスクリプトです。

## **使い方**

```
python search_disaster_events.py [検索ワード] [オプション]
```

**例:**  

グレゴリオ暦が900年から1200年の間で、「雨」というキーワードを含むデータを抽出する場合:

```
python search_disaster_events.py 雨 -min 900 -max 1200
```

「雨」か「雷」が含まれるデータを抽出する場合

```
python search_disaster_events.py 雨 雷 
```

「雨」と「雷」を含むデータを抽出する場合

```
python --and-search search_disaster_events.py 雨 雷
```
原出典に「日本」が含まれるデータを抽出する場合
```
python search_disaster_events.py -s 日本
```

原出典が「扶桑略記23」であるデータを抽出する場合
```
python search_disaster_events.py -s 扶桑略記23 --strict-s
```

## **オプション一覧**

| オプション     | 説明                           |
| -------------- | ------------------------------ |
| `-s [出典名]` | 「原出典」で部分一致検索を行う |
| `--strict-s` | -sで指定した「原出典」で完全一致検索を行う |
| `-b [掲載書誌名]` | 「掲載書誌」で部分一致検索を行う |
| `--strict-b` | -bで指定した「掲載書誌」で完全一致検索を行う |
| `-min [年], --min-year [年]` | グレゴリオ暦の下限を指定      |
| `-max [年], --max-year [年]` | グレゴリオ暦の上限を指定      |
| `--and-search` | キーワードのAND検索を有効にする    |

## **検索ワードについて**

- 検索ワードを指定した場合、「天変地異などの記事」に部分一致するデータが抽出されます。
- 検索ワードはスペース区切りで複数個指定可能で、OR検索になります。
- 検索ワードを省略した場合は、すべてのデータが対象となります。

## **出力**

検索結果は `./outputs/data_from_source.csv` に保存されます。

## **動作環境**

- Python 3
- 必要なライブラリ: `pandas`

## **ライセンス**

このスクリプトはMITライセンスのもとで提供されます。