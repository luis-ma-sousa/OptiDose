# OptiDose

> **Improved surgical survival from 0% to 60% using predictive modeling when standard protocols failed**

**Building predictive models to solve undocumented anesthesia sensitivity in Parkinson's disease mouse models**

---

## The Problem

Our lab hit a wall: transgenic (Tg) Parkinson's disease (PD) mice were dying during brain surgeries. All of them.

We perform stereotaxic surgeries to deliver gene therapy vectors (AAV) directly into the substantia nigra, a brain region critical for dopamine production and heavily affected in PD. The goal: test whether restoring specific proteins can slow or reverse disease progression.


<img width="1134" height="716" alt="Screenshot 2025-10-22 at 15 45 02" src="https://github.com/user-attachments/assets/8a019116-7175-4bec-8d0c-7439b7184691" />

*Precise 3D targeting for gene therapy delivery to the substantia nigra (shown in red). Requires optimal anesthesia for sub-millimeter accuracy. Created with BioRender.*

Standard anesthesia protocols (ketamine + medetomidine) work fine for healthy control mice, but **PD animal models have significantly higher anesthesia sensitivity and it's very poorly documented in the literature.**

This was a serious problem because:
- Tg animals take 22 weeks to breed and raise until surgery timepoint
- Each failed surgery meant months/years of setback
- We were burning through irreplaceable animals
- The research project was stalling

We needed a solution, fast.

---

## The Solution

I built a predictive model that calculates personalized anesthesia doses based on animal weight, genotype (Wild-type as controls, Tg as diseased), and type of diet (disrupted metabolism impacts anesthesia efficacy). The key aim: let the data tell us what the literature couldn't.

<img width="3568" height="2366" alt="survival_analysis" src="https://github.com/user-attachments/assets/fbe5872e-3b9e-43fc-a090-fa21e385ef18" />

### How It Works

**Real-time dosing:**
1. Input animal characteristics (weight, genotype, diet)
2. Model predicts optimal anesthesia dose for 90%+ survival probability
3. Surgeon administers calculated dose
4. Record outcome and update model

<img width="4738" height="3562" alt="Tg NCD Log regression survival vs anesthesia vs weight_oct25" src="https://github.com/user-attachments/assets/523bf79d-a837-4a15-9964-0ee95d8ded98" />

**Continuous learning:**
Each surgery makes the model better. Started with limited data, now refined across 68+ procedures.

---

## Results

**For Tg Animals (the critical need):**
- Went from 0% survival to 60%+ after implementing the model
- Finally achieved successful surgeries in this high-risk group
- Enabled the research to actually proceed

**For All Animals:**
- Created standardized, evidence-based protocols
- Reduced unnecessary deaths across all experimental groups
- Saved months of breeding time and research delays
- Generated reproducible dosing guidelines where none existed

**Impact Metrics:**
- Saved ~€2,500 in replacement animal costs (10 animals × €250 each)
- Prevented +9 months of breeding delays (full duration of experiments)
- Reduced failed surgeries by 60%

**Bonus:** Documented anesthesia sensitivity in PD models with specific criteria, filling a real gap in the literature.

---

## Why This Matters

**Scientific Impact:**
- Solved a poorly explored problem blocking PD research
- Created reusable protocols now being adopted by other groups
- First documented characterization of anesthesia sensitivity in this specific PD model
- Demonstrated how data-driven approaches work when standard methods fail

**Practical Impact:**
- Saved significant time and resources (fewer failed surgeries = fewer replacement animals)
- Improved animal welfare through optimized dosing
- Enabled research continuity that was previously stalled

**Technical Interest:**
- Built a model that works with small sample sizes (n>15 per group)
- Real-time predictions in high-stakes environment
- Continuous learning system that improves with use
- Transparent methodology that builds surgeon trust

---

## The Technical Approach

**The Challenge:** 
Almost zero existing data + small samples + life-or-death stakes = need of a simple, reliable, interpretable model

**The Solution:**
Logistic regression with group-specific models (Tg/WT × NCD/HFD)

**Why it works:**
- Reasonably reliable with n>15 samples per group
- Transparent predictions surgeons can trust
- Real-time calculations (<1 second)
- Improves continuously as data accumulates

## Key Features

**Survival Prediction Models**
- 3D visualizations showing safe dosing zones
- Group-specific optimization (WT vs Tg, NCD vs HFD)
- Confidence intervals for risk assessment

