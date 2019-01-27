# 「Kaggle API」を Python で実行してみた
## はじめに
「[kaggle その2 Advent Calendar 2018](https://qiita.com/advent-calendar/2018/kaggle-part2)」2 日目の記事です。

## 概要
Kaggle API を Python 上で実行します（<u><b>`kaggle` コマンドを実行するわけではありません</b></u>）。

## 実行環境 
- anaconda3-5.2.0
    - Python 3.6.5
         - kaggle 1.5.0

- Kaggle API Key
    - 説明は省きます
    - `kaggle` コマンドが実行できるような状態にしておいてください

## 準備
### 1. kaggle ライブラリをインポート
`kaggle`コマンドは Python で作られているので、Github を見ながらうまいことインポートします。
```python
from kaggle.api.kaggle_api_extended import KaggleApi
```
### 2. KaggleApi クラスのインスタンスを準備
`KaggleApi` クラスにいろいろな処理が書かれているので、こちらのインスタンスを準備して、`api`経由でいろいろな関数を実行して行きます。
```python
# KaggleApi のインスタンスを用意
api = KaggleApi()
```
### 3. 認証を通す
このままだと認証通っていないので、エラーになります。

そこで`api.authenticate()`を実行します。  
ローカルにある `~/.kaggle/kaggle.json`を読み込みに行って、なんやかんやしてくれます。

```python
# 認証を通す
api.authenticate()
```

## 試してみる
コンペのリストを表示させてみます。
```python
# $ kaggle competitions list
api.competitions_list_cli()
```
```
ref                                            deadline             category            reward  teamCount  userHasEntered
---------------------------------------------  -------------------  ---------------  ---------  ---------  --------------
digit-recognizer                               2030-01-01 00:00:00  Getting Started  Knowledge       2724           False
titanic                                        2030-01-01 00:00:00  Getting Started  Knowledge      10359            True
house-prices-advanced-regression-techniques    2030-01-01 00:00:00  Getting Started  Knowledge       4300           False
imagenet-object-localization-challenge         2029-12-31 07:00:00  Research         Knowledge         30           False
competitive-data-science-predict-future-sales  2019-12-31 23:59:00  Playground           Kudos       1823            True
histopathologic-cancer-detection               2019-03-31 23:59:00  Playground       Knowledge         80           False
quora-insincere-questions-classification       2019-02-05 23:59:00  Featured           $25,000       1315            True
pubg-finish-placement-prediction               2019-01-30 23:59:00  Playground            Swag        705           False
human-protein-atlas-image-classification       2019-01-10 23:59:00  Featured           $37,000       1174           False
traveling-santa-2018-prime-paths               2019-01-10 23:59:00  Featured           $25,000        547            True
two-sigma-financial-news                       2019-01-08 23:59:00  Featured          $100,000       1828            True
PLAsTiCC-2018                                  2018-12-17 23:59:00  Featured           $25,000        737            True
quickdraw-doodle-recognition                   2018-12-04 23:59:00  Featured           $25,000       1214           False
ga-customer-revenue-prediction                 2018-11-30 23:59:00  Featured           $45,000        813            True
dont-call-me-turkey                            2018-11-26 23:59:00  Playground            Swag        223           False
airbus-ship-detection                          2018-11-14 23:59:00  Featured           $60,000        884           False
inclusive-images-challenge                     2018-11-12 23:59:00  Research           $25,000        468           False
rsna-pneumonia-detection-challenge             2018-10-31 23:59:00  Featured           $30,000       1499           False
tgs-salt-identification-challenge              2018-10-19 23:59:00  Featured          $100,000       3234           False
new-york-city-taxi-fare-prediction             2018-09-25 23:59:00  Playground       Knowledge       1488           False
```
ソースをざっと確認しましたが、`kaggle`コマンドで実行できる関数は`*_cli()`という名前になっています。

これを使っても何の意味もないので、`kaggle`コマンドで直接実行できないものをいくつか使ってみました。


### 各コンペの情報を取得
`competitions_list`はコンペの情報を取ってこれます。
```python
competitions_list = api.competitions_list(category='featured')
for competition in competitions_list:
    print(competition)
```
```
vsb-power-line-fault-detection
humpback-whale-identification
elo-merchant-category-recommendation
ga-customer-revenue-prediction
quora-insincere-questions-classification
human-protein-atlas-image-classification
traveling-santa-2018-prime-paths
two-sigma-financial-news
PLAsTiCC-2018
quickdraw-doodle-recognition
airbus-ship-detection
rsna-pneumonia-detection-challenge
tgs-salt-identification-challenge
google-ai-open-images-object-detection-track
google-ai-open-images-visual-relationship-track
home-credit-default-risk
santander-value-prediction-challenge
trackml-particle-identification
youtube8m-2018
avito-demand-prediction
```
どんな情報が入っているか見てみます。
```python
for key in dir(competitions_list[0]):
    print('{}: {}'.format(key, getattr(competitions_list[0], key)))
```
```
# 一部省略
awardsPoints: True
category: Featured
deadline: 2019-03-21 23:59:00
description: Can you detect faults in above-ground electrical lines?
enabledDate: 2018-12-20 23:08:48
evaluationMetric: Matthews correlation coefficient
id: 10684
isKernelsSubmissionsOnly: False
kernelCount: 0
maxDailySubmissions: 2
maxTeamSize: 8
mergerDeadline: 2019-03-14 23:59:00
newEntrantDeadline: 2019-03-14 23:59:00
organizationName: Enet Centre, VSB - T.U. of Ostrava
organizationRef: Enet-Centre-VSB
ref: vsb-power-line-fault-detection
reward: $25,000
submissionsDisabled: False
tags: [tabular data, signal processing, binary classification]
teamCount: 60
title: VSB Power Line Fault Detection
url: https://www.kaggle.com/c/vsb-power-line-fault-detection
userHasEntered: False
userRank: None
```

`$ kaggle competitions list` では取ってこれない情報がけっこうあるのがわかります。

### Kernel の情報を取得
```python
kernels_list = api.kernels_list(competition='elo-merchant-category-recommendation')
for key in dir(kernels_list[0]):
    print('{}: {}'.format(key, getattr(kernels_list[0], key)))
```
```
# 一部省略
author: FabienDaniel
categoryIds: []
competitionDataSources: []
datasetDataSources: []
enableGpu: None
enableInternet: None
id: 0
isPrivate: None
kernelDataSources: []
kernelType: None
language: None
lastRunTime: 2018-12-13 17:08:06
ref: fabiendaniel/elo-world
slug: None
title: Elo world
totalVotes: 261
```

## メリット
### 1. `kaggle`コマンドでは見れない情報を取得できる 
上でいくつか試したように、`kaggle`コマンドでは見れない情報がたくさんあります。

簡単なツールを作りにはちょうどいいです。

### 2. 利用規約に違反しない

Kaggle は公式がスクレイピングを禁止しています。

>> “Crawls,” “scrapes,” or “spiders” any page, data, or portion of or relating to the Services or Content (through use of manual or automated means);

> A violation of any of the foregoing is grounds for termination of your right to use or access the Services. We reserve the right to remove any Content or User Submissions from the Services at any time, for any reason (including if someone alleges you contributed that Content in violation of these Terms), and without notice.

[Terms of Use](https://www.kaggle.com/terms)（2018/11/25）

禁止というよりは「やったらいつでも◯すから、気をつけてね」の方が正しいかもしれません。

スクレイピングで取ってこれる情報量には敵いませんが、ちょっとしたツールを作るにはちょうどいいです。

## 注意点
Kaggle API は API Limit が公開されていない上に不安定です。

加えて、Python プログラム上での使用は推奨された使い方ではありません。

使いすぎて垢バンされないように気をつけてください。

以下 GitHub に API Limit 関連の issue が上がっています。
[https://github.com/Kaggle/kaggle-api/issues/132:embed:cite]



## おわりに
だれかが便利なものを作ってくれると期待しています。

## 参考資料
- [Kaggle API](https://github.com/Kaggle/kaggle-api)
- [Kaggle 利用規約](https://www.kaggle.com/terms)

## Hints
- [Hatena Blog](https://doarakko.hatenablog.com/entry/kaggle_api_in_python)