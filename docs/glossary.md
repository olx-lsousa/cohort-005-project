# Glossary

The words this project uses for its domain. Use the preferred term in UI copy, emails, and code. Do not use the words listed under "Avoid".

## Refunds

### Refund request

A learner's request to get their money back for a course purchase. The learner writes a reason, and a person on the team approves or declines it. It is stored as a row in the `refunds` table, and its status is one of `requested`, `approved` or `declined` (`RefundStatus`).

- **In the UI:** the course page shows a "Request a refund" button. The settings page lists open requests under "Refund requests", each with a "Refund requested" badge.
- **In code:** `refunds`, `RefundStatus`, `getRefundOffer`, `pendingRefundRequests`, the `/courses/:slug/refund` route.
- **Avoid:**
  - "cancel my purchase" or "cancellation": these suggest something instant and automatic, but every request is reviewed and can be declined.
  - "reversal": payment-processor jargon for voiding a payment before it settles.
  - "chargeback": see below.

### Refund

The money returned to the learner once a refund request is approved. It is recorded in `refunds.amountRefunded` and is null until approval. A declined request refunds nothing.

### Refund window

The number of calendar days after a purchase in which a learner can make a refund request (`REFUND_WINDOW_DAYS`, 14 days). It is counted in whole days, so the learner keeps all of the last day.

### Chargeback

Reserved for a dispute that the cardholder raises with their bank. The bank pulls the money back from us without our approval. This project does not handle chargebacks today. Do not use the word for refund requests.
