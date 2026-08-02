# ItemFoundry

> Turn supplier documents into trusted product data.

ItemFoundry is a multi-tenant supplier product-onboarding platform for distributors, marketplaces, and resellers. It transforms inconsistent supplier documents and free-form product information into normalized, category-specific product records with field-level citations and human validation.

## Core workflow

1. A buyer defines its product-category taxonomy.
2. For each category, the buyer defines and describes the normalized fields it needs.
3. The buyer creates a supplier account, and the supplier admin manages additional supplier users.
4. A supplier submits a batch of SKUs through XLSX/CSV, product documents, and free-form information.
5. The system models product families, variants, packaging, and product identity while reusing shared documents safely.
6. An LLM recommends categories using the buyer's taxonomy, and the supplier confirms or corrects them.
7. An LLM extracts values using each confirmed category's field definitions.
8. Every proposed value includes its source evidence and validation status.
9. The supplier reviews, corrects, and attests to the product data.
10. The buyer reviews prioritized exceptions, requests corrections where needed, and approves products.
11. Approved products are delivered as canonical JSON and a buyer-mapped CSV/JSON export.

The initial experience is UI-driven. A later public supplier API will expose the same workflow, with supplier-admin API credential management and read-only masked credential visibility for regular supplier users.

## Local architecture

The platform is planned as a modular monolith with independently runnable web, API, and background-worker processes:

- Next.js and TypeScript web application
- FastAPI and Python backend
- PostgreSQL with pgvector
- Redis-backed background jobs
- LocalStack S3 for local object storage
- OpenRouter for configurable LLM access
- Docker and Docker Compose for local development

## Project status

ItemFoundry is currently in the planning and initial scaffolding phase. See the [product and delivery plan](./Docs/PRODUCT_PLAN.md) for the domain model, architecture, security model, evaluation strategy, and implementation iterations.
