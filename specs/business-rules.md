# Business Rules

Rules that apply across the whole shop. Product-specific facts live in `specs/products.md`; shipping, payment, promotion and customer details live in their own documents.

## Seller

Spreegrund Food Service GmbH, Beusselstraße 52, 10553 Berlin, Germany. VAT ID DE298765431. The shop sells only to business customers.

- Phone: +49 30 5550 1234. Email: `service@spreegrund.example`. Customer service hours: Monday to Friday, 08:00–17:00.
- Managing director: Katrin Spree. Commercial register: Amtsgericht Charlottenburg, HRB 234567 B.
- Bank account: as stated for prepayment in `payments.md`.
- Emails to customers are sent in the name of Spreegrund Food Service from `service@spreegrund.example`. Notifications for staff go to the administrator's email address (`admin.md`).

- The shop's language is English throughout, in pages, emails and documents. Dates, times and amounts are displayed consistently.
- All dates and times, including cut-offs, delivery slots, promotion periods and payment deadlines, use the Europe/Berlin time zone.

## Countries and Currencies

The shop has four country storefronts. A signed-in customer always uses the storefront of their billing country; guests can choose a storefront (default: Germany). The language is English in every storefront.

| Storefront | Currency | Serves billing countries | Shipping methods | VAT treatment |
|---|---|---|---|---|
| Germany (default) | EUR | Germany, Netherlands, Belgium | as in `shipping.md` | German VAT; EU reverse charge as below |
| Austria | EUR | Austria | EU Parcel, Warehouse Pickup | EU reverse charge as below, otherwise German VAT |
| Switzerland | CHF | Switzerland | International Freight | tax-free export delivery (0 %) |
| United Kingdom | GBP | United Kingdom | International Freight | tax-free export delivery (0 %) |

- **Base data** (catalog prices, deposits, promotion amounts and thresholds, the fees and thresholds of the Germany and Austria shipping methods, per-order budgets and credit limits) is maintained in EUR. Fixed exchange rates apply: **1 EUR = 0.95 CHF** and **1 EUR = 0.86 GBP**. Staff can change the rates; a change applies to carts from then on, never to placed orders or issued documents.
- Every **transaction** (cart, order, invoice, credit note, payment, refund, credit balance, open balance) is in the currency of the company's storefront. Conversion happens on the net unit price after customer pricing: the EUR unit price (negotiated price, or quantity price with customer-group discount, rounded to the cent as usual) is multiplied by the rate and rounded to the currency's rounding unit — 0.05 for CHF (Swiss cash rounding, half up), 0.01 for EUR and GBP. From then on every calculation uses the transaction currency: line totals, discounts, allocations, VAT, totals, fees, refunds and balances are rounded to its rounding unit wherever this document says "rounded to the cent".
- Shipping addresses must be in a country served by the company's storefront: Germany storefront → Germany, Netherlands, Belgium; Austria → Austria; Switzerland → Switzerland; United Kingdom → United Kingdom. A company's storefront cannot be changed once it has an order.
- Fixed promotion amounts, per-unit promotion amounts and all promotion thresholds (minimum goods values, the free-item threshold) are converted once from EUR at the rate and rounded to the rounding unit, for example SAVE20 = CHF 19.00 and the free-balsamic threshold = CHF 475.00. Shipping fees, free-shipping thresholds and minimum goods values of International Freight are stated in the local currency. A company's per-order budgets, credit limit, open balance and credit balance are kept in its storefront currency (EUR budgets and limits converted once at the rate).
- Orders, invoices, e-invoices, credit notes, refunds and emails of a CHF or GBP customer are in that currency. Reports show each amount in its transaction currency and its EUR equivalent at the rate that applied to the order (amount ÷ rate, rounded to the cent).
- Deliveries to Switzerland and the United Kingdom are tax-free export deliveries from Germany: 0 % VAT on the whole order, and the invoice states "Tax-free export delivery". The shop does no customs processing. Products with a deposit and chilled, frozen or fresh products are not delivered to Switzerland or the United Kingdom.
- The information pages show the seller data in every storefront, plus the storefront's currency, shipping methods and tax treatment.

## Products

