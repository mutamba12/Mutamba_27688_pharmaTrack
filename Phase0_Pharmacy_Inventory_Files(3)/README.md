# PHASE 0: RESEARCH AND PROJECT PROPOSAL

## Design and Implementation of a Pharmacy Inventory and Expiry Monitoring System Using Oracle PL/SQL

---

## 1. Student Information

| Item | Details |
|---|---|
| University | Adventist University of Central Africa (AUCA) |
| Faculty | Faculty of Information Technology |
| Course Code | INSY 8311 |
| Course Name | Database Development with PL/SQL |
| Project Phase | Phase 0 – Research and Project Proposal |
| Student Name | Alice Mutamba |
| Student ID | 27688 |
| Group | B |
| Academic Year | 2026–2027 |
| Semester | I |
| Instructor | Eric Maniraguha |
| Project Type | Individual Capstone Project |

---

## 2. Project Title

**Design and Implementation of a Pharmacy Inventory and Expiry Monitoring System Using Oracle PL/SQL**

---

## 3. Project Background

Pharmacies play an important role in providing medicines and healthcare products to patients. Effective inventory management is necessary to ensure that medicines are available, stored properly and distributed before their expiry dates.

However, some pharmacies experience difficulties managing stock quantities, recording purchases and sales, monitoring medicine batches and identifying products approaching expiry. When these activities are performed manually or using disconnected records, it becomes difficult to maintain accurate inventory information.

Database technology provides an opportunity to improve pharmacy inventory management through organized data storage, automated business rules and reliable reporting.

This project will use Oracle Database and PL/SQL to develop a Pharmacy Inventory and Expiry Monitoring System. Oracle APEX will be used as the planned innovation tool to provide an interactive interface for monitoring inventory information.

---

## 4. Problem Statement

Many pharmacies face challenges in managing medicine stock, monitoring expiry dates and maintaining accurate inventory records. Manual inventory management can make it difficult to identify medicines with low quantities, track individual medicine batches and detect products approaching their expiry dates.

These challenges may result in medicine wastage, stock shortages, financial losses and delays in serving customers.

Therefore, there is a need for a computerized pharmacy inventory management system that can organize medicine records, monitor stock movements, track expiry dates and support effective inventory decisions.

---

## 5. Proposed Solution

The proposed solution is an Oracle PL/SQL-based Pharmacy Inventory and Expiry Monitoring System.

The system will manage medicine information, suppliers, purchases, medicine batches and sales transactions. It will maintain inventory quantities and help pharmacy staff identify low-stock medicines, expired medicines and medicines approaching their expiry dates.

PL/SQL procedures, functions, packages and triggers will be used to implement database operations and enforce business rules.

An Oracle APEX dashboard will provide an interactive interface for viewing inventory information and monitoring important alerts.

---

## 6. Project Objectives

### 6.1 Main Objective

To design and implement a Pharmacy Inventory and Expiry Monitoring System using Oracle Database and PL/SQL to improve medicine stock control, inventory accuracy and expiry monitoring.

### 6.2 Specific Objectives

1. To design a normalized relational database for pharmacy inventory management.
2. To manage medicine, supplier, purchase, batch and sales information.
3. To develop PL/SQL procedures, functions, cursors and packages for inventory operations.
4. To implement database triggers, business rules and audit logging.
5. To develop an interactive Oracle APEX dashboard for monitoring pharmacy inventory.
6. To improve stock visibility and support the identification of expired, near-expiry and low-stock medicines.

---

## 7. Research Questions

The project will be guided by the following questions:

1. How can Oracle Database improve the management of pharmacy inventory information?
2. How can PL/SQL automate stock management and medicine expiry monitoring?
3. How can database triggers help prevent invalid inventory transactions?
4. How can an interactive dashboard support pharmacy inventory decisions?
5. How can batch tracking and the First Expiry, First Out (FEFO) principle help reduce medicine wastage?

---

## 8. Research and Existing System Review

The project will use academic research, technical documentation and healthcare guidance to understand pharmacy inventory challenges and possible solutions.

The research will focus on:

- Medicine expiry and wastage.
- Pharmacy inventory control.
- Medicine stock availability.
- Digital inventory management.
- Database automation.
- Medicine storage and stock rotation.

The reviewed literature will help identify problems in existing inventory practices and justify the need for an integrated database application.

A detailed research log will be maintained in:

`docs/research/research_log.md`

The research log will contain the source title, APA reference, source type, link, key findings and research gap.

At least six credible sources will be investigated, including research papers, a report or statistical source, an existing system, a dataset and a technical source.

---

