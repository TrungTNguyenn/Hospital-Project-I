
# Team 9 MIST 4610 Group Project 1



## Team Members

Ainslie Noble @ainsliehn

Austin Pasley @apasley

Justin Leeds @justinleeds

Trung Nguyen @TrungTNguyenn



## Problem Description:

Pretend you are the owner/operator of a emergency healthcare clinic needing to build a
relational database. You hired some students from the MIST 4610 class at the University of
Georgia to create the database for you. They need to know more about your organization to
identify which entities, attributes, and relationships are important for you. 
## Data Model:

Our model is based on the structure of a hypothetical 
24/7 emergency healthcare clinic. There are several essential tables.

The data model for the healthcare clinic encompasses multiple tables/entities, each interconnected through well-defined relationships to facilitate efficient data management and retrieval.

Patient-Clinic Relationship (1:M):

The Patient entity is linked to the Clinic entity through the EmergencyVisit table, representing a one-to-many relationship. Each emergency visit (recorded in the EmergencyVisit table) involves a specific patient, thereby establishing a relationship between patients and the clinic where the visit occurred. This relationship allows for tracking patient visits to the clinic and associating them with specific clinic locations.

Staff-Clinic Relationship (1:M):

The Staff entity is directly related to the Clinic entity, indicating a one-to-many relationship. This relationship allows for assigning staff to particular clinics, ensuring that staff information is associated with the respective clinic where they work.

EmergencyVisit-Patient Relationship (1:M):

The EmergencyVisit table maintains a one-to-many relationship with the Patient entity. Each emergency visit involves a specific patient, facilitating comprehensive record-keeping and continuity of care.

EmergencyVisit-Staff Relationship (1:M):

Similarly, the EmergencyVisit table is related to the Staff entity in a one-to-many relationship. Each emergency visit involves staff members who provide medical care, ensuring proper documentation of staff contributions to patient care.

EmergencyVisit-MedicalProvider Relationship (1:M):

Additionally, the EmergencyVisit table is associated with the MedicalProvider entity in a one-to-many relationship. This relationship allows for capturing details of medical providers associated with each emergency visit, facilitating coordination and communication between clinic staff and external healthcare professionals.

DiagnosticTest-EmergencyVisit Relationship (1:M):

The DiagnosticTest table is linked to the EmergencyVisit table in a one-to-many relationship. This relationship enables tracking diagnostic tests conducted during each emergency visit, ensuring accurate documentation of medical procedures and results.

Prescription-EmergencyVisit Relationship (1:M):

Similarly, the Prescription table is related to the EmergencyVisit table in a one-to-many relationship. This relationship allows for recording prescription details within the context of specific emergency visits, ensuring proper medication management and documentation.

MedicalProcedure-EmergencyVisit Relationship (1:M):

The MedicalProcedure table is associated with the EmergencyVisit table in a one-to-many relationship. This relationship enables tracking medical procedures conducted during each emergency visit, facilitating comprehensive documentation of patient care interventions.

Billing-EmergencyVisit Relationship (1:M):

The Billing table maintains a one-to-many relationship with the EmergencyVisit table. This relationship indicates that billing information is associated with each emergency visit, ensuring accurate financial documentation and patient billing.

Billing-InsuranceProvider Relationship (1:M):

Additionally, the Billing table is related to the InsuranceProvider entity in a one-to-many relationship. This relationship allows for linking billing records to specific insurance providers, facilitating proper processing of insurance claims and reimbursement.
These relationships form the backbone of the data model, enabling efficient management of patient care, staff coordination, billing processes, and external collaborations within the healthcare clinic. Each relationship serves a specific purpose in connecting relevant entities and ensuring comprehensive documentation and continuity of care for patients.

Prescription-Staff Relationship (1:M):

The Prescription entity is related to the Staff entity in a one-to-many relationship. Each prescription is associated with the staff member who prescribed it, indicating a one-to-many relationship. This relationship allows for tracking which staff members are responsible for prescribing medications to patients, ensuring proper attribution of medical interventions.
Prescription-Patient Relationship (1:M):

Similarly, the Prescription entity is linked to the Patient entity in a one-to-many relationship. Each prescription is associated with a specific patient, indicating a one-to-many relationship. This relationship enables tracking medications prescribed to individual patients, facilitating medication management and patient care.
Emergency Visit-Facility Equipment Relationship (1:M):

The EmergencyVisit entity is related to the FacilityEquipment entity in a one-to-many relationship. Each emergency visit may involve the use of various medical equipment, indicating a one-to-many relationship. This relationship allows for tracking the equipment used during each emergency visit, ensuring proper maintenance and availability of equipment for patient care.
Emergency Visit-Incident Log Relationship (1:M):

Additionally, the EmergencyVisit entity is associated with the IncidentLog entity in a one-to-many relationship. Each emergency visit may result in incidents or accidents that require documentation, indicating a one-to-many relationship. This relationship facilitates recording incident details associated with each emergency visit, ensuring proper follow-up and resolution.
Staff-Staff (Supervisor-Subordinate) Recursive Relationship (1:M):

The Staff entity may have a recursive relationship involving supervisors and subordinates, representing hierarchical structures within the staff members of the clinic. In this recursive relationship, each staff member (e.g., a supervisor) can be associated with one or more other staff members (e.g., subordinates). This relationship enables tracking supervisory relationships within the clinic's staff hierarchy, ensuring clear delineation of reporting structures and responsibilities.



## Data Dictionary:
## Queries:
