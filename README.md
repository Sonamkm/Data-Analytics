                                                                  Actual vs. Budget Analysis
The purpose of this analysis is to analyze Budget vs. Actual financial performance for 2024, across multiple categories and time period, providing clear insights into areas of overperformance and underperformance. The visual helps stakeholder tracks financial performance, identifying variances, and facilitating better decision-making.

                                                                Data Cleaning Process using Python
The Budget vs. Actual dataset was cleaned and processed in Python to ensure it was suitable for analysis and visualization.
  1.	Data Import and Exploration
    	Loaded the dataset and reviewed its structure to identify potential issues such as missing values or duplicates

  2.	Converting the Month Column to Date Format:
      Converted the Month column to a datetime format for accurate time-series analysis.
        •	data['Month'] = pd.to_datetime(data['Month'], format='%b-%y')
        •	Before: Strings like "Jan-24".
    	  •	After: Datetime format (2024-01-01).
      Purpose is to facilitated chronological sorting and time-based calculations, ensured compatibility with Power BI’s time-series visualizations.

  3.	Integrity Checks
      Verified there were no duplicate or missing values.
        •	data.duplicated().sum()
        •	data.isnull().sum()

  4.	Column Renaming
      The column names ‘Budgeted Amount’ and ‘Actual Amount’ were renamed to ‘Budget’ and ‘Actual’ for simplicity:
        •	data.rename(columns={'Budgeted Amount': 'Budget', 'Actual Amount': 'Actual'}, inplace=True)
        Simplified column names for better readability and usability.

  5.	Variance Calculation
      Added a new column, Variance, calculated as the difference between Actual and Budget for each row. This measure provides insights into financial performance       deviations.
        •	data['Variance'] = data['Actual'] - data['Budget']
      Purpose:
        •	Provided quantifiable measures of over- or under-performance.


  6.	Category Standardization
      The Category column contained inconsistent formatting. To ensure uniformity, leading/trailing spaces were removed, and all text was converted to title case:
        •	data['Category'] = data['Category'].str.strip().str.title()
      Example:
        •	Before: " revenue " → After: "Revenue".
      Purpose:
       •	Ensured consistency for accurate grouping and filtering in visualizations.


Outcome
The cleaned dataset is free of errors, formatted consistently, and enriched with key financial metrics. This ensured a seamless transition to visualization in Power BI, providing actionable insights into financial performance.


                                                            Visual Analysis Breakdown

1. Monthly and Quarterly Breakdown: Budget vs. Actual (Clustered Column Chart)
    This clustered column chart provides a side-by-side comparison of the monthly Budget and Actual financial values for 2024. Each quarter (Q1, Q2, Q3, and Q4)       is clearly segmented, highlighting the trends in budget adherence. Notable underperformance in June and December 2024 compared to other months. The                 visualization effectively demonstrates fluctuations over the months while maintaining a quarterly perspective, enabling stakeholders to identify patterns and     potential outliers.

2. Monthly Variance (Waterfall Chart)
   This waterfall chart illustrates the cumulative Variance (increase or decrease) in budget versus actual values across the months of 2024. Positive variances       are   represented in green, indicating an increase, while negative values (if any) would be shown in red. The chart reveals a consistent upward trend,             culminating in    a total variance for the year. This visualization provides an insightful summary of how monthly variances accumulate, offering a clear           depiction of financial performance over time.

