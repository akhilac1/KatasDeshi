# Architecture Decision Record - Broadcast order cancellation event.

# Status
Proposed

# Context
An order can be cancelled either by user or by system. System can cancel the order in various scenarios like food expiry, fridge going out of order, error during Purchase transaction or any other system or infra failure etc.

Any order cancellation has to be communicated to all relevant services and each service will have to take the relevant action to achieve eventual system consistency for a cancelled order like:

- PaymentService will do payment reversal for a given order cancellation.
- InventoryService will take the required action to compensate the transaction as needed.
- Asynchronous notification to the user for order cancellation.
- Order Service will mark the order cancelled.
- Coupon/Promotion Service will roll back the coupon applied.
- KitchenService, DeviceManagementService etc.
- TelemetryService will record the order failure.

This communication can either be done synchronously or asynchronously.

# Decision
Event driven architecture should be applied to solve this problem. The order cancellation will be broadcasted (pub-sub) as an event and services participating in order completion will subscribe to these events and take necessary action.

No orchestration is needed as event is published once. Each consumer subscribes to the event and knows what needs to be done.

### Performant
Because every subscriber service will act in parallel. User get notified faster and can make other food arrangements quickly.

### Reliability 
Event queues and topics are very reliable as compared to in memory data. Generally subscriber will mark an event as completed only after successful processing of the event, so If a process crashes in between then event will still be there in the Subscription queue and can be reprocessed later.

### Evolutionary 
New Services can subscribe to this event in future as needed without any change to other services.

# Consequences

### Eventual Consistency 

As the system is distributed so getting to a consistent state will take time and might slow down due to error in any of the service.

### Error handling

Error handling becomes complex in event-driven architecture. Below are the ways we will solve for it.
- Use Error queues
- Persisted messages Topics
- Synchronous send - Synchronous send does a blocking wait in the message producer until the broker has acknowledged that the message has been persisted.
- Client Acknowledge mode - with message lock duration.
