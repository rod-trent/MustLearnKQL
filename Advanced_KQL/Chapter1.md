KQL Queries from the [Advanced Must Learn KQL](https://amzn.to/4ocNTON) book.
<br><br>
```
```kql
datatable(ID: int, Tags: dynamic)
[
    1, dynamic(["Azure", "Cloud", "Data"]),
    2, dynamic(["AI", "Machine Learning"]),
    3, dynamic(["Big Data", "Analytics"])
]
| mv-expand Tags
```
---

```
```kql
// Sample KQL query
StormEvents
| where EventType == "Tornado"
| summarize Count = count() by State
| order by Count desc
```

