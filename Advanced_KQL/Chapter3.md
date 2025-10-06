KQL Queries from the [Advanced Must Learn KQL](https://amzn.to/4ocNTON) book.
<br><br>
```kql
StormEvents | where State == "FLORIDA" | count
---
---
```kql
StormEvents | where InjuriesDirect + InjuriesIndirect > 50 | join (PopulationData) on State | project State, Population, TotalInjuries = InjuriesDirect + InjuriesIndirect
---
