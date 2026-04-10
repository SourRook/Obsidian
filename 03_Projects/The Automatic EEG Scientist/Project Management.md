## Problem Statement

High-quality EEG data acquisition currently depends on trained experts. This approach of using a a trained technician to record data from each of hundreds of participants across dozens labs does not scale.

We need an automated, quantitative way to:

- Monitor EEG signal quality in real time
- Detect specific sources of noise (e.g. power line, high impedance at reference electrode)
- Recommend actions to correct source of noise
- Track how changes to our data acquisition protocol over time affect signal quality

## Abstract / High-Level Summary

This project aims to develop an **AI EEG Scientist** that automates key aspects of EEG data acquisition. The AI scientist is a real-time action recommendation system that continuously monitors incoming EEG signals, detects common and fixable failure modes, and recommends corrective actions to suppress these noise sources during data collection (e.g. “high source of line noise near participant”, “re-apply gel at Y”, “check impedance in ground / reference electrode, “move hair from channel X” )

A central component of this effort is the construction of a validation dataset containing labeled noise sources and objective signal quality metrics. This dataset will be used to train and validate the AI system, including estimating time constants for signal degradation and identifying critical points (e.g., impedance thresholds) at which neural signals become indistinguishable from the noise floor.

## **Major Milestones : Cumulative list of progress**

|14th Jan|Defined functionality of EEG recommender system|
|---|---|
|15th Jan|Designed experiment to collect validation dataset (effect of various noise sources on EEG signal quality)|
|16th|Collected and analysed first Pilot Experiment (P01) → no 15Hz component in EEG during visual flicker (15Hz)|
|19th|Collected and analysed second Pilot Experiment (P02) → neither stimulation frequency (15Hz) nor monitor refresh rate (48Hz) ****present in EEG|

## Strategies for successful time management

1. Course correction:
    - Do _**not**_ engage in tasks unrelated to project
    - Ensure that tangential tasks are authorised by Avery/Mehdi.
    - Always document any deviations from your plan.
2. Phonological loop:
    - Is this task directly related to the project?
    - If not → Either stop immediately or get authorisation.
3. 10 minute reflection:
    - Address anything that _deviated from plan_ and propose changes for next day
4. Midpoint Estimation:
    - For tasks longer than 2 hours, at midpoint, do a reflective check-in.
    - Out of scope? If so why?

## Project Overview

This project focuses on designing and validating a real-time EEG data quality monitoring system. Achieving this requires establishing reliable ground truth for the major factors that affect EEG signal quality. The first objective is to define a comprehensive taxonomy of common failure modes—including hardware issues (e.g., electrode placement, impedance, saline drying), environmental factors (e.g., electrical noise, humidity), and subject or setup variables (e.g., hair density, head shape). A dedicated validation dataset will then be constructed through pilot experiments in which these error conditions are intentionally induced and labeled, alongside control recordings in which such artifacts are minimal or absent.

The action recommendation system will comprise four integrated components.

1. **Failure mode classification**: a model capable of identify common sources of noise in real time.
2. **Action recommendation**: a ranking algorithm that proposes corrective actions based on the probability of each failure mode.
3. **Real-time monitoring**: continuous tracking of noise and signal quality metrics to
    1. Allow the experimenter to assess whether an intervention has improved data quality.
    2. Estimate how signal quality will degrade over time.
    3. Track set up time and environmental varaibles during acquisition (humidity, temperature, EEG device, experimentor, electrical / magnetic noise).
4. **Action logging**: structured prompts that require the user to log applied interventions, enabling the system to learn from historical actions and outcomes.

To minimize unnecessary interruptions the system should prioritize low false-positive rates and prompt data quality checks only at strategically intervals (e.g. every 30 minutes). In parallel, it will model signal quality degradation over time as a function of contextual variables provided by the user at the start of each recording, including humidity, head shape, cap or net model, saline or gel usage, reference and ground configuration, experimenter ID, hair density etc. These models will be used to define actionable thresholds (e.g., when saline should be reapplied) and time-based intervention recommendations.

## Critical Next Steps

### **Primary Aim**

Build a prototype **Automated EEG Scientist Dashboard** for real-time signal quality diagnostics

### **Key Objectives**

- [x] Implement three core metrics (src/metrics)
    - **Impedance + drift / time-to-noise-floor (Kalman SSM)**
    - **Line noise power (50 Hz peak vs sidebands)**
    - **Spatial coherence of line noise (phase resultant)**
- [ ] Develop classifiers for benchmarking (src/models)
- [ ] Benchmark metrics (src/tests)