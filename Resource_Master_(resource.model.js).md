# Resource Master ER Diagram

```mermaid
erDiagram
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
