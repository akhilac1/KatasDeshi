# Requirements Specification for Farmacy Foods
 - Italics indicate assumptions
## VISION 
Farmacy Food is a tech-enabled healthy food startup that takes the “Let food be thy medicine” quote literally and creates tasty meals around peoples’ dietary needs and active lifestyles to support their overall well-being. Our mission is to make health and wellness radically affordable and accessible.

### Out of Scope
- Sourcing of supplies for the kitchen 
- logistics for food distribution
- Back-office activities of Farmacy Foods is not scoped in. 
### Actors 
- Consumers 
- Kiosk Operators
- Smart Fridges
- Point of Sale devices [POS]
- Kitchen
- System

## Architectural Characteristics
1.	Food is available and accessible round the clock : **Availability**
2.	Consumers can select a meal of their choice via web or mobile : **Performance**
3.	Process personal data and health data of the consumers and recommend food : **Data Privacy, Security, Compliance** with Health data processing standards
4.	Integration with Smart Fridge, PoS at Kiosk, Partner Systems for promotion management, partner vendors - **Interoperability**
5.	Expand to other locations and larger user base - **Scalability** 

### Domain Requirements
1.   Consumers can browse and choose the food items 
        * Each PoS/Fridge has its own unique inventory
        * Users will pick up food and hence need to know where the nearest fridge is and what items are available
        * If the user wants a specific item, then the system should recommend the nearest fridge
    
2.	Consumer should be able to place and order for food
    *	User should be able to review the health aspects of the food
    *	Choose food item
    *	Quantity
3.	Consumer should be able to pay for the food
    *	Users can pay by cash at Point of Sale [PoS] – get clarification
    *	Users can pay by Card at PoS or Fridge
    *	Users can pay using virtual money at PoS or Fridge
    *	Users can redeem third-party coupons at PoS or Fridge
    
4. 	Consumer should be able to pick-up the food
    *	Smart Fridge should be able to dispense the food to the user
    
5. 	Consumers can get subsidy based on their profile [ college students ] – variable pricing for the same item based on user profile
    *	Power users – Collect health information [ Future ]

6.	System should capture user feedback
7.   Event based periodic asynchronous update of the inventory
8.	User gets notified of promotions – Free coupon for anyone moving newly into the apartment community
9.	Third party can donate food to specific groups [ philanthropic mode ] – where anyone in the area, specific demography of people [ low income groups, college kids etc.
10.	Periodic asynchronous manual update of inventory at Kiosk / Automatic inventory update based on sales [?]
11.	Long Term : Integration with 3rd party food suppliers / vendors [ broadcast inventory details to registered users]
12.	Create food recommendations based on
    *	Health goals – Integrate with third party SMEs to correlate recipes with health goals
    *	Purchase History – Predict probable interests in food based on past purchases and feedback