3. Category-Wise Distribution of Actuals (Donut Charts)
    The Donut Chart visualizes the proportion of actual spending across five main categories: Operations, Marketing, Salaries, Miscellaneous, and Revenue.

    It highlights the proportion of each category in the overall total. Key insights include:
      •	Operations represent the largest share, contributing 22.53% (369K).
      •	Marketing and Salaries follow closely at 22.25% (364K) and 21.12% (346K), respectively.
      •	Miscellaneous accounts for 17.81% (292K), while Revenue has the smallest share at 16.29% (267K). This chart effectively illustrates the distribution of             actual spending, aiding in the identification of high-impact categories.


   4. Budget Deviation Across Months and Categories (Heatmap)
	    The heatmap displays the deviation of actual expenses from the budget, categorized by month and category. Negative deviations (underperformance) are               highlighted in lighter shades, while positive deviations (overperformance) are darker:
      •	Salaries show significant deviations, especially in September (-4704) and December (+4829).
      •	Miscellaneous had consistent positive deviations in January and February (+4898, +2723).
      •	Marketing experienced heavy underperformance in July (-4310) and September(-4923). This visual highlights variances across time and categories, providing          insights into areas requiring budget adjustment or further analysis.


   5. Visual Distribution of Actuals Across Categories (Treemap)
			Treemap provides a hierarchical and proportional view of actual expenses by category. It helps identify dominant cost centers at a glance. Offers a clear          visual comparison of how much each category contributes to the total actual expenditure, where Operations has the highest value at 369k, closely followed by       Marketing with 364k, Salaries are the third-largest category, amounting to 346k, Miscellaneous expenses stand at 292k, while Revenue is the smallest               category with 267k. It is useful for presenting high-level financial overviews to management


   6. Tracking Monthly Variance: Budget vs. Actual (Line Chart)
    This chart depicts the monthly variance between budgeted and actual expenses for 2024. The “Sum of Budget” is shown in light blue, while the “Sum of Actual”       is in dark blue. From January to May, the budget and actuals follow a consistent upward trend, peaking in May. A significant drop is observed in June,             followed by a rise in July and subsequent fluctuations throughput the year. By November, the budgeted and actual values align closely, but both shows a steep      decline in December. This suggests seasonal variations or other influencing factors affecting the budget and actual spending patterns.


    Key Insights
    1.	Underperformance in Revenue:
      •	Revenue consistently fell short of projections, especially in the first quarter, with January showing the highest deficit (-$4,887). This trend signals a           potential flaw in revenue forecasting or an underperforming business strategy.
    2.	Frequent Over-Budgeting in Miscellaneous Expenses:
      •	Miscellaneous expenditures regularly exceeded budget limits, with August (+$1,209) and October (+$4,107) showing the most significant overspending. This           points to a lack of control or unexpected costs being lumped into this category.
    3.	Operational Spending Dominance:
      •	Operations (22.53% of actuals) and Marketing (22.25%) contributed the most to overall spending. These categories need close scrutiny as they significantly         impact total variance.
    4.	Seasonal Peaks in Variance:
      •	The highest deviations occurred in August, September, and October, suggesting seasonal factors or events that caused unexpected spikes in spending.
    5.  Positive Variance in Specific Months:
      •	Some months, like January and May, stayed close to or under budget, indicating areas of controlled spending that could serve as a model for other months.


Recommendations
1.	Improve Revenue Forecasting:
    o	Refine revenue projection models by incorporating historical data, market trends, and potential risks to enhance accuracy and avoid overestimation.

2.	Break Down Miscellaneous Expenses:
    o	Analyse and categorize items currently labelled as Miscellaneous to improve transparency and control over these expenditures. Reduce overestimated budgets         in Miscellaneous to optimize resource allocation.

3.	Set Spending Limits for Operations and Marketing:
    o	Establish stricter budget controls for high-spending categories. Implement performance-based reviews to ensure that marketing and operational costs align           with business outcomes.

4.	Prepare for Seasonal Variations:
    o	Identify the causes of spending spikes in August through October. If they result from predictable events, build these into the budget proactively.

5.	Regular Monitoring:
    o	Use this dashboard as a real-time monitoring tool to track variances and act swiftly when performance deviates from expectations.

Conclusion
The analysis highlights the importance of proactive financial management to minimize budget deviations. While some categories, such as Salaries and Miscellaneous, frequently went over budget, others like Revenue underperformed. By adopting better forecasting, stricter cost management, and real-time monitoring, the organization can minimize variances, optimize spending, and achieve its financial goals more efficiently.



