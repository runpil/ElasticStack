# 새로운 인덱스 생성
```json
POST _reindex
{
  "source": {
    "index": "movie-list"
  },
  "dest": {
    "index": "movie-list-v2",
    "op_type": "create"
  },
  "conflicts": "proceed"
}
```
# 생성된 인덱스에 데이터 입력
```json
POST _reindex
{
  "source": {
    "index": "movie-list"
  },
  "dest": {
    "index": "movie-list-v3"
  },
  "conflicts": "proceed"
}
```