- A product that has ever been ordered is never deleted, only deactivated or discontinued. SKUs are unique across all products and variants.

## Currency and Price Display

- Amounts are shown with two decimals and the symbol of their currency (€, CHF, £). Staff enter base data in euros and transaction amounts in the transaction currency, never in cents or other minor units.
- Catalog prices are net prices (excluding VAT). Because all customers are businesses, the storefront shows net prices first. Gross amounts appear in the cart, at checkout and on order documents.
- Deposits are never included in the product price. They are always shown as separate amounts.
- Products sold by weight or volume show their price per kilogram or per litre. Packaged goods with a known content also show a comparison price per kilogram, litre or piece where that is meaningful.
- Prices and stock are visible only to signed-in, approved customers. Guests can browse the catalog but see neither prices nor an add-to-cart option.

## Effective Price of a Line

The net unit price of a cart line is determined in this order:

1. If the customer has a negotiated price for the product, that price applies. It is final: no quantity price, customer-group discount or promotion is applied to that line, even if a quantity price or the group discount would result in a lower price.
2. Otherwise, the list price for the chosen packaging unit applies. If the product has quantity prices for that packaging unit, the tier is chosen by the total quantity of that packaging unit for that product in the cart.
3. The customer-group discount is then applied to that unit price, unless the product is excluded from discounts. The resulting unit price is rounded to the cent.
4. Promotions are applied last (see `discounts.md`).

## VAT

- Products carry either the reduced rate (7 %) or the standard rate (19 %), as stated in the catalog.
- The following rules on deposits and shipping are based on German VAT law.
- A deposit on packaging that goes with the goods (bottles, cans, crates, kegs, canisters, gas cylinders) is part of the product sale and has the VAT rate of the product, for example 7 % for milk and 19 % for water.
- A deposit on a transport aid (a Euro pallet) is a separate supply and always carries 19 %, even on a pallet of milk.
- Shipping fees and surcharges are part of the delivery of the goods. If all goods in the order have the same VAT rate, the shipping fees and surcharges carry that rate. If the order contains goods with several VAT rates, the shipping fees and surcharges are split across the rates in proportion to the merchandise net amount at each rate (after discounts, without deposits). Each share is rounded to the cent, and any rounding difference goes to the largest share.
- A credit for returned empty containers uses the VAT rate with which the deposit was charged.
- An order-level discount is split across VAT rates in proportion to the net amount (after automatic promotions) of the goods the discount applies to, per rate. Each share is rounded to the cent, and any rounding difference goes to the largest share.
- VAT is calculated per rate on the summed net amounts for that rate, then rounded. Each rate is shown separately in the cart, order and invoice.
- A VAT ID counts as verified only when staff have marked it as verified. A VAT ID entered at registration or changed later is unverified until staff confirm it; until then, reverse charge does not apply.
- Reverse charge: a customer outside Germany in the EU who has a verified VAT ID is charged 0 % VAT on the whole order. The invoice states "Reverse charge – VAT liability passes to the recipient". EU customers without a verified VAT ID pay German VAT.

## Units and Quantities

- The unit in which a product is priced, the unit in which it is ordered and the unit in which its stock is kept may differ. Conversions are exact: 1 kg = 1,000 g and 1 l = 1,000 ml.
- Quantities are checked against the minimum, maximum and step of the product in the unit the customer chose. A quantity is valid only if it is at least the minimum, at most the maximum, and the minimum plus a whole number of steps.
- The line total is calculated from the exact quantity converted into the price unit.
- Quantity input accepts both a decimal point and a decimal comma, so "3.15" and "3,15" mean the same.

## Rounding

- **Largest share:** wherever a rounding difference goes "to the largest share" and two or more shares are equally large, it goes to the share of the higher VAT rate; among lines, to the line listed first in the order; among payment methods, to the card.

- All money amounts are rounded to the rounding unit of their currency (0.01; 0.05 for CHF), half up.
- Line net amount = net unit price × quantity, rounded once per line.
- Percentage discounts are rounded once per discount, not per item.
- Fractional quantities (weight or volume) are kept exactly as ordered, for example 2.5 kg, and are never rounded to whole units.

## Totals

An order total consists of:

