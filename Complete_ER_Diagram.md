```mermaid
erDiagram
    MASTERWORKTYPE ||--o{ DELIVERYWORKTYPE : references
    DELIVERYWORKTYPE ||--o{ DELIVERYWORKTYPECATEGORY : references
    DELIVERYWORKTYPECATEGORY ||--|| TICKETTYPE : references
    TICKETTYPE ||--|| TICKETMETADATA : references
    TICKETMETADATA ||--o{ SIMPLEATTRIBUTE : contains_explicitAttributes
    TICKETMETADATA ||--o{ SIMPLEATTRIBUTE : contains_implicitAttributes
    DELIVERYWORKTYPECATEGORY ||--o{ WORKCATEGORY : references
    WORKCATEGORY ||--o{ WORKSUBCATEGORY : references
    WORKCATEGORY ||--o{ WORKITEM : references
    WORKSUBCATEGORY ||--o{ WORKITEM : references
    CLUSTERVALUE ||--o{ WORKITEM : references
    WORKITEM ||--o{ WORKITEMRESOURCELEVEL : references
    MASTERPROJECT ||--o{ SUBPROJECT : references
    SUBPROJECT ||--o{ TASKEFFORT : contains_estimationEffortTable
    SUBPROJECT ||--o{ TASKEFFORT : contains_etlEffortTable
    CLUSTER ||--o{ CLUSTERVALUE : references
    CLUSTERVALUE ||--o{ ADPROJECT : references
    ADPROJECT ||--o{ TASKEFFORT : contains_estimationEffortTable
    ADPROJECT ||--o{ TASKEFFORT : contains_etlEffortTable
    ACTIVITY ||--o{ RELATEDMODEL : references
    PROJECTHIERARCHY ||--o| PROJECTHIERARCHY : parentHierarchy
    PROJECTHIERARCHY ||--o{ PROJECTHIERARCHYPOSITION : references
    PROJECTHIERARCHYPOSITION ||--o| PROJECTHIERARCHYPOSITION : parentPosition
    MASTERWORKTYPE {
        string _id
        string masterWorkTypes
        date createdAt
        date updatedAt
    }
    DELIVERYWORKTYPE {
        string _id
        string deliveryWorkTypes
        reference MasterWorkTypeId "MasterWorkType._id"
        date createdAt
        date updatedAt
    }
    UITYPE {
        string _id
        string uitype "checkbox, radio, button"
        date createdAt
        date updatedAt
    }
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
    ACTIVITY {
        string _id
        string enterpriseId
        date date
        number hours
        string activityType
        reference activityDetails "RelatedModel._id"
        date createdAt
        date updatedAt
    }
    RELATEDMODEL {
        string _id
        string _dynamicModel "Any registered Mongoose model"
    }
    RESOURCECOLUMN {
        string _id
        string name
        date createdAt
        date updatedAt
    }
    RESOURCEMASTER {
        string _id
        map data "Map<string, Mixed>"
        date createdAt
        date updatedAt
    }
    DELIVERYWORKTYPECATEGORY {
        string _id
        string deliveryWorkTypes
        string workTypeCategory
        string taskType
        number sequence
        reference deliveryWorkTypesId "DeliveryWorkType._id"
        date createdAt
        date updatedAt
    }
    TICKETTYPE {
        string _id
        string ticketType
        number sequence
        reference deliveryWorkTypeCategoryId "DeliveryWorkTypeCategory._id"
        date createdAt
        date updatedAt
    }
    TICKETMETADATA {
        string _id
        reference ticketTypeId "TicketType._id"
        array explicitAttributes "SimpleAttribute[]"
        array implicitAttributes "SimpleAttribute[]"
    }
    SIMPLEATTRIBUTE {
        string name
    }
    PROJECTHIERARCHY {
        string _id
        number hierarchyLevel
        string hierarchyName
        reference parentHierarchy "ProjectHierarchy._id"
        date createdAt
        date updatedAt
    }
    PROJECTHIERARCHYPOSITION {
        string _id
        reference hierarchyLevel "ProjectHierarchy._id"
        string hierarchyPosition
        reference parentPosition "ProjectHierarchyPosition._id"
        date createdAt
        date updatedAt
    }
    TIMEOFFCATEGORY {
        string _id
        string name
    }
    WORKCATEGORY {
        string _id
        string name
        reference deliveryWorkTypeCategory "DeliveryWorkTypeCategory._id"
    }
    WORKSUBCATEGORY {
        string _id
        string name
        reference workCategory "WorkCategory._id"
    }
    WORKITEM {
        string _id
        string name
        reference workCategory "WorkCategory._id"
        reference workSubCategory "WorkSubCategory._id"
        reference clusterValue "ClusterValue._id"
        boolean active
        string period "One-Time, Daily, Weekly, FN, Monthly"
        string isEstimateBasedOnResourceLevel "Yes, No"
    }
    WORKITEMRESOURCELEVEL {
        string _id
        reference workItem "WorkItem._id"
        string designation
        number level
        number estimate
    }