## 9. Data Source

### 9.1 Selected Dataset

| Item | Details |
|---|---|
| Dataset Name | Pharma Sales Data |
| Author | Milan Zdravković |
| Platform | Kaggle |
| Dataset Link | https://www.kaggle.com/datasets/milanzdravkovic/pharma-sales-data |
| Main Purpose | Sales and demand analysis |
| File Format | To be confirmed after download |

### 9.2 Dataset Description

The selected dataset contains historical pharmaceutical sales information. It will be investigated to determine the available fields, number of records, data quality and suitability for the proposed database project.

### 9.3 Data Preparation Activities

The following activities will be completed:

1. Download the original dataset.
2. Verify its licence and educational-use permissions.
3. Identify the available columns.
4. Determine the exact number of records.
5. Check missing values.
6. Identify duplicate records.
7. Examine data types and inconsistencies.
8. Prepare a dataset card.
9. Preserve the original dataset without modification.

### 9.4 Dataset Limitation

The selected Pharma Sales Data dataset is intended mainly for sales and demand analysis. It may not contain supplier details, medicine batch numbers, purchase records or expiry dates.

Missing information will not be falsely represented as real dataset information. Additional legitimate data will be investigated where necessary. Any synthetic data used for testing will be clearly labelled as synthetic demonstration data.

---

## 10. Planned Database Tables

The initial database design will investigate the following tables:

| No. | Table Name | Description |
|---|---|---|
| 1 | PHARMACY | Stores pharmacy information. |
| 2 | PRODUCT | Stores medicine details. |
| 3 | SUPPLIER | Stores supplier information. |
| 4 | PURCHASE | Stores purchase transactions. |
| 5 | PURCHASE_ITEM | Stores individual medicine items in purchases. |
| 6 | BATCH | Stores medicine batch numbers, quantities and expiry dates. |
| 7 | SALE | Stores sales transactions. |
| 8 | SALE_ITEM | Stores medicines included in sales. |

The final database structure will be established during Phase II through data analysis, normalization and ERD development.

---

## 11. Planned PL/SQL Features

The project will use the following PL/SQL features:

### 11.1 Procedures

Procedures will support operations such as registering medicines, recording purchases, receiving stock, recording sales and generating inventory reports.

### 11.2 Functions

Functions will calculate available stock, determine medicine expiry status and calculate sales totals.

### 11.3 Cursors

Cursors will process multiple medicine and batch records for inventory and expiry reports.

### 11.4 Packages

Packages will group related inventory procedures and functions into reusable program units.

### 11.5 Triggers

Triggers will enforce selected business rules, support stock updates and record important database activities.

### 11.6 Exception Handling

Exception handling will manage errors such as insufficient stock, invalid product identifiers, duplicate records and attempts to sell expired medicines.

---

## 12. Planned Business Rules

The system will apply the following business rules:

1. Each medicine must have a unique product identifier.
2. Every medicine batch must have a batch number and expiry date.
3. Medicine quantities must not become negative.
4. A sale must not exceed available stock.
5. Expired medicines must not be sold.
6. Near-expiry medicines must be identified for attention.
7. Low-stock medicines must be identified for replenishment.
8. Important inventory transactions must be recorded in an audit log.
9. Stock rotation should follow the First Expiry, First Out (FEFO) principle where applicable.

---

## 13. Project Innovation

### Oracle APEX Pharmacy Inventory Monitoring Dashboard

The proposed innovation is an interactive Pharmacy Inventory Monitoring Dashboard developed using Oracle APEX.

The dashboard will connect to the Oracle Database and provide authorized users with a visual overview of pharmacy inventory.

### Planned Dashboard Components

- Total registered medicines.
- Available medicine quantities.
- Low-stock medicine alerts.
- Expired medicine alerts.
- Near-expiry medicine alerts.
- Recent purchases.
- Recent sales.
- Sales summaries.

### Expected Benefits

The dashboard will help pharmacy staff monitor stock levels, identify products requiring attention and make better inventory decisions.

The business rules will be implemented in PL/SQL so that the database enforces them independently of the user interface.

---

## 14. Expected Results

The project is expected to produce:

1. A properly designed Oracle relational database.
2. Normalized pharmacy inventory tables.
3. Working PL/SQL procedures and functions.
4. PL/SQL packages and cursors.
5. Triggers for inventory control and auditing.
6. Business rules for stock and expiry monitoring.
7. An interactive Oracle APEX dashboard.
8. Technical documentation and a final project presentation.

---

## 15. Software and Technologies

