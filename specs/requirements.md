# Requirements

Spreegrund Food Service is a B2B wholesaler of food, beverages and kitchen supplies for restaurants, cafés, hotels and retailers. This document lists the business capabilities the webshop must support. It describes what is needed, not how to build it.

Related business data and rules:

- `specs/products.md` and `specs/images/` — products
- `specs/customers.md` — customer accounts and groups
- `specs/admin.md` — administrator account
- `specs/discounts.md` — promotions
- `specs/shipping.md` — shipping methods and delivery restrictions
- `specs/payments.md` — payment methods
- `specs/business-rules.md` — VAT, rounding, prices, stock, order states and refunds

---

## Storefront

1. Visitors can browse a clean, professional storefront that works on desktop, tablet and mobile screens down to 390 pixels wide, without horizontal scrolling.
2. The home page highlights categories, featured products and active promotions.
3. Every product has its own page with name, images, description, SKU, packaging options, VAT rate, deposit information and availability.
4. Guests can browse the catalog but see neither prices nor an order option. They are invited to sign in or register.
5. Signed-in, approved customers see their own prices. These include customer-group discounts, negotiated prices and quantity prices.
6. Prices are shown as net prices, clearly labelled as "excl. VAT", with deposits shown separately. Base data is maintained in euros; every amount a customer or staff member sees or enters in a transaction is in that transaction's currency, with its currency symbol, never in cents or other minor units, and formatted the same way everywhere with its net or gross label and the unit it refers to. Percentages and physical units are always labelled.
7. Products sold by weight or volume show their price per kilogram or litre. Packaged goods show a comparison unit price where that is meaningful. The packaging overview on the product page shows each packaging unit with its price per unit and its comparison unit price.
8. Availability is clearly communicated with one of these labels: in stock, low stock, out of stock, available for backorder, or ships in a stated number of working days (for products sourced on demand).
9. Discontinued products are not shown in the storefront.
10. The storefront, checkout and admin area meet common accessibility expectations: keyboard navigation with a visible focus, meaningful labels, text alternatives for images, sufficient contrast and a sensible heading structure. Form errors are announced and tied to their field, dialogs can be operated and closed with the keyboard, and states are never shown by colour alone.

## Categories

11. Products are organised in a category tree with main categories and subcategories.
12. Customers can browse a category and see the products in it and in all its subcategories, with breadcrumbs that show where they are in the category tree.
13. Category pages can be sorted by name and price, and filtered by availability and temperature class. They show the number of matching products, show active filters so they can be removed one by one or all at once, and are paginated.

## Search

14. Customers can search products by name, SKU and description.
15. Search tolerates partial words and is not case-sensitive. "pils" finds Pilsner, and "wat-001" finds WAT-001.
16. Search results can be filtered by category and availability. A search without results says so and suggests alternatives, such as categories or popular products.

## Customer Accounts

17. Businesses can register with company name, contact person, email, password, VAT ID, billing address and shipping address.
18. New registrations must be approved by staff before the customer can see prices or order.
19. Blocked customers cannot sign in.
20. Customers can sign in, sign out and reset a forgotten password.
21. One company can have several users who share the same prices, addresses and order history.
22. Customers can manage several shipping addresses and choose one at checkout. The billing address is maintained per company.
23. Customers can see their order history, the details and status of each order, their invoices and credit notes.
24. Customers can reorder a previous order in one step. Items that are unavailable are reported.
25. Customers can see their customer group, their payment terms and, if they buy on invoice, their credit limit and open balance.

## Cart

