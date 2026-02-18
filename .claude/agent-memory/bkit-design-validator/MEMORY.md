# Design Validator Memory - TaxServiceENTEC

## Project Structure
- Plan: `docs/01-plan/features/Tax-refund.plan.md` (v1.1, 21 FRs, 177 SP)
- Schema: `docs/01-plan/schema.md` (v1.0, 63 tables, 5 layers)
- Design: `docs/02-design/features/Tax-refund.design.md` (v1.2, 2203 lines)
- Requirements: `docs/requirements-tax-refund-system.md` (833 lines, 27 US)
- Reference: `참고1번-development-design-v2.md` (83 tables, direction only)
- Validation results: `review-docs/design-validation-result.md` (v1.3, score 91/100)

## Key Naming Conventions
- Table prefixes: INP_/SMR_/OUT_/REF_/AUD_ (NOT RI_/SV_/CO_/RF_/AL_ from ref doc)
- Tax type suffixes: _C_ (corp), _I_ (inc), _S_ (shared)
- Provision codes in code: SS24, SS29_8, SS30_4, SS6, SS7, SS10
- Entity naming: PascalCase of table name (e.g., inp_request -> InpRequest)

## Critical Issue (RESOLVED 2026-02-18)
- Java 1.8 in design.md conflicted with Spring Boot 3.x (requires Java 17)
- Fixed in design.md v1.1: all Java refs updated to 17

## Schema Change from Reference
- 83 tables (ref) -> 63 tables (schema.md) -- intentional simplification
- Prefix change documented in schema.md section 11.2

## Validation v1.3 Results (2026-02-18)
- Score: 91/100, Critical 0, Open Warnings 9 (Medium 4, Low 5)
- FR-20 (환급가산금) covered by M6-02, F31/F32/F-INC-09
- FR-21 (지방소득세) covered by M6-03, F33
- All 21 FRs mapped; all 27 US stories mapped
- 6 new warnings (W-16~W-21): stale numbers in docs
- Key cross-doc inconsistencies: Plan says "83 tables"/"19 FRs", requirements has old prefixes

## Common Stale-Number Patterns
- Formula count: 53 (old) -> 56 (current). Check all docs for "53개"
- Table count: 83 (ref) -> 63 (schema). Check Plan for "83개"
- FR count: 19 (old) -> 21 (v1.1). Check Plan DoD for "19개"
- US-021/022 IDs differ between requirements and Plan v1.1
