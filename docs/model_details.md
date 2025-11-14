# Data Model Details

The model follows a star schema with Inspections as the central fact table and several dimension tables around it. The screenshot in the repository shows the exact layout used in Power BI.

---

## Fact Table

### Inspections

One row per inspection event.

Key fields  
- InspectionID  
- ChildcareInfoID  
- ComplianceID  
- EnforcementID  
- InReasonsID  
- Inspection Date  
- Remedy Date  

This table holds the measures for inspection counts, trends, compliance, and enforcement.

---

## Dimension Tables

### ChildcaresInfo

Program level information that connects inspections to the physical childcare programs.

Key fields  
- ChildcareInfoID  
- Program ID  
- Program Name  
- CityID  
- Program TypeID  
- Address and Postal Code  
- Day Care Y N  
- Out of School Care Y N  
- Preschool Y N  
- Phone Number  

This table links up to City and ProgramType and down to Inspections.

---

### City

City level lookup for grouping and geographic analysis.

Key fields  
- CityID  
- City AB   

This table filters ChildcaresInfo which then filters Inspections.

---

### ProgramType

Program classification lookup.

Key fields  
- TypeID  
- Type of Program  

This table filters ChildcaresInfo and then Inspections. It supports analysis by type of program and capacity distribution.

---

### InspectionReason

Lookup for inspection reasons.

Key fields  
- InReasonsID  
- Inspection Reason   

Used to analyze which reasons lead to more non compliance and enforcement.

---

### Enforcement

Lookup for enforcement actions.

Key fields  
- EnforcementID  
- Enforcement Action  

Used to analyze how often different enforcement actions are used.

---

### NonCompliance

Lookup for non compliance details.

Key fields  
- ComplianceID  
- Non Compliance  

Used to break down where programs are failing requirements.

---

## Relationships

The main relationships in the model

- ChildcaresInfo to Inspections  
  - ChildcareInfoID one to many into Inspections  

- City to ChildcaresInfo  
  - CityID one to many into ChildcaresInfo  

- ProgramType to ChildcaresInfo  
  - TypeID one to many into ChildcaresInfo  

- InspectionReason to Inspections  
  - InReasonsID one to many into Inspections  

- Enforcement to Inspections  
  - EnforcementID one to many into Inspections  

- NonCompliance to Inspections  
  - ComplianceID one to many into Inspections  

Filter direction flows from lookup tables into the Inspections fact table. This design keeps filter context clear, supports stable measures, and avoids circular relationships.

---

## Design Rationale

I chose this structure to

- separate program level and inspection level information  
- make measures like compliance rate and enforcement rate simple to define  
- keep slicers and filters responsive across all pages  
- support city, program type, and inspection reason analysis without complex DAX  

The star schema also makes the model easier for others to understand if they open the file in the future.
