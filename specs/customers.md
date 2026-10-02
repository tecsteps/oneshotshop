# Customers

Customer accounts that exist when the shop starts. All customers are businesses. Email domains use the reserved `.example` top-level domain.

## Customer Groups

| Group | Group discount |
|---|---|
| Standard | none |
| Retail | 3 % |
| Gastronomy | 5 % |
| Key Account | 8 % |

The group discount reduces the net list price of every product that is not excluded from discounts. See `business-rules.md` for how it combines with negotiated prices and promotions.

## Account Status

- **Active:** can sign in, see prices and place orders.
- **Pending approval:** registered but not yet approved by staff. Can sign in, but sees no prices and cannot order.
- **Blocked:** cannot sign in.

Open balances listed below are carried over from the previous accounting system. They are not overdue unless stated otherwise. No earlier orders exist in the shop.

Unless stated otherwise, a company's single user is its company admin, users have no per-order budget, and payment terms are "net 30 days" (see `payments.md`). Each customer belongs to the country storefront of its billing country (see `business-rules.md`).

New registrations always start as "pending approval" in the group Standard.

---

## C-10001 — Osthafen Küche GmbH

- Group: Gastronomy
- Status: active
- Users (both see the same company prices, addresses and orders):
  - Jana Petersen — `einkauf@osthafen-kueche.example` — password `Hafen#2026` — role: company admin
  - Mehmet Yilmaz — `kueche@osthafen-kueche.example` — password `Kombuese!26` — role: buyer, per-order budget €500.00
- Billing address: Osthafen Küche GmbH, Stralauer Allee 10, 10245 Berlin, Germany
- Shipping address: same as billing
- VAT ID: DE811223344
- Purchase on invoice: allowed, credit limit €5,000.00, current open balance €0.00
- Negotiated prices:
  - BEER-004 Pilsner Keg 30 l: €109.00 per keg
  - COF-001 Espresso Beans: €16.90 per bag, also inside cartons (a carton of 6 bags therefore costs €101.40)
  - FRZ-001 French Fries: €13.20 per carton of 4 bags. Single bags are charged at normal pricing.
- Saved order list "Weekly bar order" (shared by both users):
  - 5 crates of BEER-001 Pilsner, 0.5 l
  - 2 trays of SOFT-001 Cola, 0.33 l
  - 1 keg of BEER-004 Pilsner Keg, 30 l
  - 10 single lemons of VEG-004 Lemons
  - 2 single cartons of JUI-005 Multivitamin Juice (currently out of stock)

## C-10002 — Café Morgenrot

- Group: Gastronomy
- Status: active
- User: Lea Brandt — `hallo@cafe-morgenrot.example` — password `Morgen!2026`
- Billing address: Café Morgenrot, Inh. Lea Brandt, Kastanienallee 10, 10435 Berlin, Germany
- Shipping address: same as billing
- VAT ID: DE299887766
- Purchase on invoice: not allowed
- Negotiated prices: none

## C-10003 — Feinkost Lindner KG

- Group: Retail
- Status: active
- User: Thomas Lindner — `bestellung@feinkost-lindner.example` — password `Lindner!80331`
- Billing address: Feinkost Lindner KG, Westenriederstraße 8, 80331 München, Germany
- Shipping address: same as billing (outside the truck delivery area)
- VAT ID: DE277665544
- Purchase on invoice: allowed, credit limit €2,000.00, current open balance €1,850.00. Invoice payment is therefore only possible for orders with a gross total of €150.00 or less.
- Negotiated prices:
  - CHE-002 Parmigiano Reggiano 24 Months: €22.00 per kg
- Personal promotion code: LINDNER2026 (see `discounts.md`)

## C-10004 — Hotel Seeblick AG

- Group: Key Account
- Status: active
- Users:
  - Sabine Hoffmann — `purchasing@hotel-seeblick.example` — password `Seeblick#Key8` — role: company admin
  - Tobias Krüger — `kueche@hotel-seeblick.example` — password `Seeblick#Buy26` — role: buyer, per-order budget €1,000.00
- Billing address: Hotel Seeblick AG, Zentraleinkauf, Friedrichstraße 100, 10117 Berlin, Germany
- Shipping addresses (the customer chooses one at checkout):
  - Hotel Seeblick Wannsee, Am Großen Wannsee 50, 14109 Berlin, Germany (default; inside the truck delivery area)
  - Hotel Seeblick Warnemünde, Seestraße 10, 18119 Rostock, Germany (outside the truck delivery area)
