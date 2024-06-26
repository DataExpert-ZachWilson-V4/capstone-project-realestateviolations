# Overview
Housing authorities in large cities track violations related to health, safety, and other concerns. However, due to a fragmented landscape with diverse stakeholders, communication gaps often occur. Public agency best efforts to notify owners of complaints are often insufficient due to ownership changes, management changes, or shortcomings in fulfilling tenant obligations. These gaps lead to delays that harm tenants by not addressing their issues promptly and hurt owners who unknowingly accrue fines from unaddressed violations. Our goal is to address this by implementing a subscription model for updates on specific properties, improving information flow, and enhancing the accessibility and user-friendliness of public data sets.

We aim to improve information flow to enable more effective use of public data sets, flag chronically delinquent properties as indicators of poor management, and notify building owners/operators of new violations. These enhancements are highly valuable and urgently needed due to the affordable housing and broader real estate industry's slow adoption of new technology.

## Datasets
We decided to start small with the largest housing authority in North America. The New York City Department of Housing Preservation and Development (HPD) in New York City, NY.
The city of New York provides access to public datasets containing HPD complaints and violation information. This Agency also enforces the City's Housing Maintenance Code, which covers Life Health Saftey topics including heat, hot water, mold, pests, gas leaks, fire safety and any conditions observed to not comply with applicable housing laws.
We aim to collate this data in a presentable way that makes it easy to notify owner-operators of violations, and for future tenants to make informed renting decisions based on where high numbers of violations have not been addressed.

The datasets we chose to give context to are as follows:
- [Housing Maintenance Code Complaints and Problems](https://data.cityofnewyork.us/Housing-Development/Housing-Maintenance-Code-Complaints-and-Problems/ygpa-z7cr/about_data)
  - +14M records (each row is a problem reported by a complainant)
- [Housing Maintenance Code Violations](https://data.cityofnewyork.us/Housing-Development/Housing-Maintenance-Code-Violations/wvxf-dwi5/about_data)
  - +9M records (each row is a violation)
  - Violations are issued in four classes: Class A (non-hazardous), Class B (hazardous), Class C (immediately hazardous), and Class I (information orders).
  - Includes when Violations went into effect
- [Building Table (record of all relevant buildings)](https://data.cityofnewyork.us/Housing-Development/Local-Law-44-Building/hu6m-9cfi/about_data)
  - 3K records (each row is a building)
- [Fee Charges](https://data.cityofnewyork.us/Housing-Development/Fee-Charges/cp6j-7bjj/about_data)
  - 93K records (each row is a fee charged to owners by agency)
- [Registration Contacts](https://data.cityofnewyork.us/Housing-Development/Registration-Contacts/feu5-w2e2/about_data)
  - 746K records (each row is an organization or individual that owns a building)

## Data model
The data from the city of New York tracks all violations but overwrites most records and their timestamps when there are updates. This Type 1 SCD approach allows for no history to be observed as far as, how long violations took to process, how long violations have been open, or how frequently violations are reported. We aim to remedy this issue to gain and provide powerful insights from the data using the cumulative table design approach to begin modeling the slowly changing dimension with a Type 2 approach. 

In doing so, we'll be able to derive intervals of time when violations were open and whether they have been sufficiently resolved or are being affected by larger scale systematic issues that cause them to reoccur -- bucketing by violation type will give us analytics on violation resolutions by type as well as other actionable metrics that we wish to present on a dashboard for tenants, current owners, or future owners of NYC real estate. 

Watching for changes in when violations are opened and/or closed, will allow for owner/operators to be notified that their address has been affected by a violation, and help to close the communication gap.

## Intended Tech Stack
We have two proposed architectures, both composed using Google's tech stack.

### Batch Only
  - App Engine
  - Cloud Storage
  - Cloud Dataproc
  - Cloud Composer
  - Big Query
  - Looker
  - dbt
  
### Batch + Real-time (We are looking into ways to add a real-time component)
  - Batch only services, plus:
  - Cloud Pub/Sub
  - Cloud Dataflow

![data tech stack](https://github.com/DataExpert-ZachWilson-V4/capstone-project-realestateviolations/assets/157633808/b35f8205-6655-458e-b54f-86b64376c43d)
