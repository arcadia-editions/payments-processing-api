# payments-processing-api

Payments Processing is the bounded context that owns the payment lifecycle for an
order. In Arcadia Editions it is responsible for authorization, retries, capture,
and voiding, plus the integration behavior required to work with external payment
providers.

This is a separate center of gravity from Orders Checkout because payment rules,
provider references, failure handling, and retry policies change on their own and
emit their own business facts.

## Bounded context scope

- Authorize payment when an order is created
- Retry failed payment attempts when policy allows it
- Capture payment once fulfillment has been scheduled
- Void payment when fulfillment fails or capture cannot complete

This service does not decide what is being sold, whether stock is available, or
how shipping is arranged. It only owns the payment lifecycle.

## Contents

- `domain-model.zdl`: source of truth for the payment aggregate, lifecycle, commands, and events
- `README.md`: repository overview and bounded-context explanation

## Main domain elements

- `Payment`: aggregate for provider interaction and payment state
- `PaymentsProcessingService`: commands for authorization, retry, capture, and void
- `PaymentAuthorized`, `PaymentDeclined`, `PaymentFailed`: payment decision outcomes
- `PaymentCaptured`, `PaymentCaptureFailed`, `PaymentVoided`: settlement and compensation outcomes
