# Architecture Decision Record - Broadcast User Login 

# Status
Proposed

# Context
The User Service, upon successful authentication and authorization of the user, should load the default, location specific menu and broadcast the login event for downstream services to process. 

# Decision

User location will change continuously and hence the computation of customized menu and applicable offers will cause latency in responding to the user. 

Post successful authentication and authorization of the user,  user preferences, feedback and purchase history along with location specific promotions and offers will be processed to generate a ranked custom recommendation of food items for the user.

We will use asynchronous processing to decouple basic feature - menu display and order processing from rich nice-to-have features like customized menu and promotional offers to ensure that we adhere to the architectural requirement of performance and availability.

Since the application is based on micro-frontend architecture pattern, promotions and recommendations will load independently, without disrupting users ability to peruse the default menu.


# Consequences
Depending on the complexity of the data set, pushing recommendations to the user might be delayed. However, promotion code will be applied as appropriate during checkout and item will be priced accurately. User will be notified of the same, along with order confirmation.
