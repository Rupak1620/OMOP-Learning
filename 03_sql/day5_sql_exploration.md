# Day 5 – OMOP SQL Exploration (Practical Demo)

## Objective
Understand how OMOP CDM tables connect in practice using SQL queries.

## Steps Performed

### 1. Seeded Minimal Reference Tables
- DOMAIN
- VOCABULARY
- CONCEPT_CLASS
- Inserted concept_id = 0 (No matching concept)

Note: Some foreign key constraints were temporarily dropped to allow demo inserts.

### 2. Inserted Demo Clinical Data
- 1 Patient (person_id = 1001)
- 1 Visit
- 1 Condition: Type 2 Diabetes Mellitus
- 1 Drug: Metformin
- 1 Measurement: HbA1c = 8.5 Percent

### 3. Research-Style Query
Joined:
PERSON → VISIT_OCCURRENCE → CONDITION_OCCURRENCE → DRUG_EXPOSURE → MEASUREMENT

Retrieved patient-level clinical summary.

## Key Learning

- OMOP stores concept_id, not raw text.
- Meaning comes from joining with CONCEPT table.
- Strong foreign key structure ensures research-grade integrity.
- OMOP enables reproducible observational research queries.