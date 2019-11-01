# Elasticsearch Node 재시작 방법

## Shard Allocation 중지
  - 노드를 중단했을 때 샤드들이 재배치 되지 않도록 다음 명령 실행
```json
PUT _cluster/settings
{
  "persistent": {
    "cluster.routing.allocation.enable": "none"
  }
}
```
## Sync Flush 실행
  - Primary - Replica 샤드들 간의 세그먼트 저장 상태 동기화
```json
POST _flush/synced
```

## 노드 중단
```bash
kill `cat es.pid`
```

## 필요한 작업 진행
  - ex) jvm heap size 변경

## 중단한 노드 재시작 및 상태확인
- 노드 재시작
```bash
bin/elasticsearch -d -p es.pid
```
- 노드가 정상적으로 실행됐는지 확인
```json
GET _cat/nodex
```

## Shard Allocation 재가동
  - unassigned 된 샤드들이 새 노드에 다시 배치되도록 다음 명령 실행
```json  
PUT _cluster/settings
{
  "persistent": {
    "cluster.routing.allocation.enable": null
  }
}
```

## 클러스터 상태 확인
  - 상태가 Green 이 될 때까지 기다림
```json
GET _cat/health
```