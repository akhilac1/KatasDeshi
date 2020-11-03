# KatasDeshi

 This is a repository of design specifications for Farmacy Foods - a tech. enabled food startup
 
 These specifications were built for Oreilly Architectural Katas 2020.


## Please refer to the Architecture folder for the artifacts created by the team.

## Problem / Kata

### Farmacy Food
### Founder: Kwaku Osei

Farmacy Food is a tech-enabled healthy food startup that takes the “Let food be thy medicine” quote literally and creates tasty meals around peoples’ dietary needs and active lifestyles to support their overall well-being. Our mission is to make health and wellness radically affordable and accessible.
Farmacy Food mission: https://www.youtube.com/watch?v=9aSLSVAIkoM
Farmacy Food website: https://www.farmacyfood.com/d: Food as Medicine Actualized - Kwaku Osei - Farms, Food & Health Conference 2019


A “ghost kitchen” needs a system to allow users to have visibility of what items are available, purchase, and pick up items at any one of their points of sale.

### Users
- dozens of automated fridges 
- representative run kiosks
- thousands of customers

# Requirements:
- Must integrate with 3rd party smart fridges to obtain inventory and purchase activity
- Smart Fridges Produce item inventory levels and purchases. The smart fridges have a cloud based management system that handles communication with the Smart Fridge so obtaining this data would be through an API.
- Must integrate with point of sale system at kiosks
- The Kiosk is a sublet space inside another business where we will sell our product but have an employee to handle the transactions through a point of sale. The same data should be accessible through the POS systems API’s.
- Mobile  Web accessible
- Support providing feedback on items of verified purchases and in app surveys
- Accept coupons and promotional pricing
- Send inventory updates to central kitchen

# Long term Goals
- Long term would like to allow multiple vendors to offer items through points of sale
- Wants to harvest data to provide personalized recommendations based on users health goals, purchase history, and item ratings

 ## Our Approach:
 1. Synthesize the requirement specification to identify the actors and domains
 2. Identify the architectural characteristics for the system
 3. Create a high level breakdown of features for each domain
 3. Group features into services
 4. Define trade-offs for each service
 5. Design the service - identify technology components for the service
 6. Prototype the service 
 7. Incrementally deploy and test in production by continuously monitoring the telemetry data
 8. Enrich the features 

For the purpose of this Kata, we will work through steps 1 - 4