26. Customers can add products to the cart in any packaging unit offered for that product.
27. Customers can change quantities, switch packaging units and remove lines in the cart.
28. The cart validates quantities against minimum quantities, quantity steps, per-order limits and available stock, and explains any problem.
29. The cart shows for every line the unit price, quantity, packaging unit, line total and deposit. It also shows the merchandise total, discounts, deposits, shipping estimate, VAT per rate and gross total.
30. The cart persists across sessions and devices for a signed-in customer.
31. Customers can apply and remove a promotion code in the cart.
32. When prices, stock or promotion eligibility change while items are in the cart, the cart updates and tells the customer what changed.
33. Customers can quickly add products to the cart by entering SKUs and quantities (quick order).

## Checkout

34. Checkout is a distinct, linear sequence after the cart: shipping address and shipping method, delivery date or slot, payment method, and a final review with a read-only summary before the order is placed. It does not repeat the editable cart. An order summary with the current totals stays visible. Completed steps can be reviewed and changed, and entries are kept when a step has to be corrected.
35. Only shipping methods that are allowed for the shipping address and the cart contents are offered. If a method is blocked, checkout explains why.
36. Checkout enforces minimum order values for the chosen shipping method.
37. Customers can choose a delivery date and slot for truck delivery, and a pickup date for warehouse pickup.
38. Customers can add a purchase order reference and a delivery note to the order.
39. For each line, customers can say whether a substitute product is acceptable if the item cannot be supplied.
40. Only payment methods that are allowed for the customer, shipping method and order total are offered.
41. The final review shows all lines, deposits, discounts, shipping, VAT per rate and the gross total before the order is placed.
42. A failed payment does not create a confirmed order. The customer can retry with another method without losing the cart.
43. After a successful order, the customer sees a confirmation with the order number, the ordered items and totals, the delivery or pickup date and slot, and, for prepayment, the bank details and payment reference. The customer also receives a confirmation email with the same information.

## Orders

44. Every order gets a unique, sequential order number.
45. An order keeps the prices, VAT, deposits, discounts, addresses and terms that applied when it was placed, regardless of later changes.
46. Customers can cancel their own order online as long as nothing has shipped. Before anything has shipped, customers can also cancel single lines or quantities online.
47. Customers receive email notifications when their order is confirmed, paid (prepayment), shipped, partially shipped, cancelled or refunded, and when a return request is decided. Each email names the order number and shows the affected items, quantities and amounts, plus delivery or tracking details where relevant. Emails come from Spreegrund Food Service and include its contact details.
48. An invoice is created for each shipment and covers the goods shipped in it. It shows net amounts, VAT per rate, deposits and, where relevant, the reverse-charge note.

## Admin

49. Staff sign in to a separate admin area that customers cannot access, on a plain, neutral sign-in screen. Staff and customer sessions are independent: a staff page never shows a customer's company, cart or storefront elements. The admin area is a dedicated back-office with its own layout and navigation, without the storefront's header, search, cart or footer, and with list views that can be searched, filtered, sorted and paginated. The back-office reaches the quality of leading commerce back-offices: a global search across orders, customers, products and quotes is available from every page; data tables can be sorted by each shown field and offer filters, saved views, pagination with a choice of page size, export as CSV and bulk actions on selected rows (for example approving customers, activating or deactivating products, exporting); navigation and forms can be operated with the keyboard; actions give immediate inline feedback, with undo where it is sensible; the design is consistent, and everything is fully usable on a tablet.
50. The admin dashboard shows today's orders, revenue, orders awaiting action, registrations awaiting approval, return requests awaiting a decision, low-stock products and expiring lots. Each figure leads to the matching filtered list. It shows charts with a comparison to the previous period.
51. Staff can create, edit, deactivate and discontinue products, including descriptions, images, VAT rate, temperature class and bulky flag. A deactivated product is hidden temporarily and can be reactivated. A discontinued product is retired for good. Neither is deleted, so orders and invoices keep showing it. SKUs are unique across all products and variants. All admin data is edited through labelled form fields with validation messages, never as raw data formats such as JSON.
52. Staff can manage categories and assign products to them.
53. Staff can manage packaging units, prices, quantity prices, deposits, options, variants and bundle contents per product through form fields.
54. Staff can manage customers: approve, block, change group, set invoice permission and credit limit, and maintain addresses and users.
55. Staff can maintain negotiated prices per customer and product.
56. Staff can create, edit, deactivate and monitor promotions and promotion codes.
57. Staff can manage shipping methods, fees, thresholds, delivery areas and slot capacity.
58. Staff can find orders by order number, customer, status and date. Each order has its own admin page with its lines, totals, payment attempts, shipments, invoices, credit notes, returns and full history. That page offers exactly the actions that are allowed in the order's current state.
59. Staff can record payments, for example prepayment, invoice payment or cash on pickup.
60. Every change to an order, and every staff change to prices, negotiated prices, customer status, group, invoice permission, credit limit, promotions and stock, is logged with time, staff member, and old and new value. Staff can see this history where the changed record is shown. Every record shows this history as an activity timeline.

