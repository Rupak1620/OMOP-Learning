# Day 4 – OMOP CDM Installation (PostgreSQL + CDM v5.4)

# Goal
Install OMOP "server" locally on Windows using Docker:
- PostgreSQL container
- OMOP CDM v5.4 schema + tables in PostgreSQL

# Setup
- OS: Windows
- Tools: Docker Desktop, Git
- Database: PostgreSQL 16 (Docker)

# Steps Performed

## 1) Start PostgreSQL (Docker)
- Created docker-compose.yml under 02_installation
- Started container: omop-postgres
- Verified with: docker ps

## 2) Download OMOP CDM v5.4 PostgreSQL SQL scripts
Downloaded official SQL files from OHDSI CommonDataModel repo:
- OMOPCDM_postgresql_5.4_ddl.sql
- OMOPCDM_postgresql_5.4_primary_keys.sql
- OMOPCDM_postgresql_5.4_constraints.sql
- OMOPCDM_postgresql_5.4_indices.sql

## 3) Copy scripts to container + prepare schema
- Copied scripts into container path: /ddl
- Created schema: cdm
- Replaced placeholder @cdmDatabaseSchema with cdm

## 4) Execute scripts in correct order
- ddl → primary keys → constraints → indices

## 5) Verification
Verified tables exist using:
- \dt cdm.*

Core tables present:
- person
- visit_occurrence
- condition_occurrence
- drug_exposure
- measurement
- concept
(and others)

# Notes / Issues
- One constraint error appeared related to cohort table foreign key.
- CDM tables were still created successfully and verified.
- This can be revisited later if required.