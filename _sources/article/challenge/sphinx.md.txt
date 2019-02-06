# ドキュメント作成によく使われているカッコいいテーマを使って Github Pages を作ってみた

## はじめに
LightGBM や Oputuna など

## ブランチ構成
- master: build されたコンテンツを管理
- source: `source` 下のファイルを管理
    - ユーザページとして作成したため, `master branch` にコンテンツを置く必要がある

source 下を GitHub で管理しない場合は特に気にする必要はないです

## 必要なもの
- GitHub アカウント
- Git
- Python 3
- pip

## 手順
- 
```
```
### CSS 適用
- `build/html` 下に `.nojekyll`（中身は空）を作成
    - jekyll が使用されないようにする
- GitHub Pages では [jekyll](https://jekyllrb.com/) が使用されているため `_<hoge>` が無視されてしまう

## Plus Ultra
- 僕のフォルダ構成
```
source
├── _static
│   ├── css
│   └── img
├── _templates
├── article
│   ├── challenge
│   ├── coursera
│   ├── index.md
│   ├── kaggle
│   └── scraping
├── conf.py
├── event
│   ├── apache-arrow-tokyo-meetup-2018.md
│   ├── index.md
│   ├── julia-tokyo-8.md
│   └── pre-event-baseball-data-hackathon.md
├── html
│   └── products
├── index.md
└── note
    ├── command.md
    ├── git.md
    ├── pandas.md
    └── sphinx.md
```
- HTML ファイルの配置方法
- 既存 CSS 編集
- Jupyter Notebook 対応

## 感想
もろもろまとめての感想です.
### Good
何かイケてることやってる感がでる

あとは、記事にはしないくらいのメモ書きを管理するのにちょうどいいです.

イベントに参加したり, すでに記事が何個も作られているようなコマンドの使い方などのメモ書きとかを置いてます.



`note` や `event` のところです.

### Bad
特に便利というわけではない.

## 課題
### `conf.py` の `html_theme_options` が効かない
調査中です、助けてください.
### `Makefile` 修正
- `make clean html` 実行時に, `master` ブランチの `.git` や `.gitignore` が削除されないようにする

## おわりに
今回は

## 参考資料
- [Read the Docs: Configuration](https://sphinx-rtd-theme.readthedocs.io/en/latest/configuring.html)
- [Sphinxを便利にして、みんなに使ってもらいたい](https://qiita.com/pashango2/items/d1b379b699af85b529ce)
- [Sphinx の sphinx_rtd_theme をカスタマイズする
](http://kuttsun.blogspot.com/2016/11/sphinx-sphinxrtdtheme.html)