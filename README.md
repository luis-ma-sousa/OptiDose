# OptiDose

**Building predictive models to solve undocumented anesthesia sensitivity in Parkinson's disease mouse models**

## The Problem

Our lab hit a wall: transgenic (Tg) Parkinson's disease (PD) mice were dying during brain surgeries. All of them.

Standard anesthesia protocols (ketamine + medetomidine) work fine for healthy control mice, but **PD animal models have significantly higher anesthesia sensitivity - and it's very poorly documented in the literature.**

This was a serious problem because:
- Tg animals take 22 weeks to breed and raise until surgery timepoint. 
- Each failed surgery meant months/years of setback
- We were burning through irreplaceable animals
- The research project was stalling

We needed a solution, fast.

## The Solution

I built a predictive model that calculates personalized anesthesia doses based on animal weight, genotype (Wild-type as controls, Tg as diseased), and type of diet (disrupted metabolism impacts anesthesia efficacy). The key aim: let the data tell us what the literature couldn't.

### How It Works

**Real-time dosing:**
1. Input animal characteristics (weight, genotype, diet)
2. Model predicts optimal anesthesia dose for 90%+ survival probability
3. Surgeon administers calculated dose
4. Record outcome and update model

**Continuous learning:**
Each surgery makes the model better. Started with limited data, now it's refined across +65 procedures.

## Results

**For Tg Animals (the critical need):**
- Went from 0% survival to 60%+ after implementing the model
- Finally achieved successful surgeries!
- Enabled the research to actually proceed

**For All Animals:**
- Created standardized, evidence-based protocols
- Reduced unnecessary deaths
- Saved months of breeding time and research delays
- Generated reproducible dosing guidelines where none existed

**Bonus:** Documented anesthesia sensitivity in PD models with specific criteria, filling a real gap in the literature.

## Why This Matters?

**Scientific Impact:**
- Solved an poorly explored problem blocking PD research
- Created reusable protocols now being adopted by other groups
- Demonstrated how data-driven approaches work when standard methods fail

**Practical Impact:**
- Saved significant time and resources (fewer failed surgeries = fewer replacement animals)
- Improved animal welfare through optimized dosing

**Technical Interest:**
- Built a model that works with small sample sizes
- Real-time predictions in high-stakes environment
- Continuous learning system that improves with use

## The Technical Approach

**Challenge:** No existing data, small sample sizes, high stakes

**Solution:** Logistic regression with adaptive learning
- Separate models for each experimental group
- Weight and dose as primary predictors
- Interaction terms to capture complex relationships

**What makes it work:**
- Simple enough to be reliable with limited data
- Sophisticated enough to capture real biological variation
- Fast enough for real-time surgical decisions
- Transparent enough to build surgeon trust

**Tech Stack:** Python | Pandas | NumPy | Statsmodels | SciPy | Matplotlib | Seaborn

## Real-World Usage

This is a production system used before every surgery:

1. Calculate optimal dose pre-surgery
2. Surgeon references predictions during anesthesia
3. Track outcomes and recovery
4. Model automatically improves

## Key Features

**Survival Prediction Models**
- 3D visualizations showing safe dosing zones
- Group-specific optimization (WT vs Tg, NCD vs HFD)
- Confidence intervals for risk assessment

**Performance Tracking**
- Surgeon-specific metrics and benchmarking
- Recovery trajectory monitoring
- Continuous protocol improvement

**Analysis Pipeline**
- Automated data processing from surgical records
- Statistical validation and model diagnostics
- Publication-ready visualizations

## Key insights

- 

## Future Ideas

- Expand to other disease models with unknown anesthesia sensitivity
- Add other machine learning approaches as dataset grows
- Deploy across multiple institutions

## The Bottom Line

Started with a critical problem (100% Tg mortality), no documented solutions, and limited data. Built a practical model that works in real-time and actually gets used. Now PD mice surgeries succeed, research progresses, and we've contributed new knowledge to the field.

---

## 👨‍💻 Author

Luís Sousa — [LinkedIn](https://www.linkedin.com/in/luis-ma-sousa31) | [GitHub](https://github.com/luismasousa)

---

## 🔗 Related Projects

- **[DeepWalk](https://github.com/luismasousa/DeepWalk)** — ML classification of Parkinson's motor deficits using gait data
- **[BehaviourInSight](https://github.com/luismasousa/BehaviourInSight)** — Automated analysis of rodent behavioral tests
