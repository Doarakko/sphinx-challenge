# Git
- ブランチ一覧表示
```
$ git branch
```
- 新規ブランチ作成
```
$ git branch -b <branch name>
```

- ブランチ切替
```
$ git checkout <branch name>
```

- ブランチ名変更
```
$ git branch -m <src name> <dst name>
```

- ブランチ削除
```
$ git branch --delete <branch name>
```

- キャッシュ削除
    - `.gitignore` が適用されない場合に実行
```
$ git rm -r --cached
```

## Reference
- [.gitignoreに記載したのに反映されない件](https://qiita.com/fuwamaki/items/3ed021163e50beab7154)