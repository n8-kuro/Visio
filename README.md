# Visio
erDiagram
  Building {
  int building_id PK
  int class
  int total_rooms
  int rooms_per_floor
  bool has_luggage_service
  bool has_daily_cleaning
  bool has_laundry
  bool has_dry_cleaning
  text food_services
  text entermainment 
  }
  Room {
  int room_id PK
  int building_id FK
  int floor
  string room_number
  int capacity
  decimal base_price
  string status
  }
  Organization {
  int org_id PK
  string name
  string type
  text contact_info
  decimal discount_terms
  }
  Contact {
  int contact_id PK
  date sign_date
  date start_date
  date end_date
  text special_terms
  }
  Booking {
  int bookig_id PK
  int org_id FK
  int building_id FK
  int preferred_floor
  int number_of_rooms
  int number_of_people
  date check_id_date
  date check_out_date
  string status
  date cancellation_date
  decimal applied_discount
  }
  BookingRoom {
  int booking_room_id PK
  int booking_id Fk
  int room_id FK
  }
  Guest {
  int stay_id PK
  int guest_id FK
  int room_id FK
  int booking_id Fk
  timestamp check_in
  timestamp check_out
  decimal total_debt
  }
  Service {
  int complaint_id PK
  int guest_id FK
  int stay_id FK
  timestamp date_reported
  text description
  bool resolved
  }
  Finance {
  int finance_id PK
  int room_id FK
  string status
  timestamp changed_at
  }
  RoomStatusLog {
  int log_id PK
  int room_id FK
  string status
  timestamp changed_at
  }

  Building ||--o{ Room : содержит
  Organization ||--o{ Contact : заключает
  Organization ||--o{ Booking : создает
  Building ||--o{ BookingRoom : бронируется
  Booking ||--o{ BookingRoom : включает
  Room ||--o{ BookingRoom : назначается
  Guest ||--o{ GuestStay : проживает
  Room ||--o{ GuestStay : размещает
  Booking ||--o{ GuestStay : используется
  GuestStay ||--o{ GuestService : используется
  Service ||--o{ GuestService : предоставляется
  Guest ||--o{ Complaint : подает
  GuestStay ||--o{ Complaint : связано
  Room ||--o{ RoomStatusLog : отслеживается
  
  
