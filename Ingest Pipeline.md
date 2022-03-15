```json
PUT _ingest/pipeline/rename_field

{
  "description": "Rename engagementRate to engagement_rate",
  "processors": [
    {
      "rename": {
        "field": "metrics.engagementRate",
        "target_field": "metrics.engagement_rate",
        "ignore_failure": true
      }
    }
  ]
}

POST _reindex
{
  "source": {
    "index": "instagram"
  },
  "dest": {
    "index": "instagram_new",
    "pipeline": "rename_field"
  }
}
```