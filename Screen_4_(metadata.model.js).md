# Ticket Meta Data ER Diagram

```mermaid
erDiagram
    TICKETTYPE ||--|| TICKETMETADATA : references
    TICKETMETADATA ||--o{ SIMPLEATTRIBUTE : contains_explicitAttributes
    TICKETMETADATA ||--o{ SIMPLEATTRIBUTE : contains_implicitAttributes
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
