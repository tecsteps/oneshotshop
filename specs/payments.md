# Payment Methods

All payment methods are simulated. No real payment provider is involved, and no real money or card data is processed.

## 1. Purchase on Invoice

- Only for customers who have been approved for invoice payment (see `customers.md`).
- Payment is due according to the customer's payment terms (default: 30 days after the invoice date; see `business-rules.md` for early-payment discounts, partial payments and dunning).
- **Credit limit:** the customer's open balance plus the gross total of the new order must not exceed their credit limit. Otherwise this payment method cannot be used for the order.
- The order is confirmed immediately. Its payment status stays "open" until staff record that the payment was received.

## 2. Credit Card (Test)

The customer enters a card number, an expiry date in the future and a three-digit security code. The outcome depends only on the card number:

| Card number | Outcome |
|---|---|
| 4242 4242 4242 4242 | Approved |
| 5555 5555 5555 4444 | Approved |
| 4000 0000 0000 0002 | Declined — "Card declined" |
| 4000 0000 0000 9995 | Declined — "Insufficient funds" |
| 4000 0000 0000 0259 | Approved; a chargeback is reported right after the first capture |
| 4000 0000 0000 0069 | Approved; the authorisation expires immediately, so the first capture fails |

Any other card number is rejected as invalid.

- An approved card payment is **authorised** for the card-funded part of the order (the gross total minus any credit balance used) when the order is placed: the order is confirmed and its payment status is "authorised". Nothing is charged yet.
- The amount is **captured** shipment by shipment: each shipment's invoice is settled first from the credit balance used for the order (as far as it is not yet allocated), and the rest is captured from the card. When everything has been settled, the payment status is "paid"; after a partial shipment it is "partially paid".
- A capture may exceed the remaining authorised amount by at most 15 % (for example for catch-weight products, which are authorised at the estimated total and captured at the actual weight). A larger capture needs a new authorisation: the order is flagged "payment action required" and the customer is asked by email to pay the difference by card.
- An authorisation is valid for 7 days. If it has expired when goods ship, the capture fails, the order is flagged "payment action required", shipping is held, and the customer is asked by email to authorise the card again.
- Cancelling an order or unshipped lines recalculates the card part: card due = remaining gross total − credit balance applied (credit no longer needed is released back to the credit balance); open authorisation = max(0, card due − card amounts already captured); card refund = max(0, card amounts already captured − card due). Payment status "released" when nothing was captured and nothing stays authorised. The worked examples are in `business-rules.md` (Cancellations, Returns and Refunds). Refunds of captured amounts go back to the card.
- A chargeback reverses the captured amount: the payment status becomes "charged back", the order is flagged, and staff are notified by email.
- A declined payment does not create a confirmed order. The cart stays intact, and the customer can try again or choose another method.

## 3. SEPA Direct Debit (Test)

- The customer enters an account holder name and an IBAN and accepts a direct-debit mandate.
- Only for orders in EUR.
- The IBAN must have a valid checksum. `DE89 3704 0044 0532 0130 00` and `AT61 1904 3002 3457 3201` are valid test IBANs. `DE00 1234 5678 9012 3456 78` is invalid and must be rejected.
- The order is confirmed immediately with payment status "open". Staff mark the payment as collected.

## 4. Prepayment by Bank Transfer

- After placing the order, the customer sees the seller's bank details and the order number to use as the payment reference:
  - Account holder: Spreegrund Food Service GmbH
  - IBAN: DE46 1005 0000 1234 5678 90
  - BIC: BELADEBEXXX
- The order is created with the state "pending payment" and its stock is reserved.
- Staff record incoming bank transfers (amount, currency, payer, reference text, date). A transfer whose reference contains the number of an unpaid prepayment order in the transfer's currency (not awaiting approval) is matched to that order automatically:
  - **Exact amount:** the order is paid and becomes "confirmed".
  - **Overpayment:** the order is paid, and the excess is added to the customer's credit balance.
  - **Underpayment:** the order stays "pending payment" and shows the remaining amount. It is confirmed when the remainder arrives, or when staff accept the difference (the accepted difference is recorded as a write-off).
  - **Several order numbers in the reference:** if all named orders belong to the same company and currency, the amount is applied to them in the order they are named, each up to its open amount, and any remainder becomes credit balance; otherwise the transfer goes to the unmatched payments.
  - **Duplicate payment** for an order that is already paid: the whole amount becomes credit balance.
  - **No usable reference:** the transfer goes to the list of unmatched payments, where staff match it to an order (then the rules above apply) or to a customer's credit balance.
- An order that is still unpaid 7 days after it was placed (or after its approval, for an order that needed approval) is cancelled automatically, and its stock is released.

## 5. Cash on Pickup

- Available only when the shipping method is Warehouse Pickup.
- The order is confirmed immediately with payment status "open". Staff mark it as paid when the goods are handed over.

## Customer Credit Balance

- Each customer company has a credit balance in its storefront's currency. It grows through overpayments, duplicate payments, cancellations of prepaid lines and refunds credited to it, and it shrinks when it is used or paid out.
- At checkout, a customer with a credit balance can use it: it pays the order first, up to the order's gross total, and the rest is paid with another allowed method (split payment). The credit balance used is taken from the balance when the order is confirmed; while an order awaits approval it is only reserved.
- Staff can pay out a credit balance to the customer's bank account; this is recorded as a payment event.

## General Rules

- At checkout, only the payment methods that are allowed for this customer, shipping method and order total are offered.
- Every payment attempt is recorded with its method, amount, result and time, including declined attempts.
- Refunds go back through the methods that were used for payment. If an order was paid with several methods (for example credit balance and card), a refund is split across them in proportion to the amounts they paid, each share rounded to the cent (0.05 for CHF) with any rounding difference on the largest share; the credit-balance share is credited back to the credit balance. Refunds on purchase on invoice reduce the customer's open balance. Payments and refunds are always in the order's currency.
- The back-office has a payments ledger with every payment event: date, order, customer, method, event (authorisation, capture, release, refund, chargeback, transfer received, matched, credit used, payout), amount and currency.
- The full card number and security code are never stored or shown again after submission. Orders and payment records show only the card's last four digits.
- A customer can see the bank details and payment reference of an unpaid prepayment order at any time in their account.