## Inventory

61. Stock is kept per product in its base unit and is visible in the admin area.
62. Staff can receive goods, correct stock and record the reason for every stock movement.
63. Stock is reserved when an order is placed, released on cancellation and reduced when goods are shipped.
64. Staff can set a low-stock threshold per product and see which products are below it.
65. Two customers can never buy the same last unit; the shop never oversells.

## Packaging Units

66. Products may be sold in different packaging units. For example, a bottle may be sold on its own, as a box of six bottles, or as a crate that contains several boxes. The customer can see how many base units each packaging unit contains. Pricing, stock and deposits must behave correctly for the selected packaging unit.
67. Each packaging unit can have its own price. It may also simply be the base price multiplied by its content.
68. Some products are sold only in certain packaging units, for example only by the crate.

## Nested Packaging

69. A packaging unit can contain other packaging units, for example a crate of 4 six-packs of 6 bottles, or a pallet of crates. Content, stock and deposits add up correctly across all levels.
70. Deposits can apply at more than one packaging level, for example per bottle, per crate and per pallet.

## Measurement Units

71. Products can be counted in pieces, bottles, cans, packs, kilograms, grams or litres. Quantities and prices are always shown with their unit. Where a product allows it, the customer can order in grams or kilograms, and the conversion is exact.
72. Prices can be stated per piece, per packaging unit, per kilogram or per litre.

## Fractional Quantities

73. Products sold by weight or volume can be ordered in fractional quantities, for example 2.5 kg of cheese or 7.5 litres of juice.
74. Such products have a minimum quantity, a maximum quantity per order line and a quantity step, and the shop rejects quantities that do not fit them. Quantities can be entered with a decimal point or a decimal comma.
75. Catch-weight products are ordered per piece at an estimated weight and are invoiced at the actual weight recorded when packing.

## Deposits

76. Deposits are charged per container as defined for each product, on top of the product price.
77. Deposits are shown separately in the cart, the order, the invoice and on refunds.
78. Deposits are never discounted and do not count toward minimum order values or free-shipping thresholds.
79. Staff can record empty containers returned by a customer. The deposit is then credited to the customer.
80. A deposit that depends on volume is charged correctly, for example one canister for every started 5 litres.

## Quantity Pricing

81. Products can have quantity price tiers, so that larger quantities of a packaging unit get a lower unit price. The tiers are visible on the product page, and the cart shows which tier price applies.

## Customer-Specific Prices

82. Customer groups can have a percentage discount on eligible products.
83. Individual customers can have negotiated net prices for specific products, either per base unit or per packaging unit.
84. A negotiated price takes precedence over list prices, quantity prices, group discounts and promotions.

## Promotions

85. The shop supports percentage discounts, fixed-amount discounts, per-unit discounts, free items, buy-X-pay-Y offers and shipping discounts.
86. Promotions can be limited by date range, minimum goods value, category, product, customer group, individual customer, uses per customer and total uses.
87. Products can be excluded from all discounts.
88. Automatic promotions apply without a code. Promotion codes are entered by the customer, and at most one code is allowed per order. Every applied promotion is shown by name in the cart, the order and the invoice.