- the merchandise net total, after customer pricing and promotions
- the deposit total
- shipping fees and surcharges
- VAT per rate
- the gross total, which is the amount payable

Minimum order values, free-shipping thresholds and promotion thresholds always refer to the **merchandise net total after customer-group discounts and before promotions**. Deposits, shipping and VAT never count toward them.

## Deposits

- A deposit is charged for each returnable or single-use container as stated per product. Crate deposits are charged in addition to bottle deposits.
- Deposits are never discounted, either by customer groups or by promotions.
- Customers can return empty containers with a later delivery or at pickup. The deposit is credited when the returned empties are recorded.
- If an order line is cancelled or returned, its deposits are refunded in full.

## Stock

- Stock is kept per product in its base unit (bottle, can, piece, kilogram, litre and so on). Every packaging unit converts exactly into base units.
- Stock is reserved when an order is placed. It is released when an order or line is cancelled, and it leaves the warehouse when the goods are shipped.
- A product cannot be ordered beyond its available stock unless the catalog says it may be backordered.
- Goods from a lot past its best-before date are never sold or shipped. Lots are picked in order of the earliest best-before date first.
- A lot counts as expiring soon when its best-before date is within the next 30 days.
- A product that is out of stock and cannot be backordered stays visible but cannot be ordered.

## Variants, Related Products, Options and Bundles

- **Variants:** a product with variants (for example sizes) appears once in the catalog. Each variant has its own SKU, price and stock, and all stock and backorder rules apply per variant. The chosen variant is shown in the cart, the order and on invoices.
- **Related products:** related products are separate products, each with its own catalog entry and product page. The relation is shown on both products' pages.
- **Options:** chosen options are added to the product's net unit price and are treated as part of it. Customer-group discounts and promotions apply to the price including options, and rounding works as usual. Options have no SKU and no stock of their own; stock is counted per product unit. The same product with different option choices forms separate cart lines. The chosen options are shown in the cart, the order, on invoices and on credit notes.
- **Bundles:** a bundle is a product of its own, with its own SKU, product page and catalog entry, made of fixed quantities of other products and sold at a fixed net price. The bundle price is final: no customer-group discount, quantity price or promotion applies to it, just as for products excluded from discounts. Like those products, a bundle counts toward the goods value (minimum order values, free-shipping thresholds and the minimum goods value of promotions), but never toward the category or product thresholds of a promotion. For VAT, the bundle's net price is split across its contents in proportion to their list prices at the quantities in the bundle. Each share is rounded to the cent, and any rounding difference goes to the content item with the largest share. Each share is taxed at the VAT rate of its content item. The deposits of the contents are charged as usual, and the delivery restrictions of every content item apply to the bundle. A bundle has no stock of its own: the number of bundles available is the number of complete bundles that the sellable stock of its contents allows, and selling a bundle reduces the stock of each content item. The cart, order and invoice show the bundle as one line and list its contents.

## Assortment, Accessories and Order Lists

- **Restricted assortment:** a restricted product is visible and orderable only for the customer groups or customers named for it. For everyone else, guests included, it does not exist in the shop: it appears nowhere (categories, search, related products, accessories, bundles, quick order, order lists), and opening its product page directly behaves as if the product did not exist. All products in the category Beverages › Spirits are restricted to the groups Gastronomy and Key Account, and a bundle containing a restricted product inherits the restriction.
- **Accessories:** a product page suggests the product's accessories, each of which can be added to the cart from there. The suggestion goes one way only, and assortment restrictions apply to accessories too.
- **Order lists:** customers can keep named order lists. Each entry holds a product, its packaging unit or variant, options where applicable, and a quantity. The lists belong to the company, so all users of the same company share them. Customers can create, edit and delete lists, and add a whole list to the cart in one step. Items that are unavailable at that moment are skipped, and the customer is told which ones. The items that are added are priced like any other cart line.

## Company Roles and Approvals