- VAT ID: DE188776655
- Purchase on invoice: allowed, credit limit €20,000.00, current open balance €3,200.00
- Payment terms: 2 % early-payment discount if paid within 10 days of the invoice date, otherwise net 30 days
- Negotiated prices:
  - WINE-005 Prosecco DOC Extra Dry: €5.40 per bottle in any packaging unit (a carton of 6 therefore costs €32.40)
  - SPI-005 Single Malt Whisky 12 Years: €29.90 per bottle
  - WAT-002 Still Mineral Water 1 l Glass: €17.55 per crate of 18 bottles. Single bottles, boxes and pallets are charged at normal pricing.
- Exclusive assortment: WINE-008 Seeblick Cuvée Brut, Private Label. It is visible and orderable only for this customer.

## C-10005 — Wiener Genuss GmbH

- Group: Standard
- Status: active
- User: Florian Gruber — `office@wiener-genuss.example` — password `Wien!1060`
- Billing address: Wiener Genuss GmbH, Linke Wienzeile 4, 1060 Wien, Austria
- Shipping address: same as billing
- VAT ID: ATU12345675, verified. Orders are invoiced with 0 % VAT under the reverse-charge rule.
- Purchase on invoice: allowed, credit limit €3,000.00, current open balance €0.00
- Negotiated prices: none

## C-10006 — De Kaasboer B.V.

- Group: Retail
- Status: active
- User: Pieter de Vries — `inkoop@dekaasboer.example` — password `Kaas!Amsterdam1`
- Billing address: De Kaasboer B.V., Prinsengracht 200, 1016 HD Amsterdam, Netherlands
- Shipping address: same as billing
- VAT ID: none on file. Orders are therefore charged German VAT.
- Purchase on invoice: not allowed
- Negotiated prices: none

## C-10007 — Spätkauf am Kanal UG

- Group: Standard
- Status: active
- User: Aylin Demir — `kontakt@spaetkauf-kanal.example` — password `Kanal!10999`
- Billing address: Spätkauf am Kanal UG (haftungsbeschränkt), Paul-Lincke-Ufer 30, 10999 Berlin, Germany
- Shipping address: same as billing
- VAT ID: DE344556677
- Purchase on invoice: not allowed
- Negotiated prices: none

## C-10008 — Kantine Nordlicht GmbH

- Group: Standard (until approved)
- Status: **pending approval**
- User: Ole Jensen — `einkauf@kantine-nordlicht.example` — password `Nordlicht!13353`
- Billing address: Kantine Nordlicht GmbH, Nordufer 20, 13353 Berlin, Germany
- Shipping address: same as billing
- VAT ID: DE355667788
- Purchase on invoice: not allowed

## C-10009 — Imbiss Ecke e.K.

- Group: Gastronomy
- Status: **blocked** because of overdue invoices
- User: Kemal Aksoy — `info@imbiss-ecke.example` — password `Imbiss!2026`
- Billing address: Imbiss Ecke e.K., Karl-Marx-Straße 50, 12043 Berlin, Germany
- Shipping address: same as billing
- VAT ID: DE366778899
- Purchase on invoice: allowed, credit limit €1,000.00, current open balance €1,240.00 (overdue)
- The open balance consists of three unpaid invoices from the previous accounting system. Their dates are relative to the day the shop's data is loaded ("load day"); payment terms net 30 days:
  - LEG-0412: €300.00, invoice date load day − 40 days (due load day − 10 days)
  - LEG-0398: €440.00, invoice date load day − 50 days (due load day − 20 days)
  - LEG-0377: €500.00, invoice date load day − 70 days (due load day − 40 days)

## C-10010 — Hotel Alpenblick AG

- Group: Gastronomy
- Status: active
- User: Reto Meier — `einkauf@hotel-alpenblick.example` — password `Alpen!Blick26`
- Billing address: Hotel Alpenblick AG, Bahnhofstrasse 20, 8001 Zürich, Switzerland
- Shipping address: same as billing
- VAT number: CHE-123.456.789 MWST (Swiss UID)
- Country storefront: Switzerland, currency CHF
- Purchase on invoice: not allowed
- Negotiated prices: none

## C-10011 — Thames Deli Ltd

- Group: Retail
- Status: active
- User: Oliver Grant — `buying@thamesdeli.example` — password `Thames!Deli26`
- Billing address: Thames Deli Ltd, 12 Borough High Street, London SE1 9QQ, United Kingdom
- Shipping address: same as billing
- VAT number: GB123456789
- Country storefront: United Kingdom, currency GBP
- Purchase on invoice: not allowed
- Negotiated prices: none

