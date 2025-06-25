# Project ER Diagram

```mermaid
erDiagram
    MASTERPROJECT ||--o{ SUBPROJECT : references
    SUBPROJECT ||--o{ TASKEFFORT : contains_estimationEffortTable
    SUBPROJECT ||--o{ TASKEFFORT : contains_etlEffortTable
    MASTERPROJECT {
        string _id
        string name
        date createdAt
        date updatedAt
    }
    SUBPROJECT {
        string _id
        string name
        reference masterProject "MasterProject._id"
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
