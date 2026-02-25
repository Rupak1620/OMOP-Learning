1. What is the CONCEPT Table?

The CONCEPT table is the core vocabulary table in OMOP.

It stores standardized medical concepts used across the database.

Each row represents a unique medical concept and contains:

	concept_id → Unique identifier

	concept_name → Human-readable name

	vocabulary_id → Source vocabulary (SNOMED, LOINC, RxNorm, etc.)

	domain_id → Domain (Condition, Drug, Measurement, etc.)

	standard_concept → Indicates if the concept is standard

The CONCEPT table allows OMOP to store healthcare data using consistent and globally recognized identifiers instead of free text.

2. Why Does OMOP Use concept_id Instead of Text?

OMOP uses concept_id instead of text to ensure:

	Consistency across institutions

	No ambiguity in medical meaning

	Efficient database storage

	Faster and more reliable querying

For example:

	Instead of storing:

	“Diabetes”

	“Type 2 DM”

	“E11”

OMOP stores a single standardized concept_id that represents Type 2 Diabetes.

This prevents confusion and ensures that all hospitals refer to the same medical condition in the same way.

3. What Is the Difference Between Standard Concept and Source Concept?

A source concept is the original code used by a hospital system.

	Example:

	ICD-10 code: E11

A standard concept is the normalized concept used by OMOP for research consistency.

	Example:

	SNOMED concept ID for Type 2 Diabetes

During ETL:

	The source concept is mapped to a standard concept.

	OMOP stores the standard concept ID in clinical tables.

	The original source code is often stored in source_value fields for traceability.

This ensures both consistency and auditability.

4. Why Is Mapping Important During ETL?

Mapping is crucial because hospitals use different coding systems.

Without mapping:

	Data from different hospitals would not match.

	Research results would be inconsistent.

	Queries would miss relevant cases.

During ETL:

	Local codes are mapped to standardized concepts.

	Data is harmonized into a unified structure.

This allows researchers to run the same analysis across multiple institutions using consistent definitions.