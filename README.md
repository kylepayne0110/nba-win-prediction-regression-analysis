# NBA Win Prediction with Regression Analysis

## 🎯 Project Overview

Built and evaluated multiple regression models to predict NBA team regular season wins using performance metrics from the FiveThirtyEight NBA Elo dataset. Analyzed 618 team seasons (1995-2015) and developed predictive models achieving **R² = 0.878**, enabling data-driven decision-making for coaching staff, player trades, and in-season strategy adjustments.

## 📊 Key Results

| Model | R² | Predictors | Key Insight |
|-------|-----|-----------|-------------|
| **Simple Linear Regression** | 0.823 | Average Elo rating | Strong single predictor (r = 0.907) |
| **Multiple Regression (2 vars)** | 0.837 | Avg points + Avg Elo | Modest improvement over simple model |
| **Multiple Regression (4 vars)** | **0.878** | Points, Elo, Point Diff, Elo Diff | Best predictive performance |

**Key Finding:** Point differential is the strongest predictor - each additional point of average margin increases expected wins by ~1.5 games.

## 🛠️ Technologies & Methods

**Programming & Tools:**
- Python
- Statistical analysis libraries
- Data visualization
- Jupyter Notebooks (assumed)

**Statistical Techniques:**
- Simple linear regression
- Multiple linear regression
- Pearson correlation analysis
- Scatterplot visualization
- Hypothesis testing (F-tests, t-tests)
- Model comparison and selection

**Statistical Methods:**
- Overall F-tests for model significance (α = 0.05)
- Individual t-tests for coefficient significance (α = 0.01)
- R² and adjusted R² for model fit evaluation
- P-value analysis for statistical significance
- Coefficient interpretation for practical insights

## 📈 Dataset Information

**Source:** FiveThirtyEight NBA Elo dataset (via Kaggle)

**Sample Size:** 618 NBA team seasons (1995-2015)

**Key Variables:**
- **Outcome:** Total regular season wins
- **Predictors:**
  - `avg_pts` - Average points scored per game
  - `avg_elo_n` - Average Elo rating (skill measure)
  - `avg_pts_differential` - Average point margin (positive = winning margin)
  - `avg_elo_differential` - Average Elo difference vs opponents

## 🔬 Models Developed

### Model 1: Simple Linear Regression ⭐
**Predictor:** Average Elo rating (relative skill)

**Equation:**
```
Predicted Wins = -128.25 + 0.1121 × (Average Elo Rating)
```

**Performance:**
- R² = 0.823 (explains 82.3% of win variation)
- Pearson correlation: r = 0.907 (very strong positive)
- P-value < 0.0001 (highly significant)
- F-statistic: Very large, confirming model utility

**Key Insight:** Raising Elo by 100 points projects ~11 additional wins

**Example Predictions:**
- Team with Elo 1550 → Expected 45 wins
- Team with Elo 1450 → Expected 34 wins

### Model 2: Multiple Regression (2 Predictors) ⭐⭐
**Predictors:** Average points scored + Average Elo rating

**Equation:**
```
Predicted Wins = -152.574 + 0.3497 × (Avg Points) + 0.1055 × (Avg Elo)
```

**Performance:**
- R² = 0.837 (explains 83.7% of variation)
- Both predictors significant at α = 0.01
- Points scored: t = 7.297, p < 0.01
- Elo rating: t = 47.952, p < 0.01

**Key Insight:** Elo remains stronger predictor, but points scored adds value

**Example Predictions:**
- Team scoring 75 pts/game, Elo 1350 → Expected 16 wins
- Team scoring 100 pts/game, Elo 1600 → Expected 51 wins

### Model 3: Multiple Regression (4 Predictors) ⭐⭐⭐ (Best Model)
**Predictors:** Points scored + Elo rating + Point differential + Elo differential

**Equation:**
```
Predicted Wins = 34.5753 + 0.2597 × (Avg Points) - 0.0134 × (Avg Elo) 
                 + 1.6206 × (Point Differential) + 0.0525 × (Elo Differential)
```

**Performance:**
- R² = 0.878 (explains 87.8% of variation - best model)
- Point differential: t = 12.024, p < 0.0001 (highly significant)
- Elo differential: t = 2.915, p = 0.0040 (significant)
- Points scored: t = 6.070, p < 0.0001 (significant)
- Elo rating: t = -0.769, p = 0.442 (not significant when differentials included)

**Key Insights:**
- Point differential is the strongest predictor (coefficient = 1.62)
- Each additional point of margin → ~1.5 more wins
- Elo differential also significant
- Raw Elo becomes insignificant once differentials are included

**Example Predictions:**
- Team: 75 pts/game, Elo 1350, -5 pt diff, -30 Elo diff → Expected 26 wins
- Team: 100 pts/game, Elo 1600, +5 pt diff, +95 Elo diff → Expected 52 wins

## 📊 Correlation Analysis

