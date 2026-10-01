# House Price Prediction — Washington State

An analytical portfolio project examining how property characteristics relate to sale prices and comparing regression approaches for estimating prices. Based on an original capstone analysis by Pavithra Subramanian.

## Business problem
Property buyers, sellers, and analysts need a defensible starting point for estimating a home's sale price. The goal is to identify useful property and location attributes, compare candidate models on held-out data, and explain how estimates could inform pricing decisions. This is a historical case study, not a live valuation service or a claim to predict future housing-market movements.

## Data
- Source workbook: `innercity.xlsx` (place in `data/`). The original report describes 21,613 rows and 23 columns with sales recorded through 2015.
- Target: `price`. Example inputs include living area, lot size, bedrooms, bathrooms, quality, age, waterfront indicator, view, and location.
- Review the source workbook's provenance and reuse rights before making it public. Do not upload data if redistribution is not permitted; document how an authorised user can obtain it instead.

## Questions
1. Which available features are associated with observed sale prices?
2. How do linear regression, KNN, random forest, and gradient boosting compare on held-out data?
3. Does the original PCA experiment improve prediction relative to the same models on the original features?
4. How should a business interpret estimates and the risk of large errors?

## Approach
The original notebook explores distributions and relationships, handles missing values and outliers, examines clustering, then compares linear regression, KNN, random forest, and gradient boosting with and without PCA. This repository preserves that analytical logic; any compatibility or execution fixes should be recorded in a change log rather than silently changing the modelling approach.

## Reported results
The original report lists the following test R² scores on the non-PCA feature set: linear regression 0.6619; KNN 0.7081; random forest 0.7237; gradient boosting 0.7577. A later tuned gradient-boosting run reports test R² of 0.7597. The report's post-PCA tuned run reports test R² of 0.7002. These are **historical report values**, not independently reproduced results in this repository. The report also displays RMSE/MAPE figures without a sufficiently clear target scale or unit for a buyer-facing error statement; confirm their calculation before quoting them as currency or percentages.

## Insights and business proposals
- In this sample, property condition, age, views/waterfront attributes and size warrant investigation during pricing. Associations alone do not establish causal effects or guarantee a return on renovations.
- Use the model as a price-screening aid alongside local comparable sales and human review, particularly for unusual or high-priced homes.
- The report found no clear low/high-price separation from its K-means segments; do not market the clusters as reliable price bands.
- Prioritise validating errors by geography and price band before applying one model broadly. The original report's suggestion that better views and more space may support premium pricing is a hypothesis for further local-market testing, not a proven construction investment decision.

## Reproduce locally
1. Install Python 3 and create a virtual environment: `python -m venv .venv`.
2. Activate it: macOS/Linux `source .venv/bin/activate`; Windows PowerShell `.venv\Scripts\Activate.ps1`.
3. Install dependencies using the repository's tested `requirements.txt` once versions have been established: `python -m pip install -r requirements.txt`.
4. Place an authorised copy of `innercity.xlsx` in `data/`.
5. Start Jupyter: `jupyter lab` and run `notebooks/house_price_prediction.ipynb` from top to bottom.
6. The legacy notebook used a Google Colab Drive path. The cleaned copy should read `data/innercity.xlsx` and should document any environment-specific changes.

## Repository layout
```
house-price-prediction/
├── README.md
├── data/                 # source workbook only if sharing is permitted
├── notebooks/
│   └── house_price_prediction.ipynb
├── reports/
│   └── capstone_project_report.pdf
├── requirements.txt      # populate after a successful clean run
└── .gitignore
```

## Limitations and next checks
- Historical data through 2015 may not reflect today's housing market. Do not describe this model as current-price guidance without newer validation.
- Check handling of missing values, outliers, target transformations, clustering features, scaling, and the order of train/test splitting and PCA for leakage before relying on the reported scores.
- Re-run the notebook end to end, document actual package versions, and replace the historical metrics above with reproducible results only after verification.
- The source report contains broad housing-market context without supplying supporting evidence for every claim; this README intentionally limits claims to this analysis.

## Attribution
Analysis and original capstone report: Pavithra Subramanian. Portfolio adaptation of the supplied `Capstone project Report.pdf` and `PavithraSubramanian_CapstoneProject Notes.ipynb`.
