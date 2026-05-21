# Payments Processing

## Description

Payments Processing is the bounded context that owns the money side of an
Arcadia Editions order. It handles authorization, retries, capture, voiding, and
the integration details required to work with external payment providers.

It gives the rest of the platform trustworthy payment outcomes without owning the
order, stock, or shipping domains.

## Scope

- Authorize payment when an order is created
- Retry failed payment attempts when policy allows it
- Capture payment once fulfillment has been scheduled
- Void payment when fulfillment fails or capture cannot complete
- Own provider references, failure reasons, and payment attempt tracking

## Main domain elements

- `Payment`: aggregate for provider interaction and payment state
- `PaymentsProcessingService`: commands for authorization, retry, capture, and void
- `PaymentAuthorized`: event announcing successful authorization
- `PaymentDeclined`: event announcing a provider rejection
- `PaymentFailed`: event announcing a technical or operational authorization failure
- `PaymentCaptured`: event announcing funds were captured successfully
- `PaymentCaptureFailed`: event announcing capture did not complete
- `PaymentVoided`: event announcing the payment was compensated
