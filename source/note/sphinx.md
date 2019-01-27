# Sphinx
## Requirements
- Python 3.6.5 
- pip 18.1

## Directory Structure
```
.
├── Makefile
├── README.md
├── build
│   ├── doctrees
│   └── html
├── make.bat
└── source
    ├── _static
    ├── _templates
    ├── conf.py
    ├── html
    └── index.md
```

## Set Up
### テーマの設定
- ライブラリのドキュメントによく使われているテーマ（[LightGBM](https://lightgbm.readthedocs.io/en/latest/), [Optuna](https://optuna.readthedocs.io/en/latest/), etc）を使用
```
pip install sphinx_rtd_theme
```
- `conf.py`
```
html_theme = 'sphinx_rtd_theme'
```

### テーマのカスタマイズ
- 各テーマのソースコードを見て、どのファイルに CSS が記述されているか確認
- そのファイルを `import` して編集
- `style.css`
```
@import url("theme.css");
 
.wy-nav-content {
    max-width: none;
    max-height: none;
}

h1,h2,h3,h4,h5,h6 {
    border-bottom: 1px solid #ccc;
}
```
- `conf.py`
```
# customize default css
html_style = "/css/style.css"
```
### MarkDown
- `conf.py`
```
from recommonmark.transform import AutoStructify
from recommonmark.parser import CommonMarkParser

source_suffix = ['.md']

source_parsers = {
    '.md': CommonMarkParser,
}
```
### Jupyter Notebook(動作未確認)
```
$ pip install nbsphinx
```
### HTML 形式で記述
- `<HTML ファイルが配置されたディレクトリ>` 下のファイル（or フォルダ）が `build/html` 下に配置される
    - `<HTML ファイルが配置されたディレクトリ>` は無視されるので注意
- `conf.py`
```
html_extra_path = ['<HTML ファイルが配置されたディレクトリ>']
```
## Memo
- `$ make html` を実行すると `build/html` 下に build される
- CSS を修正して build する際は以下を実行
    - `build/html` 下の `.git` が削除されるため注意
```
$ make clean html
```

## Problem
- `conf.py` の `html_theme_options` が適用されない
    - 原因調査中
- `$ make clean html` 実行時に `.git` なども一緒に削除されてしまう
    - Makefile 修正予定

## Reference
- [Read the Docs: Configuration](https://sphinx-rtd-theme.readthedocs.io/en/latest/configuring.html)
- [Sphinxを便利にして、みんなに使ってもらいたい](https://qiita.com/pashango2/items/d1b379b699af85b529ce)
- [Sphinx の sphinx_rtd_theme をカスタマイズする
](http://kuttsun.blogspot.com/2016/11/sphinx-sphinxrtdtheme.html)