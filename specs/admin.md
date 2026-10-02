# Administrator

One administrator account exists when the shop starts:

- Name: Shop Administrator
- Email: `admin@spreegrund.example`
- Password: `Spreegrund!Admin2026`

The administrator can manage all shop data that the business needs to run day to day. This includes products, packaging units, prices, stock and lots, categories, customers and their groups and prices, promotions, shipping, orders, shipments, returns and refunds, and reports.

The admin area is a dedicated back-office with its own layout and navigation, separate from the storefront: it shows no storefront header, search, cart or footer. It is designed for efficient daily work, with list views that offer search, filters, sorting and pagination. Every piece of data, including packaging units, price tiers, deposits, options, variants, bundle contents, negotiated prices and addresses, is maintained through proper form fields with labels and clear validation messages. Staff never edit raw data formats such as JSON.

Every packaging unit, quantity tier, deposit, negotiated price, address, user, option, variant and bundle item can be added, changed and removed one by one in its own labelled fields. References to other records, such as a product's category or a bundle's contents, are chosen from the existing records with a search. Images are uploaded with a preview and can be reordered and removed. Each record is edited on its own page or panel with titled sections. The admin area also works on a tablet.

The back-office meets the standard of leading commerce back-offices: a global search across orders, customers, products and quotes from every page; data tables that can be sorted by each shown field, filtered, saved as named views, paginated with a choice of page size and exported as CSV; bulk actions on selected rows; a dashboard with charts and a comparison to the previous period; an activity timeline on every record; immediate inline feedback with undo where sensible; keyboard operation throughout; and diagrams of the order workflows, fulfillment processes and payment flows, with visual editing of workflows (see `business-rules.md`).

The administrator can create further staff accounts (see `requirements.md`). Every staff action is attributed to the staff member who performed it.

Document the address of the admin sign-in page in the README.

Customers can never use the administrator account, and the administrator account cannot sign in to the storefront as a customer.
