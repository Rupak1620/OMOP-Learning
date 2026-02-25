1. How are OMOP tables connected?

OMOP tables are connected through relational keys, primarily:
- person_id
- visit_occurrence_id
- concept_id

The PERSON table acts as the central anchor.
All clinical tables (CONDITION_OCCURRENCE, DRUG_EXPOSURE, MEASUREMENT, etc.) contain
a person_id column that links data back to a specific patient.

Additionally, many clinical tables include visit_occurrence_id, which links events to a specific hospital visit.

Each clinical event also stores a concept_id, which links to the CONCEPT table to standardize medical meaning.

This relational structure allows OMOP to build a complete and consistent patient history.

2. Why is person_id important?

person_id is the unique identifier for each patient in the OMOP database.

It is important because:
- It connects all clinical events to a single patient.
- It allows tracking of patient history over time.
- It enables patient-level research and analysis.
- It ensures consistency when joining multiple tables.

Without person_id, clinical data would not be connected to individual patients.

3. Why is visit_occurrence_id important?

visit_occurrence_id represents a specific healthcare encounter.
It is important because:
- It provides time context for clinical events.
- It groups diagnoses, medications, and measurements that occurred during the same visit.
- It enables time-based analysis.
- It helps distinguish between multiple hospital visits for the same patient.

This allows researchers to analyze events within a particular visit or across multiple visits.

4. Why do research queries require joining multiple tables?

Healthcare data is complex and multidimensional.

A single research question often involves:
- Diagnoses (CONDITION_OCCURRENCE)
- Medications (DRUG_EXPOSURE)
- Lab results (MEASUREMENT)
- Patient demographics (PERSON)

Because this information is stored in separate tables, researchers must use SQL joins to combine data.

For example:
To find patients with Diabetes who received Metformin and had HbA1c > 7, the query must join:
- CONDITION_OCCURRENCE
- DRUG_EXPOSURE
- MEASUREMENT
- PERSON

Joining multiple tables enables comprehensive cohort building.

5. What is longitudinal data in OMOP?

Longitudinal data refers to tracking patient information over time.

In OMOP, longitudinal analysis is possible because:
- Each event has a date.
- Each visit is recorded with start and end dates.
- All events are linked to a specific patient.

This allows researchers to study:
- Disease progression
- Treatment response
- Outcomes over time
- Readmission patterns

Longitudinal structure is one of the strongest features of OMOP for clinical research and AI dataset creation.