## VAT

89. Each product has a VAT rate, and the shop supports at least 7 % and 19 %.
90. VAT is calculated and shown separately per rate on the cart, order and invoice.
91. Deposits, discounts and shipping are taxed according to the business rules: deposits on packaging at the product's rate, pallet deposits at 19 %, and shipping split across the rates of the goods.
92. Customers elsewhere in the EU with a verified VAT ID are invoiced under reverse charge with 0 % VAT.

## Shipping

93. The shop offers several shipping methods with their own fees, free-shipping thresholds and minimum order values. Shipping costs are shown before the order is placed.
94. Bulky items can add a surcharge depending on the shipping method.

## Delivery Restrictions

95. Some shipping methods are limited to certain countries or postcode areas.
96. Chilled, frozen and fresh products can only be delivered by methods that keep the cold chain, or collected.
97. Products with a deposit can only be delivered within Germany or collected.
98. Truck deliveries have delivery days, slots with limited capacity and an order cut-off time.

## Order States

99. Orders move through clearly defined states. The default workflow has the states awaiting approval, pending payment, confirmed, partially shipped, shipped, delivered, completed and cancelled; further workflows can add steps (see requirement 168).
100. Payment status is tracked separately from the order state. Every payment event (authorisation, capture, release, refund, chargeback, transfer received, credit used) is listed in the order's payment history.
101. Unpaid prepayment orders are cancelled automatically after the payment deadline.

## Partial Fulfillment

102. Staff can ship part of an order and leave the rest open. Each shipment is recorded with its lines and quantities, and for parcel methods with the carrier and tracking number. Customers can see which items have shipped, which are still open, and how to track each parcel.
103. Staff can cancel individual lines or quantities of an order that have not shipped. Totals, stock and payments are adjusted. Promotions, payments and balances are recalculated as defined in the business rules.

## Backorders

104. Products can be configured to allow or forbid backorders.
105. A backorderable product can be ordered beyond stock. The backordered quantity is clearly marked in the cart and the order.
106. When new stock arrives, staff can see which backorders can now be fulfilled.

## Lots and Batches

107. Stock of lot-tracked products is kept per lot, with a lot number and quantity.
108. Staff can see which lots were shipped in each shipment, so that affected customers can be found in a recall.

## Expiry Dates

109. Each lot has a best-before date. Stock past its best-before date is never sold or shipped, and staff can see lots that will expire soon.
110. Lots are picked by the earliest best-before date first.

## Substitutions

111. Products can name a substitute product.
112. If a customer allowed substitution and an item cannot be supplied, staff can ship the substitute instead. The customer is charged no more than the original line, and the substitution is visible on the order and invoice.

## Returns and Refunds

113. Customers can request a return for delivered goods, giving the items, quantities and a reason. Returns can cover single lines, quantities or, for catch-weight products, a weight, and name a reason (quality complaint, damaged in transit, ordered by mistake).
114. Staff can approve, partly approve or reject return requests.
115. Staff can refund fully or partially. Refunds include the correct share of discounts, deposits and VAT, and produce a credit note. Returned items are inspected line by line and either restocked to a chosen warehouse or written off. Instead of a refund, staff can send a replacement shipment.
116. Refunds are reflected in the order's payment status and, for purchase on invoice, in the customer's open balance.

## Reporting

117. Staff can see sales by day, week and month, broken down by net amount, VAT and deposits.
118. Staff can see top-selling products and categories and sales by customer and customer group.
119. Staff can see how often each promotion was used and the total discount granted.
120. Staff can see current stock quantities per product and warehouse, low-stock products, open backorders and expiring lots.

## Variants, Related Products, Options and Bundles