**Strong Positive Correlations:**
- Average Elo vs Wins: r = 0.907 (very strong)
- Point differential vs Wins: Strongest predictor in multivariate model

**Moderate Positive Correlation:**
- Average points scored vs Wins: r = 0.478 (moderate)

**Statistical Significance:**
- All correlations: p < 0.0001 (highly significant)
- Patterns are real, not random noise

## 💡 Business Value & Actionable Insights

**For Coaching Staff:**
1. **Focus on margin, not just scoring** - Point differential is the strongest lever
2. **Set quantified goals** - Use regression equations to target specific win totals
3. **Early warning system** - Monitor differentials game-by-game for quick interventions
4. **Lineup optimization** - Adjust lineups when differentials slip

**For Player Trades & Signings:**
- Evaluate candidates by their impact on team differentials, not raw scoring
- Quantify expected win gains from personnel changes
- Use model to simulate trade scenarios before execution

**For In-Season Strategy:**
- Track point differential and Elo differential after every game
- Small changes in margin translate to several additional victories
- Data-driven adjustments replace intuition-based decisions

## 🎯 Model Comparison & Selection

**Why Model 3 is Recommended:**

**Strengths:**
1. Highest explanatory power (R² = 0.878)
2. Identifies point differential as key driver
3. Reveals that raw Elo becomes redundant with differentials
4. Provides most actionable coaching insights

**Practical Application:**
- Point differential: Most actionable metric for coaches
- Every 1-point improvement in margin → ~1.5 more wins
- Easier to influence than raw skill ratings

## 📝 Statistical Methodology

**Analysis Workflow:**
1. **Exploratory Analysis:** Scatterplots and Pearson correlations
2. **Simple Regression:** Baseline model with single strongest predictor
3. **Multiple Regression (2 vars):** Test if scoring adds value to Elo
4. **Multiple Regression (4 vars):** Include differential metrics
5. **Model Comparison:** Evaluate R², significance tests, practical utility

**Hypothesis Testing Framework:**
- **Overall F-test:** Determines if model is useful (α = 0.05)
- **Individual t-tests:** Tests each coefficient (α = 0.01)
- **Null hypothesis:** Coefficients equal zero (no predictive value)
- **Alternative hypothesis:** At least one coefficient differs from zero

## 🔍 Key Findings

**Point Differential Dominates:**
- Coefficient = 1.62 (largest effect size)
- Each 1-point margin improvement → 1.5 additional wins
- Most actionable metric for coaching decisions

**Elo Differential Matters:**
- Significant predictor (p = 0.004)
- Measures competitive strength of schedule
- Second most important variable

**Raw Metrics Less Important:**
- Points scored: Modest effect when differentials included
- Elo rating: Becomes insignificant with differentials in model
- Focus on relative performance, not absolute levels

**Model Accuracy:**
- 87.8% of win variation explained
- Strong predictive power for season planning
- Reliable for setting realistic win targets

## 💭 Coaching Implications

**Practice & Development:**
1. Design drills that maximize scoring margin
2. Focus on both offensive efficiency AND defensive stops
3. Small margin improvements compound into multiple wins

**In-Game Adjustments:**
4. Monitor running point differential closely
5. Make substitutions when margin trends negative
6. Prioritize lineup combinations with positive differential history

**Personnel Decisions:**
7. Evaluate free agents by their team's differential with/without them
8. Trade analysis: Calculate expected differential change
9. Draft strategy: Target players who historically improve team margins

**Season Planning:**
10. Use regression equations to set realistic win targets
11. Identify minimum differential needed for playoff contention
12. Budget resources toward differential-improving investments

## 🚀 Future Enhancements

**Potential Improvements:**
- Expand dataset to include more recent seasons (2015-2025)
- Add player-level statistics (usage rate, PER, true shooting %)
- Incorporate schedule difficulty metrics
- Include injury data and player availability
- Time-series analysis for in-season prediction updates
- Machine learning models (random forest, gradient boosting)
- Interactive dashboard for real-time win probability
- Cross-validation for more robust performance estimates

## 🎓 Statistical Concepts Demonstrated

- Simple and multiple linear regression
- Pearson correlation analysis
- Hypothesis testing (F-tests, t-tests)
- R² and adjusted R² interpretation
- Coefficient interpretation and practical significance
- Model comparison and selection
- Statistical significance vs practical importance
- Data visualization for exploratory analysis

## 📁 Project Files
```
nba-win-prediction-regression-analysis/
├── MAT_243_Project_Three_Summary_Report.pdf  # Complete statistical report
├── analysis_notebook.ipynb                    # Python analysis code (if available)
└── README.md                                  # Project documentation
```

## 👨‍💻 Author

**Kyle Payne**  
Data Analyst | Statistical Modeling | Python  
[LinkedIn](https://linkedin.com/in/kyle-payne-68408812a/) | [GitHub](https://github.com/kylepayne0110)

---

*This project demonstrates regression analysis, hypothesis testing, model comparison, and translating statistical findings into actionable business insights for sports analytics.*
