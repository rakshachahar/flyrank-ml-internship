# Machine Learning-Based Prioritization of Website Content Refresh Using Search Performance Signals

- **Author:** Raksha Chahar
- **Lane:** Google Search Ranking & Discoverability
- **Repo:** https://github.com/rakshachahar/flyrank-ml-internship
- **Date:** August 2026

## 0. Abstract

This project investigates how machine learning can prioritize website pages for content refresh using observable search-performance signals. The analysis uses the FlyRank ML Internship warehouse dataset containing anonymized historical search-performance information. A Random Forest classifier was compared against a simple baseline using the same validation strategy to evaluate decision-support performance. The results showed that combining multiple search-performance features provides stronger prioritization than the baseline while maintaining honest validation and leakage awareness. The output is intended to support content teams in identifying pages for review rather than making fully automated publishing decisions.

## 1. Problem framing

The project supports the decision of which website pages should be reviewed first for content updates. The unit of analysis is one website content page represented by its historical search-performance signals. The output is a ranked recommendation list that helps content teams prioritize review efforts. A wrong recommendation may result in unnecessary work or missed opportunities to improve content visibility. Machine learning helps by combining several observable search-performance signals instead of relying on a single fixed rule.

## 2. Data safety

The analysis uses the FlyRank ML Internship warehouse dataset hosted on Hugging Face. The primary tables include the anonymized daily content performance table and supporting warehouse metadata. Features such as impressions, clicks, average search position, and click-through rate were used for analysis.

The following information was deliberately excluded:
- Client names and identifiers used as predictive features
- Website URLs
- Search queries
- Label-derived fields that could introduce data leakage
- Any client-identifying or sensitive information

Pseudonymous IDs were used only for grouping and joining records, never as predictive features. No client-identifying information appears anywhere in the work directory or final report.

## 3. Baseline

The baseline consisted of a transparent rule-based approach using observable search-performance signals to prioritize pages for review. Pages with lower impressions or lower click-through rates were ranked higher for content refresh.

This baseline provides a fair comparison because it uses the same available information and evaluation split as the machine learning model while remaining simple and interpretable. Model performance was compared against this baseline using identical evaluation conditions.

## 4. Model / analysis

A Random Forest classifier was selected because it can capture relationships between multiple search-performance signals without requiring complex feature engineering. The model used impressions, clicks, average search position, and click-through rate as predictive features.

The target variable represented whether a page should be prioritized for review based on historical search-performance observations. Label-derived variables and future information were intentionally excluded to reduce leakage risk.

## 5. Evaluation

The model was evaluated using the same train-test split as the baseline to ensure a fair comparison. Model accuracy was compared directly with the baseline accuracy using identical data partitions.

The Random Forest model demonstrated stronger performance than the baseline while remaining interpretable for decision-support purposes. Error analysis indicated that pages with borderline search-performance signals were more likely to be misclassified, highlighting the importance of human review before acting on recommendations.

## 6. Interpretation

The model identified combinations of impressions, clicks, average search position, and click-through rate as useful indicators for prioritizing content review. Rather than relying on a single metric, the model combined multiple observable signals to generate recommendations.

The analysis did not establish causal relationships or guarantee future search rankings. Negative or uncertain cases were treated as opportunities for further human investigation rather than automatic action.

## 7. Recommendation

The resulting action playbook recommends prioritizing pages with declining visibility for content refresh, improving click-through rate through title and meta description optimization, and monitoring stable pages without unnecessary intervention.

These recommendations are intended as decision-support for content teams. Confidence should always be interpreted alongside expert human judgment, and recommendations should not be executed automatically without review.

## 8. Reproducibility

All experiments were conducted using the notebooks included in this repository. Random seeds were fixed where applicable to improve reproducibility. The project uses Python, DuckDB, pandas, and scikit-learn within Google Colab.

A fresh clone of the repository together with the FlyRank dataset access instructions is sufficient to reproduce the workflow. Metrics and exported artifacts generated during the analysis are included where appropriate to support reproducibility.

## 9. Acknowledgments & data credit

This project was built on the FlyRank ML Internship dataset.

Data credit: https://flyrank.ai

The FlyRank ML Internship program provided the anonymized search-performance dataset used for educational and research purposes. All analysis follows the public-safe data usage guidelines provided by the internship.
