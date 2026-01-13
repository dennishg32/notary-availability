 ```mermaid
 erDiagram

  classDiagram
    class USER {
        <<PK>> id : string
        <<UK>> email : string
        name : string
        password : string
        role : enum
        phone : string
        isApproved : boolean
        address : string
        city : string
        hourlyRate : float
        avgRating : float
    }

    class SERVICE {
        <<PK>> id : string
        <<UK>> name : string
        description : string
        basePrice : float
        customPrice : float
    }

    class CERTIFICATION {
        <<PK>> id : string
        <<UK>> name : string
        description : string
        dateObtained : datetime
        <<FK>> userId : string
    }

    class APPOINTMENT {
        <<PK>> id : string
        <<FK>> customerId : string
        <<FK>> notaryId : string
        <<FK>> serviceId : string
        scheduledTime : datetime
        status : string
        totalCost : float
    }

    class REVIEW {
        <<PK>> id : string
        <<FK>> appointmentId : string
        <<FK>> customerId : string
        rating : int
        comment : string
    }

    %% Relationships
    USER "1" --> "*" SERVICE : offers
    USER "1" --> "*" CERTIFICATION : holds
    USER "1" --> "*" APPOINTMENT : books
    APPOINTMENT "1" --> "1" REVIEW : has

 ```
 ````
