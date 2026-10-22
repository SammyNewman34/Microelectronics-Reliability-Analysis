# Microelectronics Reliability Analysis

## Project Overview

This project investigates the reliability of two semiconductor components used in an electric scooter motor-control system:

- **Silicon controller chip** fabricated using a 65 nm process.
- **Gallium nitride (GaN) power transistor module.**

Using accelerated life-test data, the project develops time-to-failure (TTF) models for both components and evaluates how operating voltage and temperature affect long-term system reliability.

The analysis combines Weibull statistical modeling, compact lifetime-model fitting, degradation analysis, and voltage–temperature reliability predictions.

## Project Objectives

The main objectives of this project were to:

- Explain series-system reliability and its implications for electronic systems.
- Analyze silicon time-to-failure data under nine voltage and temperature conditions.
- Extract Weibull shape and scale parameters and calculate mean time to failure (MTTF).
- Develop compact lifetime models for the silicon controller and GaN power transistor.
- Estimate GaN time to failure based on a 20% increase in on-state resistance (RDS).
- Evaluate system reliability across a range of operating voltages and temperatures.
- Identify the limiting component and determine the operating region that meets the specified reliability requirement.

## Methodology

### 1. Silicon Reliability Analysis

Silicon failure-time samples were analyzed at three voltage levels (1.0 V, 1.2 V, and 1.4 V) and three temperatures (100°C, 120°C, and 140°C).

A two-parameter Weibull distribution was fitted to each test condition. The shape parameter (beta) and scale parameter (theta) were extracted, and the mean time to failure was calculated for each condition.

The resulting MTTF values were used to fit the following compact lifetime model:

$$
TTF_{Si}(V,T)=A_{Si}\exp\left(\frac{E_{a,Si}}{kT}\right)\exp(-\gamma_{Si}V)
$$

### 2. GaN Degradation and Lifetime Modeling

The GaN analysis used drain-source resistance (RDS) measurements collected over time at different voltages and temperatures.

Time to failure was estimated as the time at which RDS increased by 20% relative to its initial value. These estimates were used to fit the following lifetime model:

$$
TTF_{GaN}(V,T)=A_{GaN}V^{-\gamma_{GaN}}\exp\left(\frac{E_{a,GaN}}{kT}\right)
$$

The fitted parameters describe the modeled dependence of device lifetime on voltage and temperature.

### 3. System Reliability Prediction

The fitted component models were used to evaluate reliability across operating temperatures from 10°C to 200°C and the voltage ranges specified in the project instructions.

The system's effective time to failure was defined as the minimum of the two component TTF values:

$$
TTF_{sys}(V,T)=\min\left(TTF_{Si}(V,T),TTF_{GaN}(V,T)\right)
$$

System reliability was evaluated using:

$$
R(t)=\exp\left(-\frac{t}{TTF_{sys}(V,T)}\right)
$$

The voltage–temperature analysis was used to examine the reliability boundary, identify operating conditions that meet the specified target, and determine which component limits system performance.

## Reported Model Parameters

The final report presents the following fitted parameters:

| Parameter | Silicon Controller | GaN Transistor |
|---|---:|---:|
| Pre-exponential factor, A | 122.325 | 317057.546 |
| Activation energy, Ea (eV) | 0.5254 | 0.3602 |
| Voltage exponent, gamma | 5.0231 | 5.0774 |

These values are reported in the project. The pre-exponential factors depend on the units and conventions used in the respective lifetime models.

## Tools and Techniques

- **Microsoft Excel** — data analysis, calculations, model fitting, and reliability sweeps.
- **Weibull analysis** — statistical characterization of silicon failure times.
- **Nonlinear parameter fitting** — extraction of compact lifetime-model parameters.
- **Degradation analysis** — estimation of GaN time to failure from RDS measurements.
- **Reliability modeling** — evaluation of operating conditions and identification of the limiting component.

## Repository Contents

```text
Microelectronics-Reliability-Analysis/
├── README.md
├── report/
│   └── microelectronics_reliability_report.pdf
└── data/
    └── reliability_test_data.xlsx
```

### Project Files

- [**Technical Report (PDF)**](report/microelectronics_reliability_report.pdf) — detailed analysis, methodology, and results.
- [**Reliability Test Data (Excel)**](data/reliability_test_data.xlsx) — workbook containing the project data and analysis.

GitHub does not render Excel workbooks as interactive spreadsheets inside a README. The workbook can be accessed through the link above and downloaded or opened in a compatible spreadsheet application.

## Limitations and Notes

The analysis is based on accelerated life-test data and the lifetime models fitted in the project. Predictions outside the measured test conditions depend on the assumptions and validity of those models.

The numerical results should therefore be interpreted as model-based reliability estimates rather than guarantees of field performance.

## Academic Project

Completed as part of a microelectronics reliability engineering course.
