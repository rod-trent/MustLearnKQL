KQL Queries from the [Advanced Must Learn KQL](https://amzn.to/4ocNTON) book.
<br><br>
```
StormEvents | where State == "FLORIDA" | count
```
---
```
StormEvents | where InjuriesDirect + InjuriesIndirect > 50 | join (PopulationData) on State | project State, Population, TotalInjuries = InjuriesDirect + InjuriesIndirect
```
---
