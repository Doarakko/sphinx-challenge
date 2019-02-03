# Apache Arrow東京ミートアップ2018
## Apache SparkとApache Arrow
### Reasearch
- PySpark
- Python UDF
- Pandas UDF

## RとApache Arrow
### Learn
- 他のソフトウェアとデータをやりとりをすることが一番のメリット
- R とデータベースの接続方法
    - RJDBC パッケージ + JDBC
    - odbc パッケージ + JDBC
        - R のデータに変換する必要ある  
            → ここで Apache Arrow 使いたい
- DB からデータとってくるときは SQL
    - R で全部とってくると死ぬ
### Research
- dplyr
- ALTREP

## PythonとApache Arrow
### Learn
- Dask
    - pandas の処理を並列, 分散実行
- データ処理に置ける課題
    - numpy は padans で使用されていることを想定されていないため, 一部微妙なところあり
- Numpy
    - 欠損値がない
- padnas
    - 欠損値を扱う際に, numpy の型変換の制約を受ける
- scikit-learn
    - numpy のみ対応
    - pandas を渡した場合は, 裏で numpy に変換
### Research
- dask

## TensorとApache Arrow
###
- システム間でのテンソルの交換
    - apache arrow
- テンソルの操作

### Research
- xnd

## Reference
- [Apache Arrow東京ミートアップ2018](https://speee.connpass.com/event/103514/)
- [Apache Arrowの最新情報（2018年9月版）](https://www.clear-code.com/blog/2018/9/5.html)
