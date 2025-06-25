# Delivery Worktype Category ER Diagram

```mermaid
erDiagram
    DELIVERYWORKTYPE ||--o{ DELIVERYWORKTYPECATEGORY : references
    DELIVERYWORKTYPE {
        string _id
        string deliveryWorkTypes
        reference MasterWorkTypeId "MasterWorkType._id"
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
