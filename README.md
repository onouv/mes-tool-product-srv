# mes-tool-product-srv
A microservice to process product events from tools

This service subscribes to product-related events from the mes-bus, processes them to calulate Yield data for tools and post the result back to the Yield value topic: 
```
Y := {
  TAP := number   # Total Amount Produced
  AAP := number   # Actual Amount Produced
  RAP := number   # Rejected Amount Produced
  toolId: string
}

On PartIn :       ---     # may be used later for product tracking

On PartOutGood : 
  Y.TAP++
  Y.AAP++
  post to Yield value Topic

On PartOutRejected : 
  Y.TAP++
  Y.RAP++
  post to Yield value Topic
```
## Fit Into Overall Architecture
![Overall Architecture](mes-deploy.png)

* ![mes-tool-mock-srv](https://github.com/onouv/mes-tool-product-srv)
* ![mes-tool-status-srv](https://github.com/onouv/mes-tool-status-srv)
* ![mes-tool-kpi-srv](https://github.com/onouv/mes-tool-kpi-srv)
* ![mes-tool-dashboard-srv](https://github.com/onouv/mes-tool-dashboard-srv)
