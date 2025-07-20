 ```mermaid
 erDiagram
     USER {
         int user_id PK
         string name
         string email
         string password
     }
     NOTARYPROFILE {
         int notary_id PK
         int user_id FK
         string license_number
         int experience_years
     }
     SERVICE {
         int service_id PK
         int notary_id FK
         string service_type
         string description
         float price
     }
     APPOINTMENT {
         int appointment_id PK
         int user_id FK
         int service_id FK
         datetime appointment_date
         string status
     }
     REVIEW {
         int review_id PK
         int appointment_id FK
         int rating
         string comment
     }

     USER ||--|| NOTARYPROFILE : "has"
     NOTARYPROFILE ||--o{ SERVICE : "offers"
     USER ||--o{ APPOINTMENT : "books"
     SERVICE ||--o{ APPOINTMENT : "is booked in"
     APPOINTMENT ||--|| REVIEW : "has"
 ```
 ````
