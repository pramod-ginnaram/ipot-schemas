```mermaid
erDiagram
    DELIVERYWORKTYPECATEGORY ||--o{ WORKCATEGORY : references
    WORKCATEGORY ||--o{ WORKSUBCATEGORY : references
    WORKCATEGORY ||--o{ WORKITEM : references
    WORKSUBCATEGORY ||--o{ WORKITEM : references
    CLUSTERVALUE ||--o{ WORKITEM : references
    WORKITEM ||--o{ WORKITEMRESOURCELEVEL : references
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
    CLUSTERVALUE {
        string _id
        string name
        reference cluster "Cluster._id"
        date createdAt
        date updatedAt
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
