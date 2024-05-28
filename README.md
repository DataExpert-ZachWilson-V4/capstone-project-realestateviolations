# Overview
Housing authorities in large cities track violations related to health, safety, and other concerns. However, due to a fragmented landscape with diverse stakeholders, communication gaps often occur. These gaps lead to delays that harm tenants by not addressing their issues promptly and hurt owners who unknowingly accrue fines from unaddressed violations. Our goal is to solve this by enabling anyone to subscribe for updates on specific properties, enhancing information flow, and making public data sets more accessible and user-friendly.

## Datasets used
We decided to start small with the largest housing authority in the United States. New York City, NY.
The city of New York provides access to public datasets containing violation information.
We aim to collate this data in a presentable way that makes it easy to notify owner-operators of violations, and for future tenants to make informed renting decisions based on where high numbers of violations have not been addressed.  
- [Housing Maintenance Code Complaints and Problems](https://data.cityofnewyork.us/Housing-Development/Housing-Maintenance-Code-Complaints-and-Problems/ygpa-z7cr/about_data)
  - +14M records (each row is a problem reported by a complainant)
- [Housing Maintenance Code Violations](https://data.cityofnewyork.us/Housing-Development/Housing-Maintenance-Code-Violations/wvxf-dwi5/about_data)
  - +9M records (each row is a violation)
  - Violations are issued in four classes: Class A (non-hazardous), Class B (hazardous), Class C (immediately hazardous) and Class I (information orders).
  - Includes when Violations went into effect
- [Building Table (record of all relevant buildings)](https://data.cityofnewyork.us/Housing-Development/Local-Law-44-Building/hu6m-9cfi/about_data)
  - 3K records (each row is a building)
- [Fee Charges](https://data.cityofnewyork.us/Housing-Development/Fee-Charges/cp6j-7bjj/about_data)
  - 93K records (each row is a fee charged to owners by agency)
- [Registration Contacts](https://data.cityofnewyork.us/Housing-Development/Registration-Contacts/feu5-w2e2/about_data)
  - 746K records (each row is an organization or individual that owns a building)

## Tech stack used
Google Cloud Tools

App Engine

Google Cloud Services

Cloud Composer Google’s version of Airflow

Big Query

DBT/Airflow for Data Quality Checks and Orchestration

Looker

## Summary
