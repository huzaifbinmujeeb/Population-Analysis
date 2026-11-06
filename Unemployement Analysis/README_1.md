# Unemployment Analysis in India

Task 2 of my CodeAlpha Data Science internship. I took state-wise unemployment data for India (May 2019 to June 2020) and looked at what happened to it when Covid-19 hit.

Everything is in one notebook: `CodeAlpha_Unemployment_Analysis.ipynb`. It is already run, so you can read the charts and output on GitHub without running anything.

## The data

`Unemployment in India.csv` has monthly readings for each state, split into rural and urban areas. Columns: region, date, frequency, estimated unemployment rate (%), estimated employed, estimated labour participation rate (%), area.

It is not clean out of the box:
- There are 28 completely blank rows.
- Column names and some text values have stray leading spaces (the date column is literally `" Date"`).
- Dates are text, not dates.
- Coverage is uneven. 20 of the 28 regions have all 14 months for both rural and urban; the rest (Chandigarh, Sikkim, Puducherry and a few others) are missing some months. So I only compare employment totals across the 20 complete regions, otherwise the totals would drop just because rows are missing.

## What I did

1. Cleaned the data (above).
2. Plotted the national unemployment rate over time, both as a simple average and weighted by labour force size.
3. Compared rural and urban.
4. Compared each state's average rate before Covid (before March 2020) with the lockdown months (April to June 2020), and ran a t-test and a Mann-Whitney test on the difference.
5. Looked at employment and labour participation.
6. Checked for seasonality.
7. Wrote up what it could mean for policy.

## What I found

- The average rate was about 9.5% before Covid and about 20.2% during April to June 2020. The monthly national average peaked at 24.9% in May 2020 and was back to about 11.9% in June.
- On the 20 complete regions, employment dropped about 31% from February to April 2020 and was still about 8% below February in June.
- Labour participation fell from 44.3% to 33.8% in April. A lot of people stopped looking for work rather than showing up as unemployed, so the unemployment rate alone understates the damage.
- Urban areas were hit harder at the peak (28.4% vs 21.2% rural in May). By June the two were almost the same.
- States were affected very differently. Puducherry (+56 points), Jharkhand (+31), Tamil Nadu (+29) and Bihar (+23) saw the biggest jumps. Puducherry is a small sample, so I would not lean on that number.
- Some states already had high unemployment before Covid (Tripura, Haryana, Himachal Pradesh), so for them it is not only a Covid story.

## Limits

- Only 14 months of data. That is not enough to say anything real about seasonality; May 2020 was 16 points above May 2019, which is far too big to be a seasonal swing, but a small seasonal effect could be hiding in there.
- Small regions give noisy numbers.
- This is descriptive. I can show unemployment jumped when the lockdown started, but not separate the virus from the lockdown rules.
- The p-values from the tests are indicative only, because readings from the same state in different months are not independent.

## Run it

```
pip install pandas numpy matplotlib scipy jupyter
jupyter notebook CodeAlpha_Unemployment_Analysis.ipynb
```

Keep the CSV in the same folder as the notebook.

## Files

- `CodeAlpha_Unemployment_Analysis.ipynb` the analysis
- `Unemployment in India.csv` the dataset
