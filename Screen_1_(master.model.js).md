# Master And Delivery Work Type ER Diagram

```mermaid
erDiagram
    MASTERWORKTYPE ||--o{ DELIVERYWORKTYPE : references
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
