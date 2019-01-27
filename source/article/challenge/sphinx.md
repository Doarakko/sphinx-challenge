# ドキュメント作成によく使われているカッコいいテーマを使って、Github Pages を作ってみた

## ブランチ構成
- master: build されたコンテンツを管理
- source: `source` 下のファイルを管理
    - ユーザページとして作成したため, `master branch` にコンテンツを置く必要がある

### CSS 適用
- `build/html` 下に `.nojekyll`（中身は空）を作成
- GitHub Pages では [jekyll](https://jekyllrb.com/) が使用されているため `_<hoge>` が無視されてしまう
    - jekyll が使用されないようにする