121. Products can have variants, such as sizes. A product with variants appears once in the catalog and has one product page, where the customer chooses the variant. Each variant has its own SKU, price and stock. The cart, order and invoice show the chosen variant. The product itself cannot be ordered without choosing a variant.
122. Products can name related products, for example another flavour. Related products are separate products with their own pages and catalog entries. Each product page links to its related products, in both directions.
123. Searching for a variant's SKU finds its product, with that variant preselected or clearly indicated.
124. Products can offer options that change the price but are neither variants nor separate products. The chosen options are visible everywhere the line appears.
125. Products can be sold as bundles. A bundle has its own SKU, page and catalog entry and a fixed price, and consists of fixed quantities of other products. Its availability follows from the stock of its contents, and selling it reduces their stock. The cart, order and invoice show the bundle as one line with its contents.

## Assortment, Accessories and Order Lists

126. Some products are visible and orderable only for certain customer groups or customers. For everyone else they do not exist: they appear neither in categories, search, related products, accessories, bundles, quick order or order lists, nor can their product page be opened directly.
127. A product page can suggest accessories that fit the product, and the customer can add them to the cart from there. Accessories are add-ons, not alternatives, and the suggestion goes one way.
128. Customers can keep named order lists that are shared by all users of the same company. A whole list can be added to the cart in one step. Unavailable items are reported and skipped, and lists can be edited and deleted.

## Pallets

129. Pallets are bulky and can only be delivered by the Spreegrund truck or collected at the warehouse.

## Search Engine Optimisation

130. Every public storefront page has a meaningful title of its own (a product page contains the product name, a category page the category name), a meta description, a canonical address and one main heading. Addresses are readable: a product page's address contains the product's name or SKU. Product pages provide structured product data for search engines (name, SKU, image, and the price where it is visible). The shop offers a sitemap of its public pages. Products of a restricted assortment never appear in the sitemap and cannot be indexed. Cart, checkout, account and admin pages are never indexed. Prices never reach guests or pending customers in any way, including search suggestions and structured data.

## Back-Office Pages

131. Each customer, product, promotion, shipping method and return request has its own admin page showing all of its data and its related records, for example a product's packaging units, tiers, stock and lots.
132. A customer's admin page shows the company data, its users, addresses, group, negotiated prices, invoice permission, credit limit, open balance, orders, invoices, returns and change history.

## Safety, Validation and Security

133. Actions that cannot be undone or that affect customers or money are confirmed before they happen, and the confirmation says what will happen (cancelling an order or line, refunding, rejecting a return, blocking a customer, discontinuing a product, deactivating a promotion). A confirmation is a separate step or dialog that appears after the action is chosen; a required checkbox next to the action does not count unless the shop explains it when the action is chosen without it.
134. Every form in the storefront and the admin area shows a clear message next to each invalid field and keeps what the user entered. A successful save or action is confirmed visibly.
135. Every business rule and every input check is enforced by the shop itself, so it still holds if someone bypasses the user interface.
136. A customer only ever sees their own company's orders, invoices, credit notes, return requests, order lists and addresses, even if they change a number or address in the browser.
137. After five failed sign-in attempts for an email address within 15 minutes, further attempts for that address are refused for 15 minutes, even with the correct password. The same limit applies to password-reset requests per email address, registrations per email address and promotion-code attempts per cart: after five failed or repeated attempts within 15 minutes, further attempts are refused for 15 minutes. Sign-in and password-reset messages never reveal whether an email address is registered.
138. Passwords have a minimum length of 8 characters and must be entered twice when set. Password-reset links expire after 60 minutes and work only once. Signing out ends the session completely, and the admin session ends after 30 minutes without activity.
139. When staff block a customer or set them back to pending approval, the change takes effect immediately, also for users who are signed in at that moment.
140. Placing an order is safe against double clicks, reloads and going back. It never creates a duplicate order or a second payment.

## Documents, Notifications and Staff

