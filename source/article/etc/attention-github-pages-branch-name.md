# GitHub Pages で Web ページを公開する際のブランチ名
GitHub Pages でユーザページを作成していた際に、戸惑ったのでまとめます。
## ケース
- （コンテンツを作成するための）ソースとコンテンツを別ブランチで管理
    - Exapmle: [Sphinx](http://www.sphinx-doc.org)
- 公開するコンテンツと編集中のコンテンツを別ブランチで管理
    - Example: OSS のドキュメント等の閲覧者が多い、バージョン管理をするもの

![](/_static/img/github-pages-setting.png)

## 設定できるブランチ名
### ユーザ（or 組織）ページ
- `master`

### プロジェクトページ
- `master`
    - `master` ブランチ直下の `/docs` 下を指定可能
    - `/docs` 下のみが公開される
- `gh-pages`



## おわりに
書いといてあれですが、「ドキュメントを読め」につきますね。

## 参考資料
- [GitHub Help: User, Organization, and Project Pages](https://help.github.com/articles/user-organization-and-project-pages/)

## Hints
- [サンプル](https://github.com/Doarakko/Doarakko.github.io)