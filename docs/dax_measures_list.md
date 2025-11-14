# DAX Measures List

This file lists sample measures used in the Alberta Childcare Compliance and Inspection Analysis dashboard. It is not a complete technical reference but a clear overview of the core logic.

Measure names match the Measures table in the Power BI model.

---

## Core Volume Measures

### Total Programs
Counts the distinct number of programs.

### Total Capacity
Sums the licensed capacity across all programs.

### Total Inspections
Counts all inspection records in the Inspections fact table.

### Inspections per Month
Counts inspections grouped by inspection month for trend analysis.

---

## Compliance Measures

### Compliant Inspections
Counts inspections where the compliance status is recorded as compliant.

### Non Compliant Inspections
Counts inspections where the compliance status is recorded as non compliant.

### Compliance Rate
Compliant Inspections divided by Total Inspections.

---

## Enforcement Measures

### Enforced Inspections
Counts inspections where an enforcement action is present.

### Enforcement Rate
Enforced Inspections divided by Total Inspections.

### Enforcement Rate Non Compliant Only
Enforced Inspections divided by Non Compliant Inspections.

This measure shows how often non compliant inspections lead to enforcement.

---

## Capacity Measures

### Avg Capacity per Program
Average capacity across programs, often viewed by program type or city.

These measures power the main cards, line charts, bar charts, and comparisons across the dashboard pages.

---

## Example of Additional DAX Created During Visualization Work

Some DAX expressions were created later in the build while I was designing the visuals.  
These measures were not part of the core calculations but were needed to group cities, shape filters, or build cleaner charts.

### City Category
I created this measure to categorize Alberta cities into Major City, Mid Sized City, and Other based on population size. It supports the program type and capacity visuals.

```
CityCategory =
SWITCH(
    TRUE(),
    'City'[Program City] IN {
        "CALGARY", "EDMONTON", "RED DEER", "LETHBRIDGE",
        "MEDICINE HAT", "FORT MCMURRAY", "GRANDE PRAIRIE"
    }, "Major City",
    'City'[Program City] IN {
        "AIRDRIE", "ST. ALBERT", "SHERWOOD PARK", "LLOYDMINSTER", "SPRUCE GROVE",
        "LEDUC", "OKOTOKS", "COCHRANE", "CHESTERMERE", "BROOKS", "WETASKIWIN",
        "CAMROSE", "STRATHMORE", "WHITECOURT", "HIGH RIVER", "DRAYTON VALLEY",
        "BEAUMONT", "SYLVAN LAKE", "FORT SASKATCHEWAN", "TABER", "STONY PLAIN",
        "VERMILION", "PONOKA", "WAINWRIGHT", "PEACE RIVER", "COLD LAKE",
        "HINTON", "BONNYVILLE", "LACOMBE", "WESTLOCK", "INNISFAIL", "EDSON"
    }, "Mid-Sized City",

    "Other"
)
```
This measure helped organize the visuals for city comparisons and made the analysis clearer without breaking the model.

