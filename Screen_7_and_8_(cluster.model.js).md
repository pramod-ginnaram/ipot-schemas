# Cluster ER Diagram

```mermaid
erDiagram
    CLUSTER ||--o{ CLUSTERVALUE : references
    CLUSTERVALUE ||--o{ ADPROJECT : references
    ADPROJECT ||--o{ TASKEFFORT : contains_estimationEffortTable
    ADPROJECT ||--o{ TASKEFFORT : contains_etlEffortTable
    CLUSTER {
        string _id
        string name
        date createdAt
        date updatedAt
    }
    CLUSTERVALUE {
        string _id
        string name
        reference cluster "Cluster._id"
        date createdAt
        date updatedAt
    }
    ADPROJECT {
        string _id
        string name
        reference clusterValue "ClusterValue._id"
        number estimationPersonDays
        number etlPersonDays
        array estimationEffortTable "TaskEffort[]"
        array etlEffortTable "TaskEffort[]"
        date createdAt
        date updatedAt
    }
    TASKEFFORT {
        string projectTask
        number distribution
        number estimatedEffort
        number burntEffort
    }
