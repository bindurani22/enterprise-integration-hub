A banking Integration Hub lets you naturally discuss:
---
Payments
Loan origination
Customer onboarding
Fraud detection
Notifications
Compliance
Audit
Event-driven processing
---
Systems include:
Internet Banking
Mobile Banking
CRM (Pega / Salesforce)
Loan Origination
Core Banking
Payment Gateway
Fraud Service
Notification Service
Document Service
Data Warehouse
---
The Integration Hub sits in the middle using:

API Gateway
Workflow Engine
Event Streaming (Kafka)
Integration Services
Identity Provider
Observability


Non-Functional Requirements



Architecture Overview
mermaid 
```mermaid
flowchart TB


    subgraph CH["Channels"]
        WB["Web"]
        MB["Mobile"]
        PT["Partner"]
    end 

    ID["Identity Provider"]
    GW["API Gateway"]
    
    subgraph IH["Integration Hub"]
        IS["Integration Services"]
        ES["Event Streaming"]
    end

    WF["Workflow Engine"]
    
    subgraph EX["External Systems"]
        CS["Customer Services"]
        BS["Business Services"]
        AS["3rd Party Services"]
    end       

    subgraph DB["Databases"]
        SQL["SQL DB"]
        NS["NoSQL DB"]
    end

      

    MN["Monitoring"]
    AN["Analytics"]
   
    CH --> GW

    GW --> ID
    GW --> WF
    GW --> IH

    WF <--> IH
    WF -->  DB
    WF <-->  EX

    %%IH --> WF
    IH <--> EX
    IH -->DB
    IH --> MN
    IH -->AN  

    ID ~~~ GW
    %%WF ~~~ IH
    %%WF ~~~ EX

    %%EX ~~~ DB
    %%DB ~~~ MN
    %%MN ~~~ AN
```
