# Youtube のコメントを取得する in Python

## Requirement
- Youtube API Key
    - 取得方法は説明しません
- YouTube Data API v3
- anaconda3-5.2.0
    - Python 3.6.5

## Program
```
import requests
import json

URL = 'https://www.googleapis.com/youtube/v3/'
API_KEY = 'your key'

def print_video_comment(video_id, n=10):
    params = {
        'key': API_KEY,
        'part': 'snippet',
        'videoId': video_id,
        'order': 'relevance',
        'textFormat': 'plaintext',
        'maxResults': n,
    }
    response = requests.get(URL + 'commentThreads', params=params)
    resource = response.json()

    for comment_info in resource['items']:
        # コメント
        text = comment_info['snippet']['topLevelComment']['snippet']['textDisplay']
        # グッド数
        like_cnt = comment_info['snippet']['topLevelComment']['snippet']['likeCount']
        # 返信数
        reply_cnt = comment_info['snippet']['totalReplyCount']

        print('{}\nグッド数: {} 返信数: {}\n'.format(text, like_cnt, reply_cnt))

video_id = 'hoge'
print_video_comment(video_id, n=5)
```
## Usage
```
$ python youtube.py
みんなの期待通りの内容だったかな！？
グッド数: 421 返信数: 34

微妙に太っている所がまた好きww
グッド数: 151 返信数: 3

はい、シンギュラリティ で笑いを我慢できなくなった
グッド数: 102 返信数: 4

*When the art style of an anime is vastly different compared to the manga's art style*
グッド数: 71 返信数: 1

サムネの顔で絶望した、訴訟
グッド数: 112 返信数: 0
```

## Hints
### videoId
```python
video_id = 'd1tnWnzWzm4'
```
`video_id` は動画 URL のこのパラメータのことです.

![](https://qiita-image-store.s3.amazonaws.com/0/245792/50ff8a6b-1323-b068-4f3d-926b25d56e5a.png)

### order
```python
'order': 'relevance',
```
デフォルト（`time `）では、直近のコメントを取ってきます。
`relevance` を指定することで、グッド数とコメント数が多い順に取ってこれます。

### textFormat

```python
'textFormat': 'plaintext',
```
コメントのフォーマットを html か plain text か選択できます。
デフォルトは html です。



## API limits
[こちら](https://developers.google.com/youtube/v3/getting-started#quota)をみてください。

## Regards
YouTube Data API にはたくさんの機能が用意されているので、それと組み合わせて

- どんなコメントがグッドまたは返信されやすいのか
- チャンネルごとの視聴者の民度
- 視聴回数の割にコメント数が多い（少ない）動画

などを分析してみるのはおもしろそうです。

## Reference
- [YouTube Data API ドキュメント](https://developers.google.com/apis-explorer/?hl=ja#p/youtube/v3/)
- [公式サンプル](https://developers.google.com/youtube/v3/code_samples/)
- [利用制限](https://developers.google.com/youtube/v3/getting-started#quota)
