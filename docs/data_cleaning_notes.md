# Data Cleaning Notes

This project started from one large dataset from the Government of Alberta. All cleaning and restructuring was done in Power Query before building the model in Power BI.

The main goal was to turn one tall table into a clear star schema with a central Inspections fact table and several related dimension tables.

---

## Splitting the Big Dataset into Tables

I reviewed all columns in the original dataset and grouped them into logical tables.


### Inspections (fact table)
Event level information for each inspection.

Fields include  
- InspectionID  
- ChildcareInfoID  
- Inspection Date  
- ComplianceID  
- EnforcementID  
- InReasonsID  
- Remedy Date  

### ChildcaresInfo
Core program level information.

Fields include  
- Program ID  
- ChildcareInfoID  
- Program Name  
- Program Address  
- CityID  
- Postal Code  
- Capacity  
- Program TypeID  
- Day Care Y N  
- Out of School Care Y N  
- Preschool Y N  
- Phone Number  

### City
Geographic information for each program.

Fields include  
- CityID  
- City AB  

### ProgramType
Classification of each childcare program.

Fields include  
- TypeID  
- Type of Program  

### InspectionReason
Reasons for inspections.

Fields include  
- InReasonsID  
- Inspection Reason  

### Enforcement
Types of enforcement actions.

Fields include  
- EnforcementID  
- Enforcement Action  

### NonCompliance
Details on non compliant findings.

Fields include  
- ComplianceID  
- Non Compliance  

---

## ID Creation and Integrity

Each table uses a clear primary key so relationships are stable.

- Program ID and ChildcareInfoID for program to inspection links  
- CityID and Program TypeID from lookup tables into ChildcaresInfo  
- EnforcementID, ComplianceID, InReasonsID from lookup tables into Inspections  

I checked that every key in the fact table matched a valid record in its dimension table and removed orphan records when needed.

---

## Standardization and Cleanup

While splitting into tables I also

- Cleaned text values for program type, inspection reason, and enforcement action  
- Converted date columns to proper Date type  
- Removed duplicate rows and null records from the original dataset 
- Filtered out rows with completely empty inspection or program information  

The end result is a clean set of tables ready for modeling and analysis.
