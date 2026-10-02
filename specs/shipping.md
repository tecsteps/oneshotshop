# Shipping and Delivery

All fees are net amounts. VAT is added as described in `business-rules.md`. "Goods value" means the merchandise net total after customer-group discounts and before promotions. It excludes deposits, shipping and VAT.

## Delivery Countries

The shop delivers to Germany, Austria, the Netherlands, Belgium, Switzerland and the United Kingdom. Addresses in any other country cannot be used as shipping addresses. Which methods a customer sees depends on the country storefront (see `business-rules.md`).

## Temperature Classes and Bulky Items

Every product belongs to one temperature class: **ambient** (the default), **chilled**, **frozen** or **fresh produce**. Some products or packaging units are marked as **bulky items** in the catalog.

- Chilled, frozen and fresh-produce products can only be delivered by the Spreegrund truck or collected at the warehouse.
- Products that carry a deposit can only be delivered within Germany or collected at the warehouse, because the deposit system is German.
- Pallets can only be delivered by the Spreegrund truck or collected at the warehouse.
- If the cart contains a product that the chosen shipping method cannot carry, checkout explains which products block that method. The customer must change the cart or choose another method.

## Shipping Methods

### 1. Spreegrund Truck Delivery

Delivery by Spreegrund's own refrigerated trucks.

- Available only for shipping addresses in Germany with a postcode from 10115 to 14199 (Berlin delivery area).
- Carries all temperature classes and bulky items.
- Fee: €15.00 per order. Free when the goods value is €250.00 or more.
- Minimum goods value: €100.00.
- The customer must choose a delivery date and a delivery slot (see below).

### 2. Standard Parcel Germany

Parcel delivery by a carrier in 2–3 working days.

- Available for shipping addresses in Germany.
- Ambient products only.
- Fee: €9.90 per order. Free when the goods value is €300.00 or more.
- Bulky surcharge: €8.50 for every bulky item in the order, for example 3 × 25 kg flour sacks = €25.50. The surcharge also applies when the order ships free.
- Minimum goods value: €75.00.

### 3. Express Parcel Germany

Next-working-day parcel delivery when ordered by 14:00 on a working day.

- Available for shipping addresses in Germany.
- Ambient products only. Not available if the order contains any bulky item.
- Fee: €19.90 per order. Never free.
- Minimum goods value: €75.00.

### 4. EU Parcel

Parcel delivery to Austria, the Netherlands and Belgium in 3–5 working days.

- Ambient products only. Products with a deposit and bulky items are not allowed.
- Fee: €24.90 per order. Free when the goods value is €750.00 or more.
- Minimum goods value: €150.00.

### 5. Warehouse Pickup

Collection at Spreegrund Food Service, Beusselstraße 52, 10553 Berlin.

- Available to customers of the Germany and Austria storefronts, whatever their shipping address; not available in the Switzerland and United Kingdom storefronts (their orders leave the country as export deliveries). Not available for orders that contain a drop-shipped product.
- Carries all temperature classes and bulky items.
- Free. No minimum goods value.
- The customer must choose a pickup date. Pickup is possible Monday to Saturday, 07:00–14:00, except on Berlin public holidays, from the next day up to 14 days ahead.

### 6. International Freight

Freight delivery to Switzerland and the United Kingdom in 5–7 working days, as a tax-free export delivery.

- Only for shipping addresses in Switzerland or the United Kingdom, and the only method there (Warehouse Pickup is not offered).
- Ambient products only. Products with a deposit and bulky items are not allowed.
- Switzerland: fee CHF 45.00 per order, free when the goods value is CHF 1,000.00 or more; minimum goods value CHF 250.00.
- United Kingdom: fee GBP 39.00 per order, free when the goods value is GBP 900.00 or more; minimum goods value GBP 200.00.
- The goods value is the merchandise net total in the order currency after customer pricing and before promotions.

## Delivery Dates and Slots (Truck Delivery)

- Deliveries run Monday to Friday. There are no deliveries on Saturdays, Sundays or Berlin public holidays.
- The earliest delivery date is the next delivery day if the order is placed by 18:00. Orders placed after 18:00 can be delivered from the delivery day after that. This applies on every day of the week: an order placed on a Monday at 10:00 can be delivered from Tuesday, and one placed on a Friday or Saturday at 19:00 from the following Tuesday (if Monday and Tuesday are delivery days).
- The latest delivery date that can be chosen is 14 days ahead.
- Slots: 06:00–09:00, 09:00–12:00 and 12:00–15:00.
- Each slot accepts at most 8 orders per day. A full slot cannot be chosen.

## Warehouses

| Warehouse | Address | Temperature classes |
|---|---|---|
| WH-BER (Berlin main warehouse) | Beusselstraße 52, 10553 Berlin | ambient, chilled, frozen, fresh produce |
| WH-BRB (Brandenburg overflow warehouse) | Am Güterbahnhof 3, 14770 Brandenburg an der Havel | ambient only |

- Stock and lots are kept per warehouse. Products without a stated split are stocked entirely in WH-BER (see `products.md`).
- Allocation: when an order is placed, each line is reserved from WH-BER first and from WH-BRB for any remainder. Chilled, frozen and fresh products come only from WH-BER. Within a warehouse, lots with the earliest best-before date come first.
- An order may ship in several shipments from different warehouses. Shipping fees are charged once per order, never per shipment.
- Staff can transfer stock between warehouses. Transferred stock is "in transit" from dispatch until it is received at the target warehouse; stock in transit cannot be sold or reserved.
- Staff print a pick list per warehouse (all lines to pick there, with lots) and a packing slip per shipment (its lines, quantities and lots, without prices).
- Warehouse Pickup is always at WH-BER. Goods allocated to WH-BRB are transferred to WH-BER before the pickup date.

## Suppliers, Cross-Docking and Drop-Shipping

| Supplier | Number | Process | Products | Lead time |
|---|---|---|---|---|
| Weinkontor Potsdam GmbH, Brandenburger Straße 40, 14467 Potsdam | SUP-01 | cross-docking | WINE-006, SPI-005 | 3 working days |
| Havelgas Versorgung GmbH, Industriestraße 8, 14612 Falkensee | SUP-02 | drop-shipping | NF-006 | 2 working days |

- **Cross-docking:** these products are not stocked. Their availability reads "ships in 3 working days". Each order line creates or extends a supplier purchase order for that supplier on the day the order is placed. Received goods are not put into stock; they go straight into the customer's shipment from WH-BER. The truck delivery date or pickup date offered for such an order is at least the supplier's lead time after the order date.
- **Drop-shipping:** the supplier ships these products directly to the order's shipping address as a separate shipment of the order (shipping is still charged once, by Spreegrund). Orders with a drop-shipped product must use Spreegrund Truck Delivery or Standard Parcel Germany to an address in Germany. The order line creates a supplier purchase order marked as drop-shipment. When the supplier confirms dispatch, staff record the shipment with its tracking reference.
- Supplier purchase order numbers follow the format `PUR-` plus a five-digit sequence; the first is `PUR-10001`.

## Backorders and Partial Shipments

Backordered quantities ship later by the same method as the original order. The follow-up shipment does not charge another shipping fee.
