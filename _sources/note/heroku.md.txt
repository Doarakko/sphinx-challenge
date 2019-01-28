# Heroku
## Requirements
- heroku/7.19.4

## Command
- ログイン
```
$ heroku login
```

- Push
```
$ git push heroku master
```

- スケジューラ追加
    - 設定はダッシュボード上で行う
```
$ heroku addons:create scheduler:standard
```

- Postgres