- Each company user is a **company admin** or a **buyer**. Company admins manage their own company's users: they invite users by email (the invitation email contains a link to set the password), deactivate and reactivate them, set their role and set a buyer's per-order budget. Deactivated users cannot sign in.
- An order placed by a buyer whose gross total exceeds the buyer's per-order budget gets the state **awaiting approval**. Its stock is reserved and a promotion code use counts, but no payment is taken: a card is only authorised, and the bank details for prepayment are shown only after approval. The company's admins receive an email that the order awaits their approval.
- A company admin approves the order or rejects it with a reason. On approval the order becomes confirmed (pending payment for prepayment) and the buyer receives an email. On rejection the order is cancelled with the reason shown, stock and card authorisation are released, a code use is given back, and the buyer receives an email with the reason.
- Company admins have no per-order budget. Orders within the budget are processed as usual.
- **Approval comes first.** While an order awaits approval, none of the payment-method rules apply yet: nothing is confirmed, no invoice or direct debit is created, a card is only authorised, a credit balance is only reserved, and no bank details are shown. They apply from the moment of approval; the payment deadline of a prepayment order starts then. The per-order budget is compared with the order's gross total in the company's currency.

## Quotes

- A customer can request a quote for the contents of the cart, with an optional comment. Staff can also create a quote for a customer.
- Staff set a net unit price for each quoted line and an expiry date (today or later) and send the quote; the customer is notified by email. The customer's own prices are the starting point.
- Quote states: requested, offered, accepted, declined, expired. A quote expires at the end of its expiry date. Declined and expired quotes cannot be accepted, and an accepted quote can be ordered once.
- Accepting a quote puts its lines into the cart at the quoted prices and quantities. The customer finishes a normal checkout (shipping, delivery date, payment). Quoted prices are final like negotiated prices: no quantity price, customer-group discount or promotion is applied to quoted lines. Deposits, shipping and VAT apply as usual. Changing the quantity of a quoted line, or removing it, drops the quoted price for that line.

## Standing Orders

- A customer can set up a standing order: lines (product, packaging unit or variant, options, quantity), a rhythm (every week or every second week on one weekday), a start date, a shipping address, a shipping method (truck delivery with a slot, or warehouse pickup), a payment method (purchase on invoice or SEPA direct debit) and whether substitutes are acceptable.
- Every occurrence becomes a normal order at the prices valid when it is generated. The automatic generation runs daily at 06:00 and generates every occurrence whose delivery date is at most 6 days ahead and still orderable at that moment under the cut-off and delivery-day rules. Staff can run "generate due standing orders now" at any time of day; it generates exactly the occurrences that would be due by that rule at that moment. An occurrence that falls on a day without deliveries moves to the next delivery day. Each occurrence is generated at most once.
- Customers can pause and resume a standing order, skip single dates and change its lines, rhythm and settings. Changes apply to occurrences that have not been generated yet.
- If stock is insufficient, the normal backorder and substitution rules apply. If an occurrence cannot be generated (for example below the minimum order value), it is skipped. In each case the customer is notified by email.

## Payment Terms, Early-Payment Discount and Dunning

- Payment terms are set per customer; the default is "net 30 days" (due 30 days after the invoice date).
- An early-payment discount (for example 2 % within 10 days) applies when the discounted amount is received by the end of the discount period (invoice date + the stated days). The discount is calculated on the invoice gross total without deposits and their VAT, rounded to the cent. The invoice states the discount, the amount payable within the discount period and the last day of that period.
- Recording payments that add up to the discounted amount within the discount period settles the invoice in full. The discount reduces the taxable amounts: it is split across the VAT rates in proportion to the invoice's gross amounts per rate (without deposits), each share rounded with any rounding difference on the largest share, and the VAT correction per rate is share × rate ÷ (100 + rate), rounded. For reverse-charge and export invoices the discount carries no VAT correction. Staff see the discount and its VAT correction per rate with the payment. A later credit note for an invoice settled with an early-payment discount reduces only the credited goods (their net plus VAT, without deposits and their VAT, and without shipping) by the same percentage, rounded; deposits are credited in full; shipping is credited only when it is refunded at all (whole order returned because of a seller error), and then reduced by the same percentage. A credit note never exceeds the money collected for the credited lines. Example: an invoice of €142.98 (goods €126.37 gross, truck shipping) paid with 2 % discount; all goods returned for a quality complaint → credit €126.37 − €2.53 = €123.84, shipping retained.
- Staff can record partial payments. The invoice then shows the remaining amount, its payment status is "partially paid", and the open balance falls by the amount received.
- Dunning: staff start a dunning run. For every unpaid invoice past its due date the run creates the highest level that is due and has not been created yet: a payment reminder from due date + 7 days (no fee), a first dunning notice from due date + 14 days (fee €5.00) and a second dunning notice from due date + 28 days (fee €10.00). Levels that were skipped are not charged. Dunning fees carry no VAT and are added to the customer's open balance. Each notice is a document with the invoice number, the amount due, the fee and a new deadline (run date + 7 days), and is sent to the customer by email.
- A customer with an invoice at the second dunning level loses purchase on invoice automatically until staff restore it.

