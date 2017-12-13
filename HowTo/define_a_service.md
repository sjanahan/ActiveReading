# Service Name
> Short description of the service and what is solves

> Owner: <Example> Team

[Lucid chart of service architecture]()

##Stakeholders
* Uses
    * What does this service depend on?
* Used By
    * Read
      * Which services are reading from this service?
    * Write
      * Which services are updating it?

## Interfaces
Detail the different interaction points for the service. If it offers one or more API's, queues, databases or s3 folders. Any way that another service may interface with it.
1. External API 
  * example...
2. Internal API 
  * example...
3. Example Topic

# SLA's
|SLA|External API|Internal API|
|---|------------|------------|
|Concurrency|10 req/s|10 req/s|
|95% Latency|50 ms|50ms|
|100% Latency|500ms|500ms|
|Request Success Rate|99.99%|99.99%|
|Data Timelines|instant|1 min|
|Data Consistency|instant|instant|

## API
* External API : https://github.com/<company>/<service>/blob/develop/swagger.yaml
* Internal API : TBD

## Example Topic

```
   FeatureChangeEvent {
       "account_id": "xyz",
       "site_ids": ["a","b"],
       "type": "feature_change"
   }
``` 

## Resources
(Runbooks)[] 
(Monitors)[]
(Repos)[]
