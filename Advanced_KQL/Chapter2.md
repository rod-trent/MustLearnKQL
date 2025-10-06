KQL Queries from the [Advanced Must Learn KQL](https://amzn.to/4ocNTON) book.
<br><br>
```
Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=23, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)
```
---
```
Traces | parse EventText with * "resourceName=" resourceName ", totalSlices=" totalSlices: long * "sliceNumber=" sliceNumber: long * "lockTime=" lockTime ", releaseTime=" releaseTime: date "," * "previousLockTime=" previousLockTime: date ")" *
```
---
```
Leads | parse Contacts with * "email=" alias: string "@" domain: string ", Website=https:" WebsiteDomain: string ")" | project EmailAddress=strcat(alias, "@", domain), EmailAlias=alias, WebsiteDomain
```
---
```
Traces | parse kind=regex flags=Ui EventText with * "resourceName=" resourceName ',' *
```
---