141. Customers and staff can open every invoice and credit note as a properly formatted document that can be printed or downloaded.
142. Staff are notified by email when a new registration is waiting for approval. Customers receive an email when their registration is received, when their account is approved, and when they request a password reset.
143. The administrator can create, deactivate and reset further staff accounts. Every staff action is attributed to the staff member who performed it.

## Storefront Layout and Pages

144. Every storefront page has a consistent header with the category navigation, a search field, the cart with its number of items, and access to the account or sign-in. On small screens every category is reachable through a menu. Every page has a footer with the seller's company and contact details and links to the information pages.
145. The storefront has information pages for imprint, terms and conditions, privacy, delivery and payment, and contact, filled with the seller data from `business-rules.md`.
146. Product listings (category, search and featured products) show for each product its image, name, SKU, available packaging units and availability. Approved customers also see the price, and can add a product to the cart directly from the listing with a packaging unit and quantity.
147. The product page shows an image gallery. Selecting a packaging unit or variant shows its image and price. The quantity input follows the product's minimum and step. Adding to the cart gives visible feedback and updates the cart indicator without leaving the page.
148. Customers have an account overview with recent orders, open balance and order lists. Their order history is paginated and can be filtered by status. Customers can add, edit and delete shipping addresses and choose a default one, and can change their own name, email address and password.
149. Pages that do not exist or may not be accessed (including restricted products), expired sessions and unexpected errors show a page in the shop's design with a way back. Empty states (empty cart, no orders yet, no order lists, admin list without entries) explain the situation and offer the next sensible step.

## Reporting, Admin Lists and Performance

150. Reports can be shown for a chosen period (day, week, month or custom range). Orders, invoices, credit notes and the reports can be exported as CSV files for bookkeeping.
151. Admin lists show the figures staff need at a glance: promotions with status and usage against their limit; customers with status, group and open balance; stock with on hand, reserved, available and backordered quantities. Statuses that depend on dates or limits (scheduled, active, expired, used up, deactivated) are worked out by the shop and shown as such; for example, a promotion that starts in 2028 is shown as scheduled.
152. Pages respond quickly with the full catalogue. Product lists use images in sizes suited to their display, not the full-size originals.
153. Text entered by customers or staff (delivery notes, order references, return reasons, company names, product descriptions) is always displayed as text and never executed. Actions cannot be triggered from other websites on a signed-in user's behalf.

## Back-Office Editing and Presentation Quality

154. In the admin area, references to other records (category, products, customer groups, customers, the contents of bundles) are chosen from existing records with a search, never typed as text or as file names. Images are uploaded with a preview and can be reordered and removed.
155. Each record is edited on its own page or in a clearly separate panel, with titled sections. Fields that only apply when a record is created do not appear when it is edited. The save action stays reachable on long forms, and a warning about unsaved changes appears only after something has actually been changed.
156. No raw markup, template code or placeholder text is ever visible anywhere: not in the storefront, the admin area, emails or documents, including pagination, product descriptions and error pages.
157. The provided business data is shown consistently wherever it appears: balances, counts, usage figures and statuses agree between lists, detail pages, the dashboard and reports.

## Company Roles and Approvals

158. Company users have the role company admin or buyer. Company admins manage their own company's users: they invite users by email, deactivate them, and set their role and per-order budget.
159. An order by a buyer above their per-order budget waits for a company admin's approval before it is confirmed; the admin approves it or rejects it with a reason, and both sides are notified by email.

## E-Invoicing, Quotes and Standing Orders

160. Every invoice and credit note is also available as an electronic invoice in the German/EU standard XRechnung (EN 16931), with the correct VAT category for domestic, reverse-charge and export invoices. Customers and staff can download it.
161. Customers can request a quote for their cart, and staff can create quotes. Staff set prices per line and an expiry date. The customer accepts a quote, which turns into an order at the quoted prices through the normal checkout, or declines it. Expired quotes cannot be accepted. Quotes have their own number series and appear in the account and the back-office.
162. Customers can set up standing orders that repeat weekly or every second week. They can pause, resume, skip single dates and edit them. Each occurrence becomes a normal order at the then-valid prices, respecting cut-off times, delivery days and holidays, and staff can generate due occurrences immediately.

