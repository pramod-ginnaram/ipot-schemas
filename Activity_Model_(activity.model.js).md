# Activity ER Diagram

```mermaid
erDiagram
    ACTIVITY ||--o{ RELATEDMODEL : references
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
