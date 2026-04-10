# Design the protocol for EEG data collection

- Track setup time
- Log errors

---

## Make a list of common errors and categorize them:

### EEG hardware errors:

- electrode placement is off …

### Environment:

- electrical noise
- humidity levels
- etc

---

## Build a validation dataset of EEG sessions intentionally configured with common errors and label each instance.

- For each of the categories of error classes above, collect dataset with those “issues” present

**Example:**

- Several minutes of data with impedance issue due to improper electrode placement

---

### Recording targets

- Some amount (~20min) for each condition
- 5 min per head shape and per location
- Multiple subjects, you can recruit us as subjects

---

### Electrode-specific labeling

- For issues that are electrode specific, add the electrode id as an additional label
- This will be useful when suggesting an action:
    - “add saline solution to electrode X”

---

### Clean ground-truth dataset

- Also collect clean dataset we know is high quality for ground truth

---

## Goals (two-fold)

1. Notify the technician that there is an issue
    - We can’t have too many false positives because otherwise the technician will be intervening the entire day, that’s not good
    - We want to minimize the number of interventions (ROC curve is great for this)
    - Ideally we should rate each type of error with some degree of severity to properly quantify the need for an interruption
2. Categorize what that issue is to be as helpful as possible
    - We would send notification with recommended action

---

## Literature review

- Do a literature review on what methods exist out there to do real-time quality assessment
- Common methods of tracking

---

## Modeling roadmap

### Baseline

- Start with a very simple baseline to classify issues
- The baseline would then suggest actions to fix the issue
- Use the validation dataset collected in the previous step to quantify the accuracy / ROC curve of the model

---

### Model development iterations

- Develop v1 of the model
    - Figure out what helps improve the accuracy
- Develop v2 of the model
    - Figure out what fails to improve the accuracy
- Develop a final version of the model based on all the previous iterations

---

## Signal quality degradation modeling

- Estimate signal quality drop-off rates over time based on various factors like:
    - humidity
    - hair density
    - head shape
- Characterize expected trajectories and define thresholds for “bad.”

---

### Saline drying curves

- Curves for when saline is drying / signal quality as a function of saline freshness
- Give auto estimates of when to reapply saline given reasonable threshold of signal quality
- Determine what the reasonable threshold of signal quality is

---

## Scope clarification

**What this is not:**

- minimizing blinks
- muscle activity
- room electrical activity

Instead it’s immediately fixable things for the tech

---

## Predictive goal

- Goal would be able to predict when to reapply saline

---

## Automation

- We want to track in automated way if there are issues
- Automate alerts to techs that there are issues

---

## Optimization framework

- We want to build an optimization space so that we understand what actions to take to improve signal quality as much as possible

---

## Dashboard

- Dashboard will notify you that something is off with something like:
    - humidity
    - saline solution dried up
    - one electrode has a problem

---