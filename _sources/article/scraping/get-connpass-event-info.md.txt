# Connpass のイベント情報を取得する in Python
Connpass API を使用してイベント情報を取得してみました。
会員登録等はいらないです。

リクエスト送るときには、1秒スリープ入れましょう。

## Requirement
- anaconda3-5.2.0 
    - Python 3.6.5

## Program
```
import time
import requests

URL = 'https://connpass.com/api/v1/event/'


def get_event_url(keyword, count=10):
    """
    イベント情報を取得する

    Parameters
    ----------
    keyword : string
        検索するキーワード
    count : int, default 10
        取得するイベント数
    """

    params = {
        'keyword': keyword,
        'count': count,
    }
    response = requests.get(URL, params=params)
    time.sleep(1)
    resources = response.json()

    for event in resources['events']:
        print(event['event_url'])

get_event_url('python', 20)
```
```
$ python get_event_url.py
https://python-web.connpass.com/event/108056/
https://coderdojo-tachikawa.connpass.com/event/109668/
https://bpstudy.connpass.com/event/109688/
https://soracom.connpass.com/event/110110/
https://fukuokaphp.connpass.com/event/109317/
https://connpass.com/event/109698/
https://maid-cafe-nomad.connpass.com/event/109572/
https://itpropartners.connpass.com/event/85381/
https://python-algo.connpass.com/event/104394/
https://pyhack.connpass.com/event/110414/
https://ai-iot-bol-fukui.connpass.com/event/104798/
https://nnc.connpass.com/event/106620/
https://data-science-academy.connpass.com/event/107546/
https://speee.connpass.com/event/103514/
https://coderdojo-sapporo.connpass.com/event/110267/
https://soil.connpass.com/event/107287/
https://supporterz-seminar.connpass.com/event/107463/
https://supporterz-seminar.connpass.com/event/107979/
https://forcia.connpass.com/event/110173/
https://forcia.connpass.com/event/110138/
```
## Hint
設定できるパラメータとレスポンスは、[API リファレンス](https://connpass.com/about/api/)に書いてあります。
日本語なので気軽に見てください。
緯度と経度が取得できるのは面白いです。

定員と参加者数を使用して、参加可能なイベントのみ送ってくる Bot を作成するのも良いですね。

```
# イベントタイトル
event['title']
# 開催場所
event['address']
# 緯度
event['lat']
# 経度
event['lon']
# 定員
event['limit']
# 参加者数
event['accepted']
```

個人的には、参加者（申込者）のアカウントが取ってこれないのが残念です。
[Connpass の利用規約](https://connpass.com/term/)ではスクレイピング自体は禁止していません。
API を使って取得した URL を、サイトの運営を妨げない範囲でスクレイピングすればいけますね。
> 第２条【サービス】
>> 当サイトの利用に際してはウェブにアクセスする必要がありますが、利用者は自らの費用と責任で必要な機器・ソフトウェア・通信手段等を用意し適切に接続・操作することとします。

> 第７条【禁止事項】
>> 当サイトの運営を妨げる、または、当社の信用を毀損する行為

## Reference
- [connpass API リファレンス](https://connpass.com/about/api/)
- [Connpass 利用規約](https://connpass.com/term/)
