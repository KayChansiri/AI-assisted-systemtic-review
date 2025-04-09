#  LLM-Assisted Systematic Review: Structured Classification with Flexible Reasoning
This project uses a structured prompting framework with Large Language Models (LLMs) like GPT-4o to assist in the abstract screening phase of a systematic review. The design aims to reduce false negatives while maintaining high interpretability and alignment with predefined inclusion criteria.

## Overview

Systematic reviews are essential for evidence-based decision-making but are time-consuming and prone to human inconsistency. This project introduces a structured yet flexible LLM-powered classification method to screen studies—particularly abstracts—based on multiple eligibility criteria.

Unlike classic Chain-of-Thought (CoT) prompting, our approach uses rule-based reasoning with inference flexibility, enabling the model to make human-like decisions while mitigating exclusion errors in ambiguous cases.

## Core Features

* Structured classification with 8 eligibility criteria and corresponding exclusion codes
* JSON-formatted outputs with decision logs
* Rule-based reasoning using flexible interpretation rules
* Lean-toward-inclusion logic to minimize false negatives
* Built-in error handling and result logging
* Temperature set to 0 for consistent decision-making

## Eligibility Criteria Used by the Model

* Empirical Research: Based on primary data.
* Publication Date: 2008 or later.
* Youth Population: Focused on individuals aged 13–25.
* Homelessness-Related: Addresses youth homelessness or housing instability.
* OECD Country: Study conducted in an OECD country.
* Intervention Described: Includes a program, service, or intervention.
* Effectiveness Reported: Presents outcomes or impact.
* Implementation Reported: Describes application, design, or delivery.
* Exclusion Codes
X-0: Not empirical research
X-1: Published before 2008
X-2: Target population not youth
X-3: Not homelessness related
X-4: Not in OECD country
X-5: No program/intervention
X-6a: No effectiveness reported
X-6b: No implementation reported

## How It Works

The script:

* Loads metadata from an Excel file (title, abstract, year, journal, author, affiliation, keywords).
* Sends a prompt to GPT-4o with structured inclusion criteria and interpretation guidance.
* Receives a JSON output with:
* A list of decisions per criterion (Yes or No (X-code))
* A final decision (Yes/No)
* Explanation (if No)
* Saves results to a new Excel file with added columns.

## Getting Started

1. Clone the Repository
2. Install Dependencies
3. Add Your OpenAI Key: Replace "INSERT YOUR KEY" with your actual API key inside screen_studies.py.
4. Run the Script

## Design Notes

Not Classic CoT: This is not a traditional step-by-step Chain-of-Thought prompt. Instead, it uses rule interpretation and structured JSON outputs for practical classification tasks.
False Negative Reduction: When ambiguity exists but the study broadly aligns with inclusion goals, the model is instructed to favor inclusion.
Temperature = 0: Ensures deterministic outputs for reproducibility.

## Limitations

LLM output is only as reliable as the prompt design and study metadata.
Human review is still recommended, especially for borderline cases or parsing errors.
GPT-based reasoning may fail to interpret complex domain-specific jargon without additional training or prompt tuning.

## Maintainer

Dr. Kay Chansiri
Email: kchansiri@chapinhall.org


