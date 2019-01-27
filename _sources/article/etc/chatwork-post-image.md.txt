# ChatWork に画像をアップロード in Python
ChatWork に[ファイルをアップロードする API](https://blog-ja.chatwork.com/2018/07/20187.html) がリリースされていたので使ってみました。

## Requirement
- anaconda3-5.2.0(Python 3.6.5)

## Program
```python:
import requests

END_POINT = 'https://api.chatwork.com/v2/'
API_TOKEN = 'your api token'


def post_jpeg(room_id, file_path, message=''):
    url = '{}rooms/{}/files'.format(END_POINT, room_id)
    jpeg_bin = open(file_path, 'rb')
    headers = {'X-ChatWorkToken': API_TOKEN}
    files = {
        'file': ('kawaii.jpg', jpeg_bin, 'image/jpeg'),
        'message': message,
    }
    request = requests.post(url, headers=headers, files=files)

room_id = 'your room id'
file_path = './hoge.jpg'
message = '正義'
post_jpeg(room_id, file_path, message)

```
![kawaii.jpg](https://qiita-image-store.s3.amazonaws.com/0/245792/dddcf617-4009-56f5-efbc-09ae4a80e153.png)

## Hint
- message は必須ではないです。
- 'image/jpeg' の部分は [Content-Type](https://qiita.com/AkihiroTakamura/items/b93fbe511465f52bffaa) での記述になります、他のファイル形式でも試してみてください。

```python:post_jpeg
files = {'file': ('kawaii.jpg', jpeg_bin, 'image/jpeg')}
```

## Reference
- [ChatWork API ドキュメント](http://developer.chatwork.com/ja/endpoint_rooms.html)

## Hints
- [Qiita](https://qiita.com/Doarakko/items/b7f44c227cd712da1051)