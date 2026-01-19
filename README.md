# "Aadhaar Enrollment-to-Biometric Drop-off Analysis Across India"
## domain: "Public Policy | Data Analytics | Governance"
## organizer: "UIDAI Data Hackathon"
### objective: 
Analyze enrollment-to-biometric drop-offs in Aadhaar registration across Indian states to identify systemic gaps, age-wise variations, and state-level disparities using trivariate analysis.

## problem_statement:
Despite high Aadhaar enrollment volumes, a significant proportion of enrollments do not complete biometric capture. This project investigates where and to what extent enrollment-to-biometric drop-offs occur across Indian states and how these patterns vary by age group.

## datasets:
### source: "UIDAI Hackathon Datasets"
### types:
    - enrollment_data:
        columns:
          - age_0_5
          - age_5_17
          - age_18_greater
    - demographic_update_data:
        columns:
          - demo_age_5_17
          - demo_age_17_
    - biometric_update_data:
        columns:
          - bio_age_5_17
          - bio_age_17_
  ### common_dimensions:
    - date
    - state
    - district
    - pincode
    - state_clean

## methodology:
  data_ingestion:
    - Multiple large CSV files (~5 lakh rows per file) merged using pandas
  data_cleaning:
    - State names standardized using custom fix_map
    - Invalid and non-administrative entries removed
    - Final dataset restricted to 36 standardized states/UTs
  aggregation:
    - State-level aggregation for enrollment, demographic, and biometric data
    - Age group 0–5 excluded due to biometric eligibility constraints
  derived_metrics:
    - enrollment_5_plus
    - biometric_5_plus
    - dropoff_rate:
        formula: "(Enrollment - Biometric) / Enrollment"

## analysis:
  ### univariate:
    - Enrollment distribution
    - Biometric distribution
    - Age-group composition
  ### bivariate:
    - State-wise enrollment vs biometric comparison
    - Time-series trend analysis
  ### trivariate:
    - bubble_chart:
        x_axis: "Enrollment (Age 5+, log scale)"
        y_axis: "Drop-off Rate"
        bubble_size: "Biometric volume"
        color: "State"
    - heatmap:
        dimensions: "State × Age Group"
        metric: "Drop-off Rate"

## tools:
  ### programming_language: "Python"
  ### libraries:
    - pandas
    - numpy
    - matplotlib
    - seaborn
  ### environment:
    - Jupyter Notebook
    - Excel

## data_availability:
  ### notice: 
    The datasets used in this project were provided by UIDAI exclusively for the purpose of this hackathon. Raw and processed datasets are not publicly shared in this repository.
  ### repository_contains:
    - analysis_code
    - data_processing_logic
    - visualization_workflows

## key_takeaways:
  - Enrollment volume alone does not ensure biometric completion
  - Several high-enrollment states show systematic drop-off patterns
  - Trivariate analysis provides stronger diagnostic insight than
    univariate or bivariate approaches
