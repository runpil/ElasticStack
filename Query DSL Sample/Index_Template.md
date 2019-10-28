```json
PUT _template/db-perfmon-template
{
  "order": 2,
  "index_patterns": [
    "db-perfmon-*"
  ],
  "settings": {
    "index": {
      "number_of_shards": "3",
      "number_of_replicas": "1"
    }
  },
  "mappings": {
    "_default_": {
      "dynamic_templates": [
        {
          "strings_as_keywords": {
            "match_mapping_type": "string",
            "mapping": {
              "type": "keyword"
            }
          }
        }
      ],
      "properties": {
        "counterdatetime": {
          "type": "keyword"
        },
        "dml_type": {
          "type": "keyword"
        },
        "doc_id": {
          "type": "keyword"
        },
        "executing_query": {
          "type": "keyword"
        },
        "executing_query_cpu_time": {
          "type": "float"
        },
        "executing_query_start_time": {
          "type": "keyword"
        },
        "executing_query_time": {
          "type": "float"
        },
        "hostname": {
          "type": "keyword"
        },
        "idx": {
          "type": "long"
        },
        "last_wait_type": {
          "type": "keyword"
        },
        "loginame": {
          "type": "keyword"
        },
        "logtype": {
          "type": "keyword"
        },
        "machinename": {
          "type": "keyword"
        },
        "procedure_name": {
          "type": "keyword"
        },
        "program_name": {
          "type": "keyword"
        },
        "session_count": {
          "type": "long"
        },
        "session_id": {
          "type": "long"
        },
        "session_status": {
          "type": "keyword"
        },
        "session_wait_type": {
          "type": "keyword"
        }
      }
    }
  }
}
```