| Technology | Purpose |
|---|---|
| Oracle Database | Database management |
| Oracle SQL Developer | Database development and administration |
| SQL | Database queries and data manipulation |
| PL/SQL | Database programming and automation |
| Oracle APEX | Interactive application and dashboard |
| GitHub | Version control and project submission |
| Draw.io | Business process and database diagrams |
| Microsoft Word | Project proposal and documentation |
| Microsoft PowerPoint | Project presentation |
| Kaggle | Dataset source |

---

## 16. Project Development Plan

The capstone project will be completed in eight phases:

| Phase | Name | Main Deliverable |
|---|---|---|
| Phase 0 | Research and Project Proposal | Research log, proposal, presentation and GitHub repository |
| Phase I | Business Process Modeling | Business process diagram and explanation |
| Phase II | Data Sourcing and Normalization | Dataset card, normalization, ERD and data dictionary |
| Phase III | Oracle PDB Creation | PDB, administrator, tablespaces and verification evidence |
| Phase IV | Database Creation and Data Loading | Oracle tables and loaded records |
| Phase V | PL/SQL Programming | Procedures, functions, cursors and packages |
| Phase VI | Triggers and Auditing | Business rules, triggers and audit log |
| Phase VII | Documentation and Innovation | Working Oracle APEX dashboard, final report and presentation |

---

## 17. GitHub Repository

**Repository Name:** alice_27688_pharmaTrack

**Repository URL:**

https://github.com/mutamba12/alice_27688_pharmaTrack

The repository will store the project proposal, research log, presentation, dataset documentation, database scripts, diagrams, screenshots and final report.

### Phase 0 Folder Structure

```text
alice_27688_pharmaTrack/
│
├── README.md
│
├── docs/
│   ├── research/
│   │   └── research_log.md
│   │
│   ├── proposal/
│   │   └── Phase0_Proposal_Alice_Mutamba.docx
│   │
│   └── presentation/
│       └── Phase0_Presentation_Alice_Mutamba.pptx
│
├── data/
│   ├── raw/
│   └── processed/
│
└── innovation/
    └── README.md
```

---

## 18. Phase 0 Deliverables

The following documents and resources will be prepared for Phase 0:

| No. | Deliverable | Status |
|---|---|---|
| 1 | Project topic and problem statement | Draft prepared |
| 2 | Research log with at least six credible sources | Starter log prepared; verification required |
| 3 | Project proposal | Draft prepared |
| 4 | Dataset source and documentation | Dataset selected; licence and record count to verify |
| 5 | Project presentation | Draft prepared |
| 6 | GitHub repository | Created |
| 7 | Project README | Prepared |

---

## 19. References

Hakuzimana, T., Kayumba, P. C., Hahirwa, I., & Kabalisa, M. (2021). Assessment of factors contributing to medicine expiry in Rwanda: Case of the Medical Procurement and Production Division. *Rwanda Journal of Medicine and Health Sciences, 4*(2), 281–291. https://doi.org/10.4314/rjmhs.v4i2.7

Jaju, R., Varshney, S., Gupta, P., Bihani, P., & Karim, H. M. R. (2023). Inventory control mechanism of the pharmacy store of a recently established national institute in Eastern India: A cross-sectional, investigative analysis. *Cureus, 15*(11), e49632. https://doi.org/10.7759/cureus.49632

Oracle. (2024). *Oracle Database PL/SQL Language Reference*. https://docs.oracle.com/en/database/oracle/oracle-database/21/lnpls/

World Health Organization. (2022). *Standard operating procedures: Storage*. https://iris.who.int/bitstream/handle/10665/360835/9789240049581-eng.pdf?sequence=1

Zdravković, M. (n.d.). *Pharma Sales Data* [Data set]. Kaggle. https://www.kaggle.com/datasets/milanzdravkovic/pharma-sales-data

**Note:** These are initial references. The final research log must contain at least six credible sources. Verify all publication details, read the original sources and confirm the dataset licence before final submission.

---

## 20. Conclusion

Phase 0 establishes the foundation for the Pharmacy Inventory and Expiry Monitoring System. It defines the pharmacy inventory problem, proposes an Oracle PL/SQL-based solution, identifies the dataset, outlines the database design and introduces Oracle APEX as the planned innovation.

The next phases will transform this proposal into a working database application through business process modeling, data normalization, Oracle PDB creation, database development, PL/SQL programming, auditing and dashboard implementation.

---

**Prepared by:** Alice Mutamba  
**Student ID:** 27688  
**Group:** B  
**Course:** INSY 8311 – Database Development with PL/SQL  
**Instructor:** Eric Maniraguha  
**Academic Year:** 2026–2027
