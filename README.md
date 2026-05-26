# Scales of Justice: Race, Implicit Bias, and Mock Juror Decision-Making

**Author:** Leela Addepalli  
**Institution:** Washington and Lee University  
**Course:** CBSC 363 – Advanced Methods: Language, Culture and Emotion  
**PI:** Dr. Holly Shablack  
**Collaborators:** Lainie Pliant, Paul Mitsopolous

---

## Overview

This project investigates whether race, social desirability, and age bias influence mock juror decision-making — and whether those effects persist even when participants are given legally complete, balanced case materials.

Participants (n = 132) were recruited via Prolific and randomly assigned to one of three experimental groups. Each evaluated one or two fictional criminal cases in which defendant race was systematically varied using validated photographs from the Chicago Face Database. The study was designed to detect:

1. **Social desirability effects** — whether white jurors convict Black defendants at higher rates after first convicting a white defendant, in an effort to appear racially impartial
2. **In-group bias** — whether non-white jurors acquit Black defendants at higher rates
3. **Adultification bias** — whether participants overestimate the age of Black defendants, as documented in Goff et al. (2014)

---

## Research Design

| Group | Defendant 1 | Defendant 2 | Purpose |
|-------|-------------|-------------|---------|
| A | White | Black | Test social desirability effect |
| B | Black | Black | Control for racial contrast |
| C | — | Black | Single-exposure control |

All case materials used fictional Virginia criminal records and court arguments. Images were drawn from the Chicago Face Database, selected for a mean age rating of 18 to enable measurement of adultification bias.

---

## Key Findings

- **Verdict patterns showed directional trends consistent with social desirability effects.** In Group A, guilty verdicts for the Black defendant (29.5%) exceeded those for the white defendant (20.5%). In Group B, guilty verdicts for the second Black defendant rose sharply to 42.5% from 12.5% for the first — suggesting that the absence of racial contrast reduced social desirability motivation.
- **ANOVA results were statistically non-significant** across all main effects and interactions, likely due to limited statistical power (n = 132) and a racially skewed sample (73% white).
- **Near-significant interactions** (p = .105–.161) between participant race and race group on culpability ratings suggest trends worth investigating with a larger, more diverse sample.
- **In-group acquittal bias among non-white participants was not detected**, likely a function of insufficient sample size rather than absence of the effect.

---

## Repository Structure

```
scales-of-justice/
│
├── Final_Analysis.Rmd        # Full analysis pipeline: data cleaning, recoding,
│                             # ANOVA models, and visualizations
│
├── Scales_of_Justice.pdf     # Complete research paper with methodology,
│                             # results tables, and figures
│
└── README.md                 # This file
```

> **Note:** Raw data (`final clean data.csv`) is not included in this repository to protect participant confidentiality in accordance with IRB protocols.

---

## Methods & Tools

- **Platform:** Qualtrics survey, Prolific recruitment
- **Language:** R
- **Key packages:** `tidyverse`, `ggplot2`, `ez` (ezANOVA), `psych` (EFA), `apaTables`, `Hmisc`, `ungeviz`
- **Statistical approaches:**
  - Data wrangling and recoding (Likert scale items, age estimation cleanup, participant filtering)
  - Exploratory Factor Analysis (EFA) to assess the latent structure of the criminal culpability scale
  - Two-way and three-way between-subjects ANOVAs using `ezANOVA`
  - Violin plots with crossbar means and bootstrapped confidence intervals for data visualization

---

## Analysis Highlights

### Data Pipeline
Raw Qualtrics exports required substantial cleaning before analysis: filtering out survey previews and non-consenting participants, recoding five-point Likert items to numeric scores, handling free-text age responses, computing composite criminal culpability scores, and restructuring the dataset from wide to long format using `pivot_longer` for mixed-model compatibility.

### Modeling Approach
Separate ANOVAs were run for Defendant 1 (varying race: white vs. Black across groups) and Defendant 2 (Black across all groups), with participant race, defendant race/race group, and age estimation accuracy as between-subjects factors. A three-way model including age accuracy was added to test whether adultification interacted with culpability judgments.

### Visualization
Custom violin plots with jittered data points, red crossbar means, and black confidence interval error bars were used to display distributional variation in criminal culpability ratings across participant race and experimental group conditions.

---

## Limitations

- **Sample size:** n = 132 is underpowered for detecting small effect sizes in multi-way factorial designs
- **Sample composition:** 73% white participants limits subgroup analysis for non-white jurors
- **Online context:** Prolific-based mock juror studies lack the social dynamics of real deliberations
- **Static stimuli:** Photographs and text case summaries limit ecological validity compared to video or in-person courtroom simulations

---

## Policy Relevance

Findings contribute to the empirical literature on implicit bias in legal decision-making, with implications for jury selection procedures, juror bias training, and structural interventions in criminal proceedings following *Peña-Rodriguez v. Colorado* (2017). The study's focus on social desirability as a suppressor of implicit bias offers a novel lens for understanding racial disparities in verdict outcomes.

---

## References

Goff, P. A., Jackson, M. C., Di Leone, B. A. L., Culotta, C. M., & DiTomasso, N. A. (2014). The essence of innocence: Consequences of dehumanizing Black children. *Journal of Personality and Social Psychology, 106*(4), 526–545.

Hunt, J. S. (2015). Race, ethnicity, and culture in jury decision making. *Annual Review of Law and Social Science, 11*(1), 269–288.

Lynch, M., & Haney, C. (2011). Mapping the racial bias of the white male capital juror. *Law & Society Review, 45*(1), 69–102.

Mitchell, T. L., Haw, R. M., Pfeifer, J. E., & Meissner, C. A. (2005). Racial bias in mock juror decision-making: A meta-analytic review. *Law and Human Behavior, 29*(6), 621–637.

Ma, D. S., Correll, J., & Wittenbrink, B. (2015). The Chicago Face Database. *Behavior Research Methods, 47*(4), 1122–1135.
