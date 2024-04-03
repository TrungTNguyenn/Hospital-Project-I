
# Team 9 MIST 4610 Group Project 1



## Team Members

[Ainslie Noble](https://github.com/ainsliehn)


[Austin Pasley](https://github.com/apasley)

[Justin Leeds](https://github.com/justinleeds)


[Trung Nguyen](https://github.com/TrungTNguyenn)




## Problem Description:

Pretend you are the owner/operator of an emergency healthcare clinic needing to build a
relational database. You hired some students from the MIST 4610 class at the University of
Georgia to create the database for you. They need to know more about your organization to
identify which entities, attributes, and relationships are important for you. 
## Data Model:

Our model is based on the structure of a hypothetical 
24/7 emergency healthcare clinic. There are several essential tables.

The data model for the healthcare clinic encompasses multiple tables/entities, each interconnected through well-defined relationships to facilitate efficient data management and retrieval.

**Clinic-Patient Relationship (1:M):**

The Patient entity is linked to the Clinic entity through the EmergencyVisit table, representing a one-to-many relationship. Each emergency visit (recorded in the EmergencyVisit table) involves a specific patient, thereby establishing a relationship between patients and the clinic where the visit occurred. This relationship allows for tracking patient visits to the clinic and associating them with specific clinic locations.

**Clinic-Staff Relationship (1:M):**

The Staff entity is directly related to the Clinic entity, indicating a one-to-many relationship. This relationship allows for assigning staff to particular clinics, ensuring that staff information is associated with the respective clinic where they work. Various employees can be assigned to a single clinic.

**Patient-EmergencyVisit Relationship (1:M):**

The EmergencyVisit table maintains a one-to-many relationship with the Patient entity. Each emergency visit involves a specific patient, facilitating comprehensive record-keeping and continuity of care. One patient can have multiple emergency visits.

**Staff-EmergencyVisit Relationship (1:M):**

Similarly, the EmergencyVisit table is related to the Staff entity in a one-to-many relationship. Each emergency visit involves staff members who provide medical care, ensuring proper documentation of staff contributions to patient care. One staff member will handle multiple emergency visits.

**MedicalProvider-EmergencyVisit Relationship (1:M):**

Additionally, the EmergencyVisit table is associated with the MedicalProvider entity in a one-to-many relationship. This relationship allows for capturing details of medical providers associated with each emergency visit, facilitating coordination and communication between clinic staff and external healthcare professionals. Many different patients  during their emergency visits may utilize the same medical provider.

**EmergencyVisit-DiagnosticTest Relationship (1:M):**

The DiagnosticTest table is linked to the EmergencyVisit table in a one-to-many relationship. This relationship enables tracking diagnostic tests conducted during each emergency visit, ensuring accurate documentation of medical procedures and results. There may need to be several tests taken during a visit.

**EmergencyVisit-Prescription Relationship (1:M):**

Similarly, the Prescription table is related to the EmergencyVisit table in a one-to-many relationship. This relationship allows for recording prescription details within the context of specific emergency visits, ensuring proper medication management and documentation. A doctor may prescribe multiple medications/prescriptions during a single visit.

**EmergencyVisit-MedicalProcedure Relationship (1:M):**

The MedicalProcedure table is associated with the EmergencyVisit table in a one-to-many relationship. This relationship enables tracking medical procedures conducted during each emergency visit, facilitating documentation of patient care procedures. There may need to be multiple procedures done in a single visit.

**EmergencyVisit-Billing Relationship (1:1):**

The Billing table maintains a one-to-one relationship with the EmergencyVisit table. This relationship indicates that each visit is a separate instance with its billing id. billing information is associated with one emergency visit, ensuring accurate financial documentation and patient billing. There will only be one comprehensove bill for a single visit.

**InsuranceProvider-Billing Relationship (1:M):**

Additionally, the Billing table is related to the InsuranceProvider entity in a one-to-many relationship. This relationship allows for linking billing records to specific insurance providers, facilitating proper processing of insurance claims and reimbursement. One insurance agency can be associated with multiple bills.

**Staff-Prescription Relationship (1:M):**

The Prescription entity is related to the Staff entity in a one-to-many relationship. Each prescription is associated with the staff member who prescribed it, indicating a one-to-many relationship. This relationship allows for tracking which staff members are responsible for prescribing medications to patients, ensuring proper record-keeping of prescriptions.

**Patient-Prescription Relationship (1:M):**

Similarly, the Prescription entity is linked to the Patient entity in a one-to-many relationship. Each patient can have various prescriptions, indicating a one-to-many relationship. This relationship enables tracking medications prescribed to individual patients, facilitating medication management and patient care.

**FacilityEquipment-EmergencyVisit Relationship (1:M):**

The EmergencyVisit entity is related to the FacilityEquipment entity in a one-to-many relationship. Each emergency visit may involve the use of various pieces of medical equipment, indicating a one-to-many relationship. This relationship allows for tracking the equipment used during each emergency visit, ensuring proper maintenance and availability of equipment for patient care.

**IncidentLog-EmergencyVisit Relationship (1:M):**

Additionally, the EmergencyVisit entity is associated with the IncidentLog entity in a one-to-many relationship. Each emergency visit may result in incidents or accidents that require documentation, indicating a one-to-many relationship. This relationship facilitates recording incident details associated with each emergency visit, ensuring proper follow-up and resolution.

**Staff-Staff (Supervisor-Subordinate) Recursive Relationship (1:M):**

The Staff entity may have a recursive relationship involving supervisors and subordinates, representing hierarchical structures within the staff members of the clinic. In this recursive relationship, each staff member (e.g., a doctor) can be associated with one or more other staff members (e.g., nurse). This relationship enables tracking supervisory relationships within the clinic's staff hierarchy, ensuring a clear delineation of reporting structures and responsibilities.


<img width="780" alt="Screen Shot 2024-04-03 at 1 16 39 PM" src="https://github.com/TrungTNguyenn/Hospital-Project-I/assets/140082975/498abaed-9276-4bba-b81c-68f9c4f55ea3">



## Data Dictionary: 
[Data Dictionary](https://github.com/TrungTNguyenn/Hospital-Project-I/files/14826663/Data.Dictionary.pdf)

## Queries:
[Query Screenshots and Matrix](https://github.com/TrungTNguyenn/Hospital-Project-I/files/14846140/Copy.of.MIST.4610.Queries.pdf)

**Simple Queries**

SELECT *
FROM IncidentLog
WHERE natureOfIncident REGEXP 'Complaint';

***Returns all incidents that were listed as complaints.***
_A manager of the hospital would utilize this to ensure that the hospital would address these incidents and complaints to make sure that they don’t happen again, and they make use of it to determine the performance of their staff. This data can be referenced if a situation leads to legal issues or insurance claims._

SELECT *
FROM Patient
WHERE gender = 'F'
AND birthDate > '2002-01-01';

***Returns the patientID, first name, last name, birthday, gender, phone number, and medical histories of all female patients who were born after January 2002.***
_A manager would be interested in these query results because it could help quickly access each female patient’s exact information and medical history born after January 2002 so that no mistakes are made in misidentifying a person._

SELECT providerID, providerName
FROM MedicalProvider med
WHERE NOT EXISTS (SELECT *
FROM Prescription p
WHERE p.prescribingPhysician = med.providerID);

***Returns all doctors who have not written any prescriptions.***
_A manager would be interested in these query results because it would aid in distinguishing which doctors have not been diagnosing patients properly, or haven’t been as productive as other doctors. This may be helpful if another provider sees the patient again, and can see which provider prescribed the medication, and collaborate on the best treatment plan. This data can also be used to track a provider to see if they are overprescribing medications, as this is a liability. This would allow the managers to address the doctors to make sure there isn’t anything wrong or their patients are just all generally healthy._

SELECT AVG(cost) AS avgOverduePayments
FROM Billing
WHERE paymentStatus = 'Overdue';

***Returns the average total of all overdue payments.***
_A manager would be interested in these query results because it would help calculate the average total of overdue payments which would then be reported to the upper-level management so that they can address the overdue payments and try to push out emails and mail to get their payments or send the overdue payments to collections. This way the hospital can try to recoup their money._

**<u>Complex Queries</u>**

SELECT initialAssessment, fName, lName, birthDate
FROM EmergencyVisit
JOIN Patient
ON EmergencyVisit.patientID = Patient.patientID
WHERE birthDate > '2000-01-01'
ORDER BY birthDate ASC;

***Returns the patient’s initial assessment/reason for visit, first and last name, for all patients born after January 1st, 2000 in ascending order***
_A manager would be interested in these query results because it would help the doctors at the hospital distinguish exactly what problems need to be addressed and if their treatment is working._

SELECT fName, lName, results, dateTimeOrdered
FROM DiagnosticTest
JOIN EmergencyVisit
ON DiagnosticTest.emergencyVisitID = EmergencyVisit.visitID
JOIN Patient
ON EmergencyVisit.patientID = Patient.patientID
WHERE testType = 'ultrasound';

***Returns the first and last name of the patient who received an ultrasound. Also shows the results and the day/time it was ordered by the doctor.***
_A manager would be interested in these query results because it would help distinguish which patients received an ultrasound and which doctor ordered it at a certain time and date. This would help patients and doctors see if the pregnancy is going smoothly and spot out problems early on._

SELECT EmergencyVisit.patientID, COUNT(EmergencyVisit.patientID) AS VisitCount
FROM EmergencyVisit
JOIN Patient
ON EmergencyVisit.patientID = Patient.patientID
GROUP BY patientID
ORDER BY VisitCount DESC;

***Returns the total amount of times each patient has visited the clinic in descending order.***
_A manager would be interested in these query results because they could see which patients have had the longest amount of time spent at the hospital and could be responsive for certain patients/situations based on that. They could also figure out why the treatment is not working and the patient is continuing to come back._

SELECT Billing.paymentStatus, SUM(cost) AS totalCost, fName, lName, EmergencyVisit.patientID
FROM Billing 
JOIN EmergencyVisit
ON Billing.visitID = EmergencyVisit.visitID
JOIN Patient
ON EmergencyVisit.patientID = Patient.patientID
WHERE Billing.paymentStatus = 'Overdue'
GROUP BY EmergencyVisit.patientID
HAVING totalCost > 500
ORDER BY totalCost DESC;

***Returns the total amount overdue, first and last name, and patientID for each patient.***
_A manager would be interested in these query results because it would allow them to see exactly how much money is overdue from each patient. This would help send out overdue statements to each person._

SELECT p.patientID, p.fName, p.lName,
(SELECT AVG(prescriptionCount) FROM (SELECT COUNT(*)AS prescriptionCount
FROM Prescription prescript WHERE prescript.patientID = p.patientID
GROUP BY p.patientID) AS presciptCount) AS avgScripts
FROM Patient p
ORDER BY avgScripts DESC;

***Returns the average amount of prescriptions for each patient.***
_A manager would be interested in these query results because it would show how much each medicine inventory is needed in the hospital so that each patient has it and to see the frequency of medicine needed, or if they are being overprescribed._

SELECT SUM(Billing.cost) AS TotalCosts, YEAR(EmergencyVisit.arrivalDateTime) AS YearTotal
FROM Billing 
JOIN EmergencyVisit
ON Billing.visitID = EmergencyVisit.visitID
JOIN Clinic
ON EmergencyVisit.clinicID = Clinic.clinicID
WHERE Billing.paymentStatus = 'Paid'
GROUP BY YEAR(arrivalDateTime)
ORDER BY YEAR(arrivalDateTime) ASC;

***Returns the total amount of paid bills, sorted by each year, at all clinics.***
_A manager would be interested in these query results because they show revenue and the difference in unpaid balances. It can also be used for accounting purposes to make sure there aren’t any abnormalities in the total amount of paid bills._