## Order Workflows

- Each order follows one order-processing workflow. A workflow defines its states, the transitions between them, the conditions a transition needs (for example "payment received", "approval granted", "all lines picked", "cold-chain check done", "export documents ready") and the actions that run automatically when a state is entered (for example sending an email, reserving or releasing stock, creating an invoice, notifying staff).
- Rules decide which workflow an order follows, checked in this order; the first that matches applies:
  1. **Export** — shipping address in Switzerland or the United Kingdom: adds the state "export documents ready" before shipping; shipping needs the condition "export documents ready"; entering that state notifies staff by email.
  2. **Chilled goods** — the order contains a chilled, frozen or fresh product: adds the state "cold-chain check" before shipping; shipping needs the condition "cold-chain check done".
  3. **Prepayment** — payment by prepayment: starts in "pending payment"; picking needs the condition "payment received".
  4. **Standard** — all other orders: the states in "Order States" above.
- The Standard workflow is the one described under "Order States"; the other three extend it. Its automatic actions: on entering "confirmed", send the order confirmation; on entering "cancelled", release stock and the card authorisation and send the cancellation email. **Every shipment** (an event that can happen several times per order) creates its invoice, settles its amount (see `payments.md`) and sends the shipping email, whatever state the order is in.
- Staff can change workflows and rules in the back-office. A change applies only to orders that enter the workflow afterwards; orders already in it keep the version they started with.
- **Diagrams:** every workflow, every fulfillment process (standard warehouse fulfillment, multi-warehouse split, cross-docking, drop-shipping) and the payment flow of every payment method is shown in the back-office as a diagram: steps or states as boxes, transitions as arrows, and the conditions and automatic actions written on them. On an order's page, its workflow diagram highlights the order's current state.
- **Visual editing:** staff edit a workflow on its diagram: add, remove and rename steps, add and remove transitions, attach conditions and automatic actions, and set the rules that decide which orders use it. Saving is refused with a message if the workflow has no start state, no end state, a step that cannot be reached, or a step from which no end state can be reached.
- **Versions:** every saved change creates a new version of the workflow. Running orders keep the version they started with; new orders use the latest version. Staff can see the version history and compare two versions.
- The seeded Standard workflow has these states: awaiting approval, pending payment, confirmed, partially shipped, shipped, delivered, completed, cancelled. Its transitions: awaiting approval → confirmed, pending payment or cancelled; pending payment → confirmed or cancelled; confirmed → partially shipped, shipped or cancelled; partially shipped → partially shipped (a further partial shipment) or shipped; shipped → delivered; delivered → completed.
- Every order shows its workflow, current state, the transitions that are possible now (only those whose conditions hold) and the full history.

## Catch-Weight Products

Some products are ordered per piece but charged by weight (for example a whole cheese wheel). The cart and order use the estimated weight. When the order is packed, the actual weight is recorded and the line is recalculated. The invoice shows the actual weight and charges the line at that weight, so any difference from the estimate is charged or credited. The price unit is the kilogram: the customer-group discount is applied to the price per kilogram and rounded; the estimated line = estimated weight × that price, the invoiced line = actual weight × that price, each rounded once.

## Order Numbers and Documents

