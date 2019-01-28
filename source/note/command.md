# Command
## zip, unzip
- zip ファイルを解凍
```
$ unzip <file path>.zip <解凍先>
```

## asadmin
- サーバ起動
```
$ asadmin start-domain domain1
```
- サーバ停止
```
$ asadmin stop-domain domain1
```
- デプロイ
```
$ asadmin deploy <target>
```
- 再デプロイ
    - プロジェクト名を入力
```
$ asadmin redeploy <target>
```
## emacs
- 復帰
    - 中断状態（cntl + z）の際に実行
```
$ fg
```
- ショートカット
```
中断: cntl + z
```
## maven
- `target` 下を削除
```
$ mvn clean
```
- maven のローカルリポジトリに登録
```
$ mvn install
```
- ビルド
```
$ mvn package
```

## tmux
- 起動
```
$ tmux
```

- ショートカット
```
ウインドウ切替: cntl + B, O
ウインドウ分割: cntl + B, %
```