**Performance Tracking**
- Cumulative survival rates over time
- Protocol improvement visualization
- Continuous refinement metrics

**Analysis Pipeline**
- Automated data processing from surgical records
- Statistical validation and model diagnostics
- Publication-ready visualizations

---

## Key Insights

- **Tg animals are extremely anesthesia-sensitive** - requiring 20-30% doses compared to 110-125% for wild-type animals (4-5× less anesthesia needed)
- **Survival improvement in Tg animals: 0% → 60%** - a critical breakthrough enabling the research to proceed
- **High-fat diet (HFD) improves anesthesia tolerance** - increased weight from HFD allows animals (regardless of genotype) to better tolerate anesthesia
- Post-surgical monitoring confirmed **no animals dropped below 10% acceptable weight loss**, validating both anesthesia protocols and post-op care
- **Coordinate accuracy: ~30% error = 0.11mm deviation** - while percentage seems high, actual deviation is sub-millimeter and still within target area (substantia nigra pars compacta), which is excellent precision
- **Surgeon-specific performance tracking** - individual surgeons can identify exactly which checkpoints need improvement
- **Dose is the strongest predictor** (p=0.0219 for Tg NCD). Weight appears non-significant (p=0.2212) but acts as a hidden confounder since dose is weight-adjusted
- **Protocol optimization visible over time** - early surgeries (days 1-5) showed 0% survival, stabilizing at 35-45% after first protocol refinement (days 6-12), and increasing up to ~60% in later surgeries
- **Tg Model R² = 0.26** - not stellar, but sufficient to significantly increase survival from 0% to 60%

---

## Limitations

**Small Sample Size**
- Still relatively few observations, especially for Tg animals
- Limits statistical power

**Missing Predictive Factors**

Likely other variables could improve predictions:
- Fasting glycemia levels
- Body fat percentage/distribution
- Individual metabolic markers
- Energy expenditure variability
- Oxygen saturation differences

This likely explains the modest R² values.

**Not All Animals Survive**

Some deaths still occur despite optimal dosing, potentially due to:
- Individual tolerance variations
- Depth of anesthesia fluctuations
- Unmeasured biological factors

**Probabilistic Guidance**

Model provides probabilistic guidance, not guarantees - but increased survival from 0% to 60%, demonstrating real-world utility despite limitations.

---

## 📁 Repository Contents
```
OptiDose/
├── OptiDose.ipynb          # Complete analysis pipeline
├── Surgery summary.xlsx    # Anonymized surgical records (n=68)
└── README.md
```
  
---
## Skills Demonstrated

**Tech Stack:** Python | Pandas | NumPy | Statsmodels | SciPy | Matplotlib | Seaborn

**Data Science:**
- Statistical modeling with limited data
- Model validation and diagnostics
- Feature engineering and interaction terms
- Continuous learning systems
- Uncertainty quantification

**Domain Expertise:**
- Translational neuroscience
- Pharmacology/anesthesiology
- Experimental design
- Scientific communication
- Literature gap analysis

**Software Engineering:**
- Production model deployment
- Real-time prediction systems
- Data pipeline automation
- Version control and documentation

**Research Impact:**
- Problem identification in experimental setting
- Protocol development and optimization
- Cross-institutional collaboration potential
- Ethical research practices (animal welfare)

---

## Future Ideas

- Expand to other disease models with unknown anesthesia sensitivity
- Add Bayesian approaches for better uncertainty quantification with small samples
- Incorporate additional physiological markers as predictors
- Deploy across multiple institutions for larger-scale validation
- Reach 90%+ survival target through continued refinement

---

## The Bottom Line

Started with a critical problem (100% Tg mortality), no documented solutions, and limited data. Built a practical model that works in real-time and actually gets used. Now PD mouse surgeries succeed, research progresses, and we've contributed new knowledge to the field.

**This isn't just a portfolio project - it's a production system saving lives and enabling research.**

---

## 👨‍💻 Author

Luís Sousa — [LinkedIn](https://www.linkedin.com/in/luis-ma-sousa31) | [GitHub](https://github.com/luismasousa)

---

## 🔗 Related Projects

- **[DeepWalk](https://github.com/luismasousa/DeepWalk)** — ML classification of Parkinson's motor deficits using gait data
- **[BehaviourInSight](https://github.com/luismasousa/BehaviourInSight)** — Automated analysis of rodent behavioral tests

---

## 🙏 Acknowledgments

Thanks to the surgical team and lab members who contributed data and feedback throughout this project's development.
