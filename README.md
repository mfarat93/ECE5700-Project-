# Pipette Pressure Curve Classification and Operator Decision Support

## Overview

This project uses a neural network to classify liquid handling pressure-vs-time curves into normal and abnormal pipetting events. It also includes an interactive user interface that simulates how an operator or automated liquid handling system could respond to those classifications in real time.

The goal is to detect issues such as empty aspiration, foamy samples, clots, or short dispenses from pressure curves and guide the next action based on the predicted event.

---

## Project Components

This project currently contains two main parts:

### 1. Model Training / Evaluation Code
This portion of the project:
- loads and preprocesses pressure curve data
- maps each curve to a pipetting event class
- trains a neural network classifier
- evaluates classification accuracy on held-out test data

### 2. Interactive Operator Decision Tool
This portion of the project:
- randomly selects a test pressure curve
- plots the curve
- runs inference using the trained model
- displays:
  - predicted label
  - true label
  - model confidence
- automatically cycles through normal events
- pauses on abnormal events and presents operator action buttons

This simulates how a liquid handler or operator-facing software could respond to pipetting anomalies in real time.

---

## Classes

The model predicts among the following pipetting event classes:

- `correct_aspiration`
- `correct_dispense`
- `empty_aspiration`
- `foamy_sample`
- `clot_aspiration`
- `clot_dispense`
- `short_dispense`

Normal curves:
- `correct_aspiration`
- `correct_dispense`

Error / intervention-required curves:
- `empty_aspiration`
- `foamy_sample`
- `clot_aspiration`
- `clot_dispense`
- `short_dispense`

---

## Example Workflow

1. A pressure curve is selected from the test set
2. The model predicts the pipetting event class
3. If the event is normal:
   - the curve is displayed
   - the UI waits a few seconds
   - the next curve is automatically processed
4. If the event is abnormal:
   - the curve is displayed
   - the UI pauses
   - the user is given action options based on the predicted error type

Example actions include:
- Reload Sample
- Skip Sample
- Bottom Touch-off
- Waste + Resample
- Eject Tip
- Re-Aspirate

---

## Repository Structure

Example structure:

```text
project/
│
├── Version_2_ECE57000_Project.ipynb            
├── 7 idividual pipette class curves                   
├── README.md
