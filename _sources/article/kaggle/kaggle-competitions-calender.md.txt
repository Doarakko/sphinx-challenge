# Kaggle の Google Calender を作りました
## はじめに
「[Kaggle Advent Calender 2018](https://qiita.com/advent-calendar/2018/kaggle)」25 日目の記事です。
 

## 概要
Kaggle API をうまく使ってコンペの Google カレンダーを作ります。

Kaggle のカレンダーは、過去に[こちら](https://www.kaggle.com/general/2756)の公式フォラームに投稿されていましたが、現在は機能していません。

以下はプログラムの説明になります。
カレンダーだけ見たい方は[こちら](https://doarakko.github.io/products/kaggle-competitions-calender.html)からどうぞ。


## 実行環境 
- anaconda3-5.2.0
    - Python 3.6.5
         - kaggle 1.5.0

- Kaggle API Key
    - 説明は省きます
    - `kaggle` コマンドが実行できるような状態にしておいてください

- Google Calender API
    - v3
    - 説明は省きます

- Heroku

## 手順
### 1. Kaggle API でコンペの情報取得
[こちら](https://doarakko.hatenablog.com/entry/kaggle_api_in_python)
の記事を参考に Kaggle API を Python で実行します。



```python
from kaggle.api.kaggle_api_extended import KaggleApi

def get_competitions_list(category='featured'):
    api = KaggleApi()
    api.authenticate()
    return api.competitions_list(category=category)
```

### 2. カレンダーに登録されているイベント名を取得
```python
def get_event_name_list():
    now = datetime.datetime.utcnow().isoformat() + 'Z'
    events_result = service.events().list(
        calendarId=CALENDER_ID, timeMin=now).execute()
    events = events_result.get('items', [])

    events_name = []
    for event in events:
        events_name.append(event['summary'])

    return events_name
```

### 3. 新規コンペをカレンダーに登録
```python
def create_events(competitions_list):
    event_name_list = get_event_name_list()
    if event_name_list is None:
        return 0

    for competition_info in competitions_list:
        competition_name = getattr(competition_info, 'title')

        now = datetime.datetime.utcnow().isoformat()

        end_date = getattr(competition_info, 'deadline')
        end_date = timezone('UTC').localize(end_date)
        end_date = end_date.isoformat()

        # 新規コンペの場合
        if competition_name not in event_name_list and now < end_date:
            key_list = ['description', 'evaluationMetric', 'isKernelsSubmissionsOnly', 'tags', 'url']
            description = ''
            for key in dir(competition_info):
                if key in key_list:
                    description += '{}: {}\n'.format(key, getattr(competition_info, key))

            start_date = getattr(competition_info, 'enabledDate')
            start_date = timezone('UTC').localize(start_date)
            start_date = start_date.isoformat()

            body = {
                'summary': competition_name,
                'description': description,
                'start': {
                    'dateTime': start_date,
                    'timeZone': 'America/Los_Angeles',
                },
                'end': {
                    'dateTime': end_date,
                    'timeZone': 'America/Los_Angeles',
                },
                'reminders': {
                    'useDefault': False,
                },
                'visibility': 'public',
            }
            event = service.events().insert(calendarId=CALENDER_ID, body=body).execute()
            print('[Create] {}'.format(competition_name))
```

`key_list`に設定したものを、イベントの説明欄に入れます。
```python
key_list = ['description', 'evaluationMetric', 'isKernelsSubmissionsOnly', 'tags', 'url']
description = ''
for key in dir(competition_info):
    if key in key_list:
        description += '{}: {}\n'.format(key, getattr(competition_info, key))
```

以下がイベントの登録処理です。    
タイムゾーンが`America/Los_Angeles`になっていますが、こちらは`dateTime`がどのタイムゾーンかを入れます。最初戸惑いました。

あとは、個人のカレンダーの設定に合わせて Google 側でうまくやってくれます。

```python
body = {
    'summary': competition_name,
    'description': description,
    'start': {
        'dateTime': start_date,
        'timeZone': 'America/Los_Angeles',
    },
    'end': {
        'dateTime': end_date,
        'timeZone': 'America/Los_Angeles',
    },
    'reminders': {
        'useDefault': False,
    },
    'visibility': 'public',
}
event = service.events().insert(calendarId=CALENDER_ID, body=body).execute()
```

### 4. Heroku にあげて定期実行
省略します。

## おわりに
2019 年も楽しい Kaggle ライフが送れそうです。
[f:id:Doarakko:20181225075647p:plain]

## 参考資料
- [作ったカレンダー](https://doarakko.github.io/products/kaggle-competitions-calender.html)
- [作ったプログラム](https://github.com/Doarakko/kaggle-competitions-calender)
- [「Kaggle API」を Python で実行してみた](https://doarakko.hatenablog.com/entry/kaggle_api_in_python)
- [Kaggle API](https://github.com/Kaggle/kaggle-api)