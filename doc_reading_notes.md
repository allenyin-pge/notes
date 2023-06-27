# Utility Standard: TD-4810S

This standard describes the PGE gas Transmission Integrity Management Program (TIMP)

## Intro

- This standard takes precendence over other programs cited.
- All revisions to program needs to be approved by Senior Director of Gas Transmission

### Personnel

- Senior director of gas transmission (GT): #TODO: Who is this?
- Principal asset management specialist: #TODO: Who is this?
- Supervisor of GT program
- Business analyst:
    - "Provides data analysis and validation support to ensure data processes and data systems meet IM requirements" -- #TODO: What are the IM requirements for data processes and systems?
- ...
- Risk Management Engineering Supervisor: "Performs continual evaluation (CE) following assessments or transmission pipeline incidents" -- this is Ian Hom?
- ...
- Integrity Data Specialist, Risk Analyst, and Data Scientist: Me, lol

### Class and Consequence Area

- high consequence areas (HCAs): specific locales where a release could have the most significant adverse consequences on people. Segments located within HCAs are known as covered segments.
    - Consequence measured in terms of potential damage
    - Consequence area and class designations, and consequence designation date must be maintained in GIS systems.

## Threat Types

ASME identifies NINE threat types to steel transmission pipelines
- Time-dependent
- Resident: Also applies to plastic transmission pipes
- TIme-independent: Also applies to plastic transmission pipes

Data used for threat identification must be documented in GIS database.

Process:
- Manager of TIMP risk management reviews and concurs with all applicable procedures.
- Risk management engineering supervisors are responsible for the implementation of the threat identification process for assigned threats.
- Risk management engineers are responsible for providing risk management expertise and support for the annual threat identification process.
- Integrity data specialists are responsible for performing GIS data integration in support of threat identification.

## Risk Assessment

- Must perform risk assessment on all steel and plastic transmission pipelines annually
- Gather data -> validate data -> integrate date -> analyze risk -> validate risk results
- Data sources: "Utility Procedure TD-4810P-01, Attachment 2, provides a detailed list of data sources used during the risk assessment process."
- Data integration: "Field data is captured with global positioning system (GPS) coordinates, historic mileposts, location descriptions, or addresses that can be geo-referenced."
  - "An information technology (IT) support team is engaged annually to provide database infrastructure and programming support for data integration, risk calculation, threat identification, and roll-up of risk and threat results"
- Risk assessment: "All equipment, appurtenances, and features along the pipeline are considered a part of the segment and may contribute to the evaluation of risk for the entire segment."
- Validation of risk assessment results: "The annual validation includes three steps: validation of data integration, validation of risk calculation, and steering committee review by SMEs."

## Continual Evaluation

At the conclusion of each assessment, a post-assessment integrity report must be developed to establish reassessment intervals, identify new threats, and acceptable P&M measures, and perform CE.
- TD-4810P-17: Implementation procedure
- TD-4819P-01: Assigning reassessment intervals procedures

# Utility Procedure: TD-4810P-01 -- Attachment 3, Transmission Integrity Management Program Risk Algorithm for Steel Pipe

Documentation for the current risk evaluation algorithm

## Calculating and Communicating Risk Results

1. Quantitative values of failure likelihood and estimates of consequences is done for each pipeline "dynamic segment", where segment is defined as __discreet__, __contiguous__ segment of pipeline where all variables used in calculation (for failure likelihood OR consequences) are held constant.
    - So the number of segments would change with time...right?
2. Risk is expressed as `failure likelihood x consequences`.

### Risk Methodology

Risk = Product(LOF, COF)

Units are:
- Risk = Impacted occupants per mile-year
- LOF_R = Ruptures/mile-yr
- LOF_L = SIF/mile-yr, SIF=Significant Injuries or Fatalities

Question -- Equation 1 second term, if LOF_L is converted to ruptures/mile-yr, why have separate term of COF_L??

### Other sections...

So many questions, notes in PDF itself..

### General thoughts

- The additive form of the threat-interaction formula doesn't seem to make sense.
- Low-hanging fruits and testing of data-driven approaches are the corrosion threats, because they are currently calculated from ILI data analytically, possible to derive a more accurate model easily.
- In a lot of the formulas where the scores are assigned based on threshold level, LOW score = good condition, but for susceptibility, HIGH score = bad. There is a lot of INVERSION of scale going on...
- Then there are "credit" factors, where HIGH score = good or bad, depending on who it's applying to
- When ILI data is available, the Probability of Exceedance calculations is statistical and seems well-grounded.
    - **IMPORTANT**: ILI availability gates which model is to be used

### Third-party damage (TPD)

- TPD is unique in that it causes significant ruptures historically.
- PGE data instead of industry rates is used to establish baseline numbers.
- Landuse has been determined as major factor for TPD likelihood

### Consequence of Failure (COF) assessment

- Unit is "number of occupants impacted" or "Impacted Occupancy Count" (IOC)
- Different type of consequence, including environmental loss, is converted to IOC via conversion factor and added (wtf how?!)

#TODO: Make flow chart of how the calculations feed into each other...
- How are these scores in charts determined...?