## Payment Terms and Dunning

163. Payment terms are set per customer, including early-payment discounts. Invoices show the discount, the amount payable within the discount period and its last day. A payment of the discounted amount within the period settles the invoice, with the VAT corrected per rate. Partial payments are possible and reduce the open balance.
164. Staff run dunning for overdue invoices: payment reminder, first and second dunning notice, each with its document, email and fee as defined. A customer with an invoice at the second dunning level automatically loses purchase on invoice.

## Countries and Currencies

165. The shop has country storefronts for Germany, Austria, Switzerland and the United Kingdom, each with its currency, shipping methods, fees, tax treatment and information-page details. Customers belong to the storefront of their billing country.
166. Prices are shown and charged in the storefront's currency (EUR, CHF or GBP), converted from EUR at fixed exchange rates that staff maintain and rounded as defined. Orders, documents, refunds and emails use the order's currency, and reports show the transaction currency and the EUR equivalent. A rate change affects only carts from then on.
167. Deliveries to Switzerland and the United Kingdom are tax-free export deliveries by International Freight, stated as such on the invoice. Products with a deposit and chilled, frozen or fresh products are not delivered there.

## Order Workflows

168. Staff can configure order-processing workflows: states, allowed transitions, conditions that must hold for a transition and automatic actions on entering a state (for example sending an email, releasing stock, creating an invoice or notifying staff). Rules decide which workflow an order follows. Every order shows its workflow, its current state, the transitions that are possible now and its full history. A changed workflow applies only to orders that enter it afterwards.

## Payment Flows

169. Card payments are authorised when the order is placed and captured when goods ship, shipment by shipment. Captures above the defined tolerance need a new authorisation, an expired authorisation must be renewed, and a chargeback flags the order, reverses the amount and notifies staff.
170. Staff record incoming bank transfers. Transfers are matched to orders by their reference; exact payments, overpayments, underpayments, payments for several orders and duplicate payments are handled as defined, and transfers without a usable reference wait in a list of unmatched payments for manual matching.
171. Customers have a credit balance, which grows through overpayments and refunds to credit and can pay all or part of a later order together with another payment method. Staff can pay a credit balance out. Refunds are split across the payment methods that were used, as defined.
172. A payments ledger in the back-office lists every payment event with date, order, customer, method, amount and currency.

## Warehouses and Fulfillment

173. Stock and lots are kept per warehouse. Orders are allocated to warehouses by defined rules, and an order may ship in several shipments from different warehouses.
174. Staff can transfer stock between warehouses; stock in transit cannot be sold.
175. Staff can print a pick list per warehouse and a packing slip per shipment.
176. Some products are not stocked but sourced from a supplier on demand: their availability shows the lead time, ordered quantities create a supplier purchase order, and received goods go straight into the customer's shipment.
177. Some products are shipped directly by their supplier as a separate shipment of the order.

## Partial Cancellations and Returns

178. Cancelling part of an order recalculates its promotions, shipping, deposits, VAT and payments as defined in the business rules, both before and after a partial shipment.
179. Returns are refunded according to their reason: a quality complaint or damage in transit is refunded in full including deposits, a mistaken order carries a restocking fee, and return shipping is paid as defined. Bundles are returned as a whole, and catch-weight products by weight.

## Process Diagrams and Editing

180. Workflows, fulfillment processes and payment flows are shown in the back-office as diagrams with their steps, transitions, conditions and automatic actions, and an order's current state is highlighted on its workflow. Staff edit workflows on the diagram. Invalid workflows are refused with a message, and every saved change creates a new version while running orders keep theirs.
