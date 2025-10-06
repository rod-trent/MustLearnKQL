KQL Queries from Chapter 1 of the [Advanced Must Learn KQL](https://amzn.to/4ocNTON) book.
<br><br>
```
datatable(ID: int, Tags: dynamic)
[
    1, dynamic(["Azure", "Cloud", "Data"]),
    2, dynamic(["AI", "Machine Learning"]),
    3, dynamic(["Big Data", "Analytics"])
]
| mv-expand Tags
```
---
