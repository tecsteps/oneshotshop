# #OneShotShop — B2B Food & Beverage Edition

**#OneShotShop** is an open benchmark for AI coding agents. Every agent gets the same task, the same business data and a single prompt. Each one then has to build a complete, working online shop on its own. The finished shops are tested against the same acceptance criteria. They are then compared on feature completeness, cost, time and code quality.

This edition raises the bar. Instead of a general-purpose shop, the agents build a webshop for **Spreegrund Food Service**, a fictional Berlin wholesaler that supplies restaurants, cafés, hotels and retailers. B2B food and beverage wholesale is full of difficult commerce rules:

- packaging units nested inside each other, such as bottles, six-packs and crates
- products sold by weight or volume in fractional quantities
- deposits on bottles, crates and kegs
- quantity prices, customer-group discounts and negotiated customer prices
- mixed VAT rates and reverse charge
- delivery slots and cold-chain delivery restrictions
- lots with best-before dates, backorders and substitutions
- partial shipments, returns and refunds

The agents receive no code, no database schema and no prescribed architecture. They get only business intent and raw business data, and they have to turn that into working software themselves.

- Website, results and comparisons: [agentic-engineers.dev](https://agentic-engineers.dev/)
- Follow the challenge on LinkedIn: [#OneShotShop](https://www.linkedin.com/search/results/all/?keywords=%23oneshotshop)
- Created by [Fabian Wesner](https://www.linkedin.com/in/fabian-wesner/)

## What's in This Repository

| Path | Contents |
|---|---|
| `specs/requirements.md` | The business capabilities the shop must support |
| `specs/business-rules.md` | Cross-cutting rules: prices, VAT, rounding, stock, order states, refunds |
| `specs/products.md` | About 130 products with prices, packaging, deposits, VAT and stock |
| `specs/images/` | Product images (one per SKU) and packaging-unit images, 218 in total |
| `specs/customers.md` | Customer accounts, groups and negotiated prices |
| `specs/admin.md` | The administrator account |
| `specs/discounts.md` | Promotions and promotion codes |
| `specs/shipping.md` | Shipping methods, delivery areas and restrictions |
| `specs/payments.md` | Simulated payment methods |

## Prompt

Build the complete B2B food and beverage webshop described in this README and in `specs/*`, from this empty repository, in one go, without stopping or asking questions. Sub-agents or team mode are allowed.

Quality bar: production-ready for real business buyers and staff who use it every day. A polished, responsive storefront and a complete, dedicated back-office (see `specs/admin.md`). Every requirement and business rule is implemented exactly: no placeholders, no shortcuts.

Verify everything: automated unit and feature tests for all business logic, plus the Playwright MCP to use the shop as real customers and staff, on desktop and mobile. Fix every bug you find. Track each requirement's status and how you verified it in `specs/progress.md`, and commit after every meaningful step.

Finish with a full browser review of all customer and staff features against the specs and the rules below. If anything fails, fix it and repeat the review. You are done only when it passes completely.

Rules:

- PHP with Laravel. SQLite for everything: database, queue and cache; file sessions; log mail; FTS5 search. No external services and nothing to install on the host.
- Frontend, architecture, schema and libraries are your choice.
- Use the provided business data: products, images, customers, promotions and the rest.
- Do not reuse code from previous One-Shot Shop versions or branches.
- A fresh clone (git-ignored files such as `.env` are not available) must start with exactly: `composer install && npm ci && npm run build && php artisan migrate --seed && php artisan serve`