- Order numbers follow the format `SG-` plus a five-digit sequence and are never reused. The first order is `SG-10001`.
- Invoice numbers follow the format `INV-` plus the year plus a five-digit sequence, for example `INV-2026-00001`. Every shipment produces its own invoice when it is shipped. The invoice covers exactly the goods in that shipment and their deposits. The first invoice of an order also carries the shipping fees and surcharges. An order-level discount (promotion code) is carried by the lines it applies to: each eligible line has a fixed discount share (its part of the code discount, at its VAT rate, frozen when the order is placed). An invoice carries, for every line it contains, that line's share for the invoiced quantity (rounded; the last invoice of the line takes the rest). Lines not eligible for the code (negotiated, quoted, excluded, bundles) never carry a discount. VAT is calculated per invoice; the last invoice of the order is adjusted by any VAT rounding difference so that all invoices together equal the order's totals.
- An invoice lists each line with its quantity, unit price and net amount, each applied promotion with its discount, the deposit total, shipping fees and surcharges, the net amount and VAT for each VAT rate, and the gross total. A credit note shows the same breakdown for the refunded amounts.
- Every invoice also shows the seller's name, address and VAT ID, the customer's billing address and VAT ID, the invoice date, the delivery date, the order number and purchase order reference, the payment method and, for purchase on invoice, the due date.
- Credit notes follow the format `CN-` plus the year plus a five-digit sequence.
- Every invoice and credit note is also available as an electronic invoice in the German/EU standard XRechnung (EN 16931). It contains the seller and the buyer with their VAT IDs, the line items, the deposits, the VAT breakdown per rate, the totals, the payment terms and the due date. A reverse-charge invoice carries the VAT category for reverse charge with its exemption reason, and an export invoice the category for tax-free export with its reason. A matching PDF with embedded data (ZUGFeRD / Factur-X) may be offered in addition. Customers and staff can download the electronic invoice next to the printable invoice.
- Quote numbers follow the format `SQ-` plus a five-digit sequence and are never reused. The first quote is `SQ-10001`.
- An order keeps a frozen copy of the prices, VAT rates, deposits, addresses and promotion that applied when it was placed. Later changes to products, prices or promotions do not change existing orders.

## Order States

| State | Meaning |
|---|---|
| Awaiting approval | Placed by a buyer above their per-order budget; waiting for a company admin's decision |
| Pending payment | Placed, waiting for payment, for example prepayment |
| Confirmed | Accepted and ready to be picked |
| Partially shipped | Some lines or quantities have shipped; the rest is still open or backordered |
| Shipped | Everything that is going to ship has shipped |
| Delivered | The customer has received the goods |
| Completed | Delivered and fully paid; no returns open |
| Cancelled | The whole order was cancelled before anything shipped; stock released and payment released or refunded |

Payment status is tracked separately: open, authorised, partially paid, paid, released, partially refunded, refunded, charged back or failed. Every state change is recorded with its time and the person who made it.

An order in "pending payment" cannot be picked or shipped until the payment has been recorded. Staff mark shipments as delivered. An order becomes "delivered" when every quantity that has not been cancelled has shipped and all its shipments are delivered. It becomes "completed" automatically once it is also fully paid and no return is open.

## Cancellations, Returns and Refunds

### Cancellations

- As long as nothing of an order has shipped, the customer can cancel the whole order or single unshipped lines or quantities online. After the first shipment, only staff can cancel unshipped lines or quantities. Shipped goods are never cancelled, only returned. Cancelling lines or quantities is a line event, not an order state: when nothing remains to ship after such a cancellation, the order becomes "shipped" (or stays "delivered"/"completed" if it already was); an order is "cancelled" only if all of it was cancelled before anything shipped.
- A cancellation releases the reserved stock in the warehouse it was reserved in. For a product sourced on demand, an open supplier purchase order is reduced accordingly; goods that have already been received go into stock at WH-BER.
- After a cancellation, the order's promotions are recalculated as if the order had been placed with the remaining lines (shipped and unshipped): a promotion code whose minimum goods value is no longer reached is removed, percentage and per-unit discounts are recalculated, automatic promotions are recalculated, and a free item that has not shipped is removed. **Discounts on goods that have already been invoiced are kept**: the recalculation changes only the discounts of lines and quantities not yet invoiced. Shipping fees and surcharges are never added or increased by a cancellation; they are reduced only when an item that caused a surcharge is cancelled. Deposits of cancelled lines are dropped, and VAT is recalculated per rate.
- Payment effects of a cancellation (card): let *card due* = remaining gross total − credit balance applied to the order (credit no longer needed is released back to the credit balance). The open authorisation becomes max(0, card due − card amounts already captured). Card amounts already captured above the card due are refunded to the card: refund = max(0, captured − card due). Examples: two tins (€90.95), €10.00 credit, nothing shipped, one tin cancelled → open authorisation €45.48 − €10.00 = €35.48, refund €0. Three tins (€136.43), €10.00 credit, one tin shipped and settled by the €10.00 credit and €35.48 card, one unshipped tin cancelled → card due €90.95 − €10.00 = €80.95, open authorisation €80.95 − €35.48 = €45.47, refund €0. Same order, both unshipped tins cancelled → only the shipped tin (€45.48) remains; card due €35.48, open authorisation €0, refund max(0, €35.48 − €35.48) = €0. A prepayment or other payment above the new total becomes credit balance; for purchase on invoice only the shipped goods are ever invoiced.

