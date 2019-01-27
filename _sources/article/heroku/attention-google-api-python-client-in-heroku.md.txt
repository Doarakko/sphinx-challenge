# Heroku で google-api-python-client を使用する際の注意点
## 概要
Heroku で `google-api-python-client` ライブラリを Python で使用した際につまづいたことをまとめました。

## 注意点
ここで使用している `oauth2client` ライブラリは廃止予定です。

> Note: oauth2client is now deprecated. As such, it is unlikely that we will address or respond to your issue. We recommend you use google-auth and oauthlib.

[oauth2client/.github/ISSUE_TEMPLATE.md](https://github.com/googleapis/oauth2client/blob/master/.github/ISSUE_TEMPLATE.md)

 気が向いたら修正します。

## 実行環境
- Python 3.6.5 
    - google-api-python-client==1.7.7
    - httplib2==0.12.0
    - oauth2client==4.1.3
- Heroku CLI

## 課題1：`token.json` をそのまま上げるわけにはいかない
### 解決策①：Heroku CLI で環境変数を設定
以下コマンドで、JSON ファイルを環境変数として設定できます。

```
$ heroku config:set GOOGLE_APPLICATION_CREDENTIALS="$(< token.json)"
```
### 解決策②：ブラウザ上から環境変数を設定
JSON ファイルの中身をコピペします。
![スクリーンショット 2019-01-05 19.31.23.png](https://qiita-image-store.s3.amazonaws.com/0/245792/4b1150b1-7156-438c-5f86-127f41b11147.png)

どちらでも OK です。

## 課題2：環境変数をどう使うか

以下 [Google Calender API のサンプルプログラム](https://developers.google.com/calendar/quickstart/python)の抜粋。

```python
store = file.Storage('token.json')
creds = store.get()
# 省略
service = build('calendar', 'v3', http=creds.authorize(Http()))
```
ここではローカルにある `token.json` を読み込んで、「**なにか**」してから`googleapiclient.discovery.build` に渡しています。

つまり、環境変数をそのまま渡してもうまくいきません。
環境変数に対して同じ「**なにか**」をしてあげる必要があります。

### 解決策: [ソース](https://github.com/googleapis/oauth2client) を見る
以下 [oauth2client のソースコード](https://github.com/googleapis/oauth2client/blob/master/oauth2client/file.py)抜粋。

```python: oauth2client/oauth2client/file.py
try:
    f = open(self._filename, 'rb')
    content = f.read()
    f.close()
except IOError:
    return credentials

try:
    credentials = client.Credentials.new_from_json(content)
    credentials.set_store(self)
except ValueError:
    pass
```
JSON ファイルを開いた後に、`client.Credentials.new_from_json` で処理しています。
そこで、環境変数 `GOOGLE_APPLICATION_CREDENTIALS` に対しても同じことをしてあげれば OK です。

```python

from httplib2 import Http
from oauth2client import client
from googleapiclient.discovery import build

CONTENTS = os.environ.get('GOOGLE_APPLICATION_CREDENTIALS')
CREDS = client.Credentials.new_from_json(CONTENTS)
SERVICE = build('calendar', 'v3', http=CREDS.authorize(Http()))
```

`oauth2client/oauth2client/file.py` で `with`ブロックが使われていないことに違和感を感じ、いろいろ見ていたら `oauth2client` が廃止予定であることがわかりました。

## おわりに
Google API のサンプルプログラムが廃止予定の `oauth2client` で書かれていますが、現在[こちら](https://github.com/gsuitedevs/python-samples/issues/10)で issue が立っているので、そのうち修正されると思います。

## 参考資料
- [oauth2client](https://github.com/googleapis/oauth2client)
- [Using Google Cloud With Heroku](https://simpleit.rocks/apis/google-cloud/using-google-cloud-with-heroku/)
