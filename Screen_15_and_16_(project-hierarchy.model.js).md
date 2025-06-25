# Project Hierarchy ER Diagram

```mermaid
erDiagram
    PROJECTHIERARCHY ||--o| PROJECTHIERARCHY : parentHierarchy
    PROJECTHIERARCHY ||--o{ PROJECTHIERARCHYPOSITION : references
    PROJECTHIERARCHYPOSITION ||--o| PROJECTHIERARCHYPOSITION : parentPosition
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