### Returns

- Customers can request a return for shipped goods within 14 days of delivery: single lines, quantities, or for catch-weight products a weight. Chilled, frozen and fresh products can be returned only for quality complaints. Bundles can be returned only as whole bundles, never as single contents.
- Every return names a reason with its own outcome:
  - **Quality complaint** and **damaged in transit:** refund of the goods including their deposits; return shipping is free (the goods are collected with the next delivery or at pickup). For damage in transit, staff add a carrier claim note.
  - **Ordered by mistake:** a restocking fee of 10 % of the returned goods' net amount (after their share of discounts, rounded to the cent) is deducted before VAT; deposits are refunded in full; the customer returns the goods at their own cost.
- Empty containers on their own are not a return: staff record them as returned empties (see Deposits).
- Staff decide each return request (approve, partially approve or reject). When the goods arrive, staff inspect each line and either restock it to a chosen warehouse and lot or write it off.
- Instead of a refund, staff can send a replacement shipment of the same goods at no charge. The order's totals stay unchanged and no credit note is issued.

### Refunds

- A refund covers the net price actually paid for the returned items, after their share of any order discount (promotions are not recalculated for returns), minus any restocking fee, plus their deposits and VAT per rate, using the order's VAT treatment (0 % for reverse-charge and export orders; Euro-pallet deposits at 19 %). A catch-weight return is refunded in proportion to the returned weight: returned kg ÷ invoiced kg × the amount paid for the line after discounts. For products with a volume deposit (canisters), the return states the number of containers returned, and their deposits are refunded per container. Shipping is refunded only when the whole order is returned because of a seller error.
- Refunds go back through the payment methods that were used (see `payments.md`), in the order's currency, or reduce the open balance for purchase on invoice. Each refund produces a credit note with the VAT per rate.
- **Cash refunds** (money paid back by card, bank transfer or to the credit balance) never exceed the amount collected for the refunded lines, and all cash refunds of an order never exceed the amount collected for it. **Receivable credits** (credit notes for invoices not yet paid) reduce the open amount of the invoice; they never exceed the invoiced amount, and any part above the open amount becomes credit balance.
- **Residuals:** when the last remaining quantity of a line is refunded, its refund entitlement (net after discounts, before any restocking fee) is what was paid for the line minus the entitlements of its earlier refunds; restocking fees are then deducted per refund as usual and are never refunded later. Deposits are refunded only for containers actually returned (unreturned canisters are never refunded). The VAT of that last refund is the VAT per rate on everything credited for the line in all its refunds (net after retained fees plus the deposits actually credited) minus the VAT refunded for it before, whatever the return reasons were. Example: one of two tins (€42.50 net each, 7 %) returned by mistake (€38.25 + €2.68 = €40.93), the other for a quality complaint: VAT on €80.75 is €5.65, so the second refund is €42.50 + €2.97 = €45.47 (total €86.40). Example: two tins at €42.50 net each, both returned one at a time as ordered by mistake: each refund is €38.25 net + €2.68 VAT = €40.93, together €81.86 (fees €4.25 + €4.25 retained).
