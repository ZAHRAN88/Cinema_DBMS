# Detailed Cinema Database Management System Entity Explanations

## 1. Movies Entity

### Key Attributes:
- **Movie ID (PK)**: Unique identifier for each movie
- **Title**: Name of the movie
- **Duration**: Length of the movie in minutes
- **Release Date**: When the movie is released
- **Genre**: Type of movie (Action, Drama, Comedy, etc.)
- **Rating**: Age rating (G, PG, PG-13, R, etc.)
- **Director**: Movie's director
- **Cast Members**: Main actors in the movie
- **Current Status**: Now Showing/Coming Soon

### Relationship Types:
1. **Movies to Show Times (1:N)**
   - One movie can have MANY show times
   - Each show time must be for ONE movie
   - Examples:
     * "Avengers" showing at 10:00 AM, 2:00 PM, 6:00 PM
     * Multiple halls showing same movie at different times

2. **Movies to Genres (M:N)**
   - One movie can have MANY genres
   - One genre can have MANY movies
   - Examples:
     * "Ant-Man" is both Action and Comedy
     * "Inception" is both Sci-Fi and Thriller

### Business Rules:
1. Must have valid release date
2. Duration must be specified
3. At least one genre must be assigned
4. Rating must be specified before screening

## 2. Theater Halls Entity

### Key Attributes:
- **Hall ID (PK)**: Unique identifier for each hall
- **Hall Name/Number**: Identifier displayed to customers
- **Seating Capacity**: Total number of seats
- **Screen Type**: Regular/IMAX/3D
- **Sound System**: Audio system specifications
- **Current Status**: Active/Maintenance

### Relationship Types:
1. **Halls to Seats (1:N)**
   - One hall CONTAINS many seats
   - Each seat BELONGS TO one hall
   - Examples:
     * Hall 1 has seats A1-A30, B1-B30
     * VIP Hall has special recliner seats

2. **Halls to Show Times (1:N)**
   - One hall can host MANY show times
   - Each show time uses ONE hall
   - Examples:
     * Hall 1 showing different movies throughout day
     * IMAX hall reserved for specific formats

### Business Rules:
1. Cannot exceed maximum capacity
2. Must have maintenance schedule
3. Screen type determines movie format compatibility
4. Sound system must match screen type requirements

## 3. Seats Entity

### Key Attributes:
- **Seat ID (PK)**: Unique identifier for each seat
- **Hall ID (FK)**: Reference to containing hall
- **Seat Number**: Visible identifier (e.g., A1, B2)
- **Seat Type**: Regular/VIP/Couple
- **Row Number**: Row identifier
- **Status**: Available/Occupied/Maintenance

### Relationship Types:
1. **Seats to Tickets (1:N)**
   - One seat can be used for MANY tickets (over time)
   - Each ticket must have ONE specific seat
   - Examples:
     * Seat A1 used for different shows
     * VIP seats having special pricing

2. **Seats to Halls (N:1)**
   - MANY seats belong to ONE hall
   - Each seat must be in ONE hall

### Business Rules:
1. Cannot be double-booked
2. Must have valid seat number format
3. Status must be updated in real-time
4. Maintenance status blocks booking

## 4. Show Times Entity

### Key Attributes:
- **Show ID (PK)**: Unique identifier for each show
- **Movie ID (FK)**: Reference to movie being shown
- **Hall ID (FK)**: Reference to hall being used
- **Date**: Show date
- **Start Time**: When show begins
- **End Time**: When show ends
- **Show Type**: 2D/3D/IMAX
- **Price Category**: Regular/Premium/Special
- **Available Seats**: Number of unsold seats
- **Status**: Scheduled/Cancelled/Completed

### Relationship Types:
1. **Show Times to Movies (N:1)**
   - MANY show times for ONE movie
   - Each show time has ONE movie

2. **Show Times to Tickets (1:N)**
   - One show time can have MANY tickets
   - Each ticket is for ONE show time

### Business Rules:
1. Cannot overlap in same hall
2. Must allow cleaning time between shows
3. Must match hall capabilities
4. Cannot sell more tickets than capacity

## 5. Customers Entity

### Key Attributes:
- **Customer ID (PK)**: Unique identifier for each customer
- **Name**: Customer's full name
- **Email**: Contact email
- **Phone Number**: Contact number
- **Date of Birth**: For age verification
- **Membership Status**: Regular/Premium/VIP
- **Loyalty Points**: Points accumulated
- **Registration Date**: When account was created

### Relationship Types:
1. **Customers to Tickets (1:N)**
   - One customer can have MANY tickets
   - Each ticket belongs to ONE customer

2. **Customers to Memberships (1:1)**
   - Each customer has ONE membership level
   - Each membership belongs to ONE customer

### Business Rules:
1. Must have valid email format
2. Must be 13+ for account creation
3. Points system rules
4. Membership benefits rules

## 6. Tickets Entity

### Key Attributes:
- **Ticket ID (PK)**: Unique identifier for each ticket
- **Show ID (FK)**: Reference to show time
- **Customer ID (FK)**: Reference to customer
- **Seat ID (FK)**: Reference to specific seat
- **Price**: Final ticket price
- **Purchase DateTime**: When ticket was bought
- **Payment Status**: Paid/Pending/Refunded
- **Booking Status**: Confirmed/Cancelled
- **Payment Method**: Cash/Card/Online

### Relationship Types:
1. **Tickets to Show Times (N:1)**
   - MANY tickets for ONE show time
   - Each ticket for ONE show time

2. **Tickets to Customers (N:1)**
   - MANY tickets can belong to ONE customer
   - Each ticket belongs to ONE customer

### Business Rules:
1. Cannot sell after show starts
2. Cancellation policy rules
3. Refund rules
4. Price must match show category

## 7. Staff Entity

### Key Attributes:
- **Employee ID (PK)**: Unique identifier for each staff
- **Name**: Staff member's name
- **Role**: Position/Job title
- **Contact Information**: Phone/Email
- **Schedule**: Working hours
- **Employment Status**: Active/Inactive

### Relationship Types:
1. **Staff to Halls (M:N)**
   - One staff can work in MANY halls
   - One hall can have MANY staff

2. **Staff to Shows (M:N)**
   - One staff can work MANY shows
   - One show can have MANY staff

### Business Rules:
1. Cannot exceed working hours limit
2. Must have break periods
3. Qualifications for roles
4. Schedule conflict prevention

## 8. Concessions Entity

### Key Attributes:
- **Item ID (PK)**: Unique identifier for each item
- **Item Name**: Product name
- **Category**: Food/Beverage
- **Price**: Item cost
- **Current Stock**: Available quantity
- **Status**: Available/Unavailable

### Relationship Types:
1. **Concessions to Orders (1:N)**
   - One item can be in MANY orders
   - Each order item is ONE concession

2. **Concessions to Staff (M:N)**
   - MANY items managed by MANY staff
   - Staff can manage MANY items

### Business Rules:
1. Stock level monitoring
2. Price update rules
3. Minimum stock alerts
4. Expiry date tracking

Would you like me to add any additional details to specific entities or explain any relationships in more depth?
