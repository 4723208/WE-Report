# 第6回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208
## 実装した内容
```json
curl -X 'PUT' \
  'http://127.0.0.1:8000/todos/1' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "GFPレポート作成",
  "description": "本日中",
  "completed": true
}'
```



## 動作確認結果
正常系：
```json
{
  "id": 1,
  "title": "GFPレポート作成",
  "description": "本日中",
  "completed": true
}
```
異常系：存在しないタスクIDでのエラー確認
```json
{
  "detail": "Object \"TodoItem\" does not exist"
}
```