# Architecture Decision Record - Asynchronous Order Processing

# Status
Proposed

# Context
Order confirmation is a complex workflow, involving many internal services and external systems to work in cohesion. Any failures midway or delays in any of the service will impact performace and availability of the system negatively and cause poor user experience.

# Decision

When the user places an order, accurate price, including tax should be billed to the user and the order should be queued for processing. A notification should be posted to the user, clearly indicating that the order is pending for confirmation. 

Queued Order should be retireved in the same sequence that it was queued [ FIFO ] and validated to ensure food is available both in central inventory and also at the location via the third-party Fridge API/PoS interface. Post confirmation of availability, food should be blocked for the user, against a specific Order code. After successful reservation of food, inventory should be updated and notification should be sent to the PoS/Fridge with details of the order code. 

Post completion of all of the above steps, the user should be sent a confirmation of the order.
In case of failure of any of the above, Order should be immediately cancelled, with payment refund intiated. User should be notified of the cancellation and SLA for completing the refund.

# Consequences
User wait time will be high in case of network delays or errors in any of the dependent systems. Order processing time should vbe strictly constrained to an acceptable interval of 2 min and cancellation